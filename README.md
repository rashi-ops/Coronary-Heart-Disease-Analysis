# Coronary Heart Disease (CHD) Analysis

## Project Overview
This project focuses on predicting the **10-year risk of Coronary Heart Disease (CHD)** using the **Framingham Heart Study** dataset.  
The main objective is to perform **Exploratory Data Analysis (EDA)**, **data preprocessing**, and apply **Machine Learning models** (specifically Logistic Regression) to identify patients who are at higher risk of CHD.

---

## About the Dataset
The **Framingham Heart Disease Dataset** includes **4,240 records** with **16 columns** (15 features + 1 target).  
It contains patient health information such as age, BMI, blood pressure, cholesterol, smoking habits, and more.  
The target variable is **TenYearCHD**, which indicates whether the patient developed coronary heart disease within ten years (1 = Yes, 0 = No).

| Column Name | Description |
|--------------|-------------|
| male | Gender of the patient (1 = Male, 0 = Female) |
| age | Age of the patient |
| education | Education level |
| currentSmoker | Whether the patient is a current smoker |
| cigsPerDay | Average number of cigarettes smoked per day |
| BPMeds | Whether the patient is on blood pressure medication |
| prevalentStroke | Whether the patient had a stroke previously |
| prevalentHyp | Whether the patient has hypertension |
| diabetes | Whether the patient has diabetes |
| totChol | Total cholesterol level |
| sysBP | Systolic blood pressure |
| diaBP | Diastolic blood pressure |
| BMI | Body Mass Index |
| heartRate | Heart rate (beats per minute) |
| glucose | Blood glucose level |
| TenYearCHD | Target — 1 if CHD occurred within 10 years, else 0 |

---

##  Data Preprocessing
- **Handling Missing Values:** Missing entries in columns like `education`, `cigsPerDay`, `BPMeds`, `totChol`, `BMI`, `heartRate`, and `glucose` were identified and treated.  
- **Data Distribution:** Plotted feature distributions to detect skewness and outliers (few outliers were found).  
- **Feature Selection:** Checked for multicollinearity and correlation among attributes.  
- **Data Split:**
x_train.shape: (3392, 14)
y_train.shape: (3392,)
x_test.shape: (848, 14)
y_test.shape: (848,)

yaml
Copy code

---

## Model Used: Logistic Regression
We used a **Logistic Regression Model** to classify whether a patient is likely to develop CHD within ten years.

###  Performance Metrics (Initial Model)
- **Training Accuracy:** 85.52%  
- **Testing Accuracy:** 85.85%

**Confusion Matrix (Initial):**
| Class | Precision | Recall | F1-Score | Support |
|--------|------------|--------|-----------|----------|
| 0 | 0.86 | 0.99 | 0.92 | 725 |
| 1 | 0.62 | 0.07 | 0.12 | 123 |

>  The model performs well for class 0 (healthy patients) but poorly for class 1 (at-risk patients), showing an imbalance issue.

---

##  After Model Adjustment
After tuning and improving the model:

**Confusion Matrix (Improved):**
| Class | Precision | Recall | F1-Score | Support |
|--------|------------|--------|-----------|----------|
| 0 | 0.92 | 0.67 | 0.77 | 725 |
| 1 | 0.25 | 0.63 | 0.35 | 123 |

- **Accuracy:** 66%  
- **Macro Avg Recall:** 0.65  
- **Weighted Avg F1-Score:** 0.71  

>  The recall for class 1 (CHD positive) significantly improved, meaning the model became better at identifying high-risk patients even though overall accuracy dropped slightly.

---

##  Conclusion
Our logistic regression model achieved a good balance between accuracy and recall after improvement.  
While the overall accuracy is around **66%**, the **recall for high-risk patients (class 1)** improved greatly — which is crucial in medical prediction tasks where false negatives can be dangerous.

Future improvements may include:
- Using **SMOTE** or **class weighting** to handle class imbalance.  
- Trying **Random Forest** or **XGBoost** models for better predictive performance.  
- Hyperparameter tuning to further optimize model accuracy and recall.

---

##  Key Learnings
- Importance of handling missing data and class imbalance.
- Logistic Regression is a simple yet powerful baseline model.
- Recall is often more important than accuracy in health-related predictions.

---

## 🛠️ Tech Stack
- **Python**
- **NumPy**, **Pandas**
- **Matplotlib**, **Seaborn**
- **Scikit-learn**
