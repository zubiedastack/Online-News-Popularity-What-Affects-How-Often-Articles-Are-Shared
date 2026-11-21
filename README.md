# Online News Popularity: What Affects How Often Articles Are Shared

A data mining project for CIS 3920 (Data Mining for Business Analytics/Applied Machine Learning for Business) at Baruch College. We analyzed 39,644 Mashable articles to find out which characteristics of an online news article affect how many times it is shared on social networks.

## Research Question

What characteristics of an online news article affect how many times it is shared on social networks?

## Why It Matters

Digital publishers rely on advertising revenue, which depends on web traffic, and social media sharing is one of the biggest drivers of that traffic. Knowing which characteristics lead to more shares helps editors make better decisions about topics, keywords, and publishing schedules before an article goes live.

## Dataset

- **Source:** [Online News Popularity, UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/332/online+news+popularity)
- **Size:** 39,644 articles published by Mashable over two years, with 58 predictive attributes and no missing values
- **Outcome:** Number of social media shares (modeled as the natural logarithm of shares, because shares are extremely right-skewed)

The dataset is not included in this repository. Download `OnlineNewsPopularity.csv` from the link above to run the code.

## Hypothesis

If an online news article belongs to the lifestyle or social media category, is tagged with keywords that have historically performed well, and is published on a weekend, then it will receive a significantly higher number of social media shares than articles without these characteristics.

## Methods

The data was split into a training set (70%) and a test set (30%). Three models were built using the same factors: content category, keyword strength, weekend publishing, and the number of images, videos, words, and links.

1. **Multiple linear regression:** Measures the effect of each factor while holding the others constant
2. **Decision tree (3 levels):** Groups articles and shows how factors interact
3. **Random forest (300 trees):** Captures nonlinear patterns and ranks factor importance

## Key Findings

![Effect of each factor on shares](figure1_effects.png)

- **Keyword strength** was the most consistent predictor across all three models. Doubling keyword strength increased expected shares by about 18.5%.
- **Weekend articles** received about 31% more shares than weekday articles.
- **Social media articles** received about 65% more shares than world news articles, followed by technology (43%) and lifestyle (32%).
- **Images** had a small positive effect, while videos and article length were not significant.

| Model | R-squared (test set) | Root mean squared error (test set) |
| --- | --- | --- |
| Random forest | 0.120 | 0.868 |
| Multiple linear regression | 0.087 | 0.885 |
| Decision tree | 0.085 | 0.885 |
| No model (predicting the average) | 0.000 | 0.926 |

The results largely support the hypothesis. However, even the best model explains only about 12% of the variation in shares, which shows that much of what makes an article go viral is not captured in the data.

## How to Run

1. Open `APPLIEDMACHINELEARNINGPROJ_CODE.ipynb` in [Google Colab](https://colab.research.google.com/).
2. Upload `OnlineNewsPopularity.csv` using the Files panel on the left.
3. Click **Runtime > Run all**.

Libraries used: pandas, NumPy, statsmodels, scikit-learn, Matplotlib.

## Reference

Fernandes, K., Vinagre, P., & Cortez, P. (2015). A Proactive Intelligent Decision Support System for Predicting the Popularity of Online News. *Proceedings of the 17th EPIA 2015, Portuguese Conference on Artificial Intelligence*, Coimbra, Portugal.
