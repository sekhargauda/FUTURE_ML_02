# 🎫 Customer Support Ticket Classification

A machine learning project that classifies customer support tickets into predefined categories using Natural Language Processing (NLP) and multiple classification algorithms.

The project follows an end-to-end workflow, from data preprocessing and exploratory data analysis to model training, evaluation, comparison, and saving the trained model for reuse.

---

## 📑 Table of Contents

- [📌 Project Overview](#-project-overview)
- [📂 Dataset & Preprocessing](#-dataset--preprocessing)
- [📊 Exploratory Data Analysis](#-exploratory-data-analysis)
- [⚙️ Text Preprocessing](#️-text-preprocessing)
- [🤖 Modeling & Evaluation](#-modeling--evaluation)
- [💾 Model Saving](#-model-saving)
- [📁 Project Structure](#-project-structure)
- [🚀 How to Run](#-how-to-run)
- [🏆 Results & Conclusion](#-results--conclusion)
- [🔮 Future Improvements](#-future-improvements)
- [👤 Author](#-author)

---

# 📌 Project Overview

Customer support teams receive tickets covering different issues and topics. Manually categorizing these tickets can be time-consuming.

This project uses machine learning and NLP techniques to automatically classify customer support tickets based on their text.

The project includes:

- Loading and exploring customer support ticket data.
- Cleaning and preprocessing ticket text.
- Analyzing ticket categories and text lengths.
- Converting text into numerical features using TF-IDF.
- Training and comparing multiple classification algorithms.
- Evaluating models using classification metrics.
- Selecting a model based on its evaluation results.
- Saving the trained model for future predictions.

---

# 📂 Dataset & Preprocessing

The project uses a customer support ticket dataset containing ticket descriptions and their corresponding topic categories.

### Dataset Columns

| Column | Description |
|---|---|
| `Document` | Text describing the customer support ticket |
| `Topic_group` | Category assigned to the support ticket |

During preprocessing, the columns are renamed:

| Original Column | Renamed Column |
|---|---|
| `Document` | `ticket_text` |
| `Topic_group` | `topic` |

## Data Preprocessing

The initial data preparation includes:

- Checking dataset dimensions and data types.
- Examining descriptive statistics.
- Identifying missing values and duplicate records.
- Removing rows with missing values.
- Renaming columns for easier use during model development.
- Calculating ticket text lengths for further analysis.

## Project Workflow

```text
Customer Support Ticket Dataset
              |
              v
        Data Loading
              |
              v
       Data Exploration
              |
              v
      Data Preprocessing
              |
              v
      Text Preprocessing
              |
              v
       Label Encoding
              |
              v
       Train-Test Split
              |
              v
       TF-IDF Vectorization
              |
              v
      Model Training
              |
              v
      Model Evaluation
              |
              v
      Model Comparison
              |
              v
      Best Model Selection
              |
              v
        Model Saving
              |
              v
       Prediction Pipeline
```

---

# 📊 Exploratory Data Analysis

Exploratory Data Analysis (EDA) was performed to understand the dataset and the distribution of customer support tickets.

The analysis includes:

- Dataset shape and information.
- Descriptive statistics.
- Missing-value and duplicate checks.
- Ticket text length calculation and descriptive statistics.
- Distribution of ticket text lengths.
- Distribution of ticket categories.
- Word cloud visualization of ticket text.

These analyses help understand the dataset's structure, the distribution of ticket categories, and the characteristics of the text before model training.

---

# ⚙️ Text Preprocessing

Text preprocessing was performed to clean the ticket descriptions before converting them into numerical features.

The preprocessing steps include:

- Converting text to lowercase.
- Removing punctuation.
- Removing English stopwords.
- Removing numeric tokens.
- Correcting spelling using SymSpell.
- Applying WordNet lemmatization using NLTK.

These steps help standardize ticket text before feature extraction.

## Label Encoding

The target categories are converted into numerical labels using `LabelEncoder`.

Class weights are also calculated to account for differences in category frequencies during training.

## TF-IDF Vectorization

TF-IDF (Term Frequency-Inverse Document Frequency) is used to convert preprocessed ticket text into numerical features.

The vectorizer is integrated into a Scikit-learn Pipeline with the classification models.

---

# 🤖 Modeling & Evaluation

## Train-Test Split

The dataset is divided into training and testing sets using a **70:30 split**.

The split uses:

```text
Test Size     : 30%
Training Size : 70%
Random State  : 101
Stratify      : Target labels
Shuffle       : True
```

Stratification helps preserve the distribution of target categories across the training and testing sets.

## Models Developed

The following classification algorithms were trained and evaluated:

- Logistic Regression
- Decision Tree Classifier
- Multinomial Naive Bayes
- Bernoulli Naive Bayes
- XGBoost Classifier
- LightGBM Classifier
- SGD Classifier
- Calibrated Linear SVC

Class weights were used for selected models to address class imbalance.

## Evaluation Metrics

The models were evaluated using:

- **Accuracy** — proportion of correctly classified tickets.
- **Precision** — proportion of predicted positive cases that are correct.
- **Recall** — proportion of actual positive cases correctly identified.
- **F1-Score** — harmonic mean of precision and recall.
- **ROC-AUC** — measures the model's ability to distinguish between classes.

A confusion matrix and classification report were also used to examine model performance.

## Model Comparison

The models were compared using a performance DataFrame containing their evaluation metrics.

The comparison helps identify differences in classification performance across the tested algorithms.

---

# 💾 Model Saving

The selected LightGBM pipeline is saved using Python's Pickle module.

```text
model.pkl
```

The saved pipeline includes the trained text-processing and classification components, allowing it to be loaded for reuse without retraining.

---

# 📁 Project Structure

```text
FUTURE_ML_02/
│
├── customer_support_tickets.csv
│
├── ticket-classification.ipynb
│
├── predict.ipynb
│
├── model.pkl
│
└── README.md
```

---

# 🚀 How to Run

## 1. Clone the Repository

```bash
git clone https://github.com/sekhargauda/FUTURE_ML_02.git
```

## 2. Navigate to the Project Directory

```bash
cd FUTURE_ML_02
```

## 3. Install Dependencies

Install the libraries used in the notebook:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
pip install nltk symspellpy wordcloud xgboost lightgbm
```

## 4. Run the Classification Notebook

Open:

```text
ticket-classification.ipynb
```

Run the notebook to perform data exploration, preprocessing, model training, evaluation, comparison, and model saving.

**Note:** The training notebook uses a Google Drive dataset path. Update the dataset path if you are running it outside the original Google Colab environment.

## 5. Run the Prediction Notebook

Open:

```text
predict.ipynb
```

The repository also includes this notebook for prediction-related work.

---

# 🏆 Results & Conclusion

The project implements an end-to-end customer support ticket classification workflow using NLP and machine learning.

Multiple classification algorithms were trained and evaluated using accuracy, precision, recall, F1-score, ROC-AUC, confusion matrices, and classification reports.

The notebook's model comparison identifies **LightGBM** as the best-performing model overall, with reported accuracy above 86% and ROC-AUC above 98%.

The trained LightGBM pipeline is saved as `model.pkl` for reuse.

---

# 🔮 Future Improvements

Potential improvements include:

- Experimenting with additional NLP feature extraction techniques.
- Evaluating transformer-based text classification models.
- Improving performance on less frequent ticket categories.
- Testing the model on new, unseen customer support tickets.
- Developing an API for ticket classification.
- Building an interactive interface for ticket predictions.

---

# 👤 Author

## [Sekhar Gauda](https://github.com/sekhargauda/)

Machine Learning / NLP Project

[GitHub Repository](https://github.com/sekhargauda/FUTURE_ML_02)

---

⭐ **Project Status: Completed**
