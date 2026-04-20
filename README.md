# News Topics Classification

This project solves a news topic classification task from the **News-topics-competition-2025** competition.  
The main challenge is that the competition provides **no training data**. Only the test set is available, so the training dataset had to be collected independently using **web scraping and parsing** from open news sources.

The main notebook for the project is: [news_topics_competition.ipynb](./news_topics_competition.ipynb)

## Project Goal

The goal is to predict the topic of each news article from the test set.  
Each article must be assigned to one of the following 9 classes:

- `0` — Society / Russia
- `1` — Economics
- `2` — Law Enforcement / Security
- `3` — Former USSR
- `4` — Sport
- `5` — Self-care
- `6` — Construction
- `7` — Tourism / Travel
- `8` — Science and Technology

## Project Pipeline

The project was completed in several stages:

1. **Web scraping**
   - News articles were collected from open news websites.
   - Website rubrics were used as topic labels.

2. **Dataset creation**
   - Parsed articles were stored in a structured dataset.
   - The dataset included article text and topic labels.

3. **Text preprocessing**
   - Texts were cleaned and normalized.
   - Empty and low-quality samples were filtered out.

4. **Feature extraction**
   - TF-IDF vectorization was applied to the article text.

5. **Model training**
   - Several classification models were tested.
   - Logistic Regression gave the best public leaderboard result.

6. **Prediction**
   - The trained model was applied to the competition test set.

7. **Submission**
   - Predictions were saved in the required Kaggle CSV format.

## Methodology

Since no labeled training set was provided, the project relied on **weak supervision**:  
news website sections were treated as target labels. After collecting and preprocessing the data, text features were extracted using **TF-IDF**, and classification models were trained on the scraped dataset.

The final submissions were created using the same format as the provided baseline file:

- `topic`
- `index`

## Evaluation

The competition metric is:

**Accuracy** — the proportion of correctly predicted news topics.

## Results

The following public leaderboard scores were achieved:

- Baseline submission: **0.50880**
- Improved TF-IDF ensemble: **0.53844**
- Logistic Regression: **0.54681**
- CatBoost: **0.47672**
- **RuBERT: 0.66882** — best result

## Main Conclusion

This project demonstrates a full NLP workflow for a real-world competition without a provided training set.  
The complete pipeline included scraping, dataset construction, preprocessing, model training, evaluation, and submission generation.

Among all tested approaches, **RuBERT achieved the best public Kaggle score of 0.66882**, clearly outperforming TF-IDF-based models and CatBoost. This indicates that transformer-based models capture semantic structure in Russian news texts much better and are the most effective solution for this classification task.

- cleaner scraped labels,
- better alignment between website rubrics and target classes,
- more diverse news sources,
- stronger domain adaptation between scraped news and competition test data.

## Tech Stack

- Python
- Pandas
- NumPy
- BeautifulSoup
- Requests
- Scikit-learn
- TF-IDF
- Logistic Regression

## Repository Contents

- `news_topics_competition.ipynb` — main project notebook
- `parsed_lenta_news.csv` — scraped training dataset
- `submission.csv` — final competition submission file

## Author
Yulia Bezginova  
Telegram: [@ybezginova_de](https://t.me/ybezginova_de)
