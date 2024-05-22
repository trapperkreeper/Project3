# Project3

## Overview

The goal of this project is to analyze Tweet sentiment of five companies
(Amazon, Apple, Google, Microsoft, and Tesla) over a period of five years,
and see how strong of a correlation there is between the Tweet sentiment and
fluctuations in stock price.

## Methodology

The Tweet and market data span from January, 2015, through December, 2019.
Since there is no trading activity on weekends, we discarded Tweet data on 
Saturdays and Sundays -- therefore our analysis compares the Friday-to-Monday
price differential to Monday's Tweet sentiment.

### Sentiment Analysis

We used Valence Aware Dictionary and sEntiment Reasoner (VADER) to calculate a
sentiment score for each Tweet. VADER returns a value between -1.0 (very
negative) to 1.0 (very positive). Per the library's recommendation, we
designate scores between -0.05 and 0.05 as "Neutral", and do not take them into
account for this analysis.

Tweets with positive sentiment are assigned a value of +1, and Tweets with
negative sentiment a value of -1. We maintain the totals of these values
separate for each day, as $Tweets_{pos}$ and $Tweets_{neg}$

### Tweet Score

In order to preserve the significance of large Tweet volume, we calculate the
"Tweet Score" for each day as follows:
$$Tweet Score = \sqrt{|Tweets_{pos}{^2} - Tweets_{neg}{^2}|}$$

## Results

Now that we have the change in price as well as the Tweet Score, we use the
Pandas DataFrame `corr()` method to calculate the correlation between the two.

Here are the results for each company:

| Company | Correlation Score |
| ------- | ----------------- |
| Amazon | 0.114406 |
| Apple | 0.084650 |
| Google (Class A) | 0.175427 |
| Google (Class C) | 0.069292 |
| Microsoft | 0.124491 |
| Tesla | 0.101101 |

Additionally, we analyzed the correlation between Tweet volume (again excluding
Tweets classified as "Neutral") and trading volume, and find a much higher
correlation here:

| Company | Correlation Score |
| ------- | ----------------- |
| Amazon | 0.547947 |
| Apple | 0.630284 |
| Google (Class A) | 0.551027 |
| Google (Class C) | 0.413433 |
| Microsoft | 0.348763 |
| Tesla | 0.777124 |

## Credits

### Contributors

[Cynthia Estrella](https://github.com/cynstar)\
[Javier Ibarra-sanchez](https://github.com/ibarrajavi)\
[Racquel Jones](https://github.com/RacquelRobinsonJonesATX)\
[Iker Maruri](https://github.com/trapperkreeper)\
[Fu Thong](https://github.com/kibble)

### Data Attribution

[Kaggle: Tweets about the Top Companies from 2015 to 2020](https://www.kaggle.com/datasets/omermetinn/tweets-about-the-top-companies-from-2015-to-2020?select=Tweet.csv)

[MarketStack: Real-Time, Intraday &
Historical Market Data API](https://marketstack.com/)

### VADER Sentiment Analysis

https://github.com/cjhutto/vaderSentiment
Hutto, C.J. & Gilbert, E.E. (2014). VADER: A Parsimonious Rule-based Model for Sentiment Analysis of Social Media Text. Eighth International Conference on Weblogs and Social Media (ICWSM-14). Ann Arbor, MI, June 2014.