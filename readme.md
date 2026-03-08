# Diabetes Prediction using Machine Learning

This project builds and evaluates machine learning models to predict
diabetes risk using clinical features from the PIMA Indians Diabetes
Dataset. The workflow includes data preprocessing, exploratory data
analysis, model training, performance evaluation, and model
interpretability using explainable AI techniques.


# Project Overview

Diabetes is a chronic metabolic disease characterized by elevated blood
glucose levels. Early detection can help prevent severe complications
such as cardiovascular disease, kidney failure, and nerve damage.

This project explores how machine learning models can assist in
predicting diabetes using patient health measurements.

The full workflow includes:

-   Data cleaning and preprocessing
-   Exploratory data analysis (EDA)
-   Training multiple machine learning models
-   Cross-validation model comparison
-   Performance evaluation using ROC, calibration, and confusion
    matrices
-   Explainable AI analysis using SHAP
-   Feature importance analysis


# Dataset

The project uses the PIMA Indians Diabetes Dataset.

Dataset characteristics:

  Property             Value
  Number of samples    768
  Number of features   8
  Target variable      Diabetes outcome (0 / 1)

Features include:

-   Pregnancies
-   Glucose
-   BloodPressure
-   SkinThickness
-   Insulin
-   BMI
-   DiabetesPedigreeFunction
-   Age


# Data Preprocessing

Several preprocessing steps were performed to prepare the dataset for
modeling.

1.  Handling invalid values

Certain medical features contained biologically impossible zero values.
These were treated as missing values.

Affected features:

-   Glucose
-   BloodPressure
-   SkinThickness
-   Insulin
-   BMI

2.  Missing value imputation

Missing values were filled using the median computed from the training
set to avoid data leakage.

3.  Train-test split

The dataset was split using stratified sampling:

-   80% training set
-   20% testing set

This preserved the class distribution between diabetic and non-diabetic
samples.


# Exploratory Data Analysis

Exploratory analysis was performed to understand feature relationships
and dataset characteristics.

Visualizations included:

-   Correlation heatmap
-   Feature distributions by diabetes outcome
-   Box plots comparing feature values
-   Class distribution visualization

Key observations:

-   Glucose shows the strongest correlation with diabetes outcome.
-   BMI and Age show moderate correlation.
-   The dataset has moderate class imbalance (\~65% non-diabetic, \~35%
    diabetic).


# Machine Learning Models

Three models were implemented and compared.

### Logistic Regression

A linear baseline model used for comparison.

### Random Forest

An ensemble model using multiple decision trees to improve predictive
performance and reduce variance.

### XGBoost

A gradient boosting algorithm optimized for structured tabular datasets.


# Model Evaluation

Model performance was evaluated using multiple metrics to provide a
comprehensive comparison.

Evaluation methods include:

-   Accuracy
-   ROC-AUC score
-   5-fold stratified cross-validation
-   ROC curve comparison
-   Calibration curves
-   Confusion matrices

Using multiple metrics ensures both classification performance and
probability reliability are assessed.


# Results Summary

  Model                 Accuracy     ROC-AUC      CV AUC (mean ± std)
  Logistic Regression   0.7078       0.8130       0.837 ± 0.020
  Random Forest         0.7468       0.8085       **0.840 ± 0.020**
  XGBoost               **0.7597**   **0.8331**   0.824 ± 0.027

Best Model: Random Forest (CV ROC-AUC = 0.840)

Interpretation:

-   Random Forest achieved the best cross-validated performance,
    indicating strong generalization ability.
-   XGBoost achieved the highest test-set accuracy, but slightly lower
    cross-validation stability.
-   Logistic Regression provides a useful baseline despite being a
    simpler linear model.


# Model Interpretability

Model explanations were generated using SHAP (SHapley Additive
exPlanations).

SHAP helps explain how each feature contributes to model predictions.

Key insights:

-   Glucose is the strongest predictor of diabetes risk.
-   BMI and Age are important secondary predictors.
-   Feature contributions align with known clinical risk factors.


# Feature Importance

Feature importance was analyzed using:

-   XGBoost feature importance
-   SHAP feature contributions
-   Permutation importance

Most influential features:

1.  Glucose
2.  BMI
3.  Age
4.  DiabetesPedigreeFunction


# Project Structure

    Diabetes_Predictor
    │
    ├── diabetes_training.ipynb
    ├── diabetes.csv
    └── README.md


# How to Run

Clone the repository:

    git clone https://github.com/paul-dev-28/Diabetes_Predictor.git
    cd Diabetes_Predictor

Install dependencies:

    pip install numpy pandas matplotlib seaborn scikit-learn xgboost shap

Run the notebook:

    jupyter notebook

Open the notebook:

    diabetes_training.ipynb



# Key Findings

-   Ensemble models outperform linear models on this dataset.
-   Random Forest achieved the most stable performance across
    cross-validation folds.
-   Glucose, BMI, and Age are the strongest predictors of diabetes risk.
-   Explainable AI analysis confirms clinically meaningful feature
    relationships.


# Future Improvements

Possible extensions for this project:

-   Hyperparameter tuning using grid search
-   Training deep learning models for comparison
-   Validation using larger healthcare datasets
-   Deployment as a web-based diabetes risk prediction tool
