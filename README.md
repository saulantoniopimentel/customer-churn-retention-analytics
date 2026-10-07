# Customer Churn & Retention Analytics

End-to-end customer churn analysis and retention strategy project using Python, Machine Learning and Power BI.

The project analyzes customer behavior, identifies factors associated with churn, estimates individual churn risk, and provides an interactive Power BI dashboard to support customer retention decisions.

---

## 📌 Business Problem

Customer churn is a major challenge for subscription-based businesses because losing customers directly impacts recurring revenue and increases customer acquisition costs.

The objective of this project is to answer:

> **Which customers are most likely to churn, what characteristics are associated with churn, and how can the business prioritize retention efforts?**

The analysis combines exploratory data analysis, predictive modeling and business intelligence to transform customer data into actionable retention insights.

---

## 🎯 Project Objectives

- Analyze customer demographics, services and contract characteristics.
- Identify the main factors associated with customer churn.
- Compare churn behavior across contracts, tenure, internet services and payment methods.
- Build a Machine Learning model to estimate individual churn probability.
- Classify customers into Low, Medium and High Risk categories.
- Prioritize customers for retention campaigns.
- Build an interactive Power BI dashboard for business decision-making.

---

## 🗂️ Dataset

The project uses the **IBM Telco Customer Churn dataset**, containing information about customer demographics, services, contracts, payment methods and churn status.

### Dataset characteristics

- **7,043 customers**
- **21 original variables**
- Customer demographics
- Account information
- Services subscribed
- Contract information
- Payment methods
- Monthly and total charges
- Churn status

The original dataset contains `TotalCharges` as a text field, which required data type conversion during preprocessing.

---

## 🧹 Data Preparation

The data preparation process was performed using Python and Pandas.

### Main steps

1. Loaded the raw CSV dataset.
2. Inspected data types and missing values.
3. Checked for duplicate records.
4. Converted `TotalCharges` from text to numeric.
5. Identified 11 missing values in `TotalCharges`.
6. Verified that those records corresponded to customers with zero tenure.
7. Replaced those missing values with `0`.
8. Created customer tenure groups.
9. Created a high-risk exploratory profile.
10. Prepared categorical and numerical variables for Machine Learning.

### Tenure groups

Customers were classified into:

- `0-12 months`
- `13-24 months`
- `25-48 months`
- `49-72 months`

---

## 📊 Exploratory Data Analysis

The exploratory analysis identified several relevant patterns.

### Overall churn

| Metric | Value |
|---|---:|
| Total Customers | 7,043 |
| Churned Customers | 1,869 |
| Retained Customers | 5,174 |
| Churn Rate | 26.54% |
| Retention Rate | 73.46% |

---

### Churn by Contract

Customers with month-to-month contracts presented the highest churn rate.

| Contract | Churn Rate |
|---|---:|
| Month-to-month | 42.71% |
| One year | 11.27% |
| Two year | 2.83% |

This suggests that contract duration is strongly associated with customer retention.

---

### Churn by Internet Service

| Internet Service | Churn Rate |
|---|---:|
| DSL | 18.96% |
| Fiber optic | 41.89% |
| No internet service | 7.40% |

Fiber optic customers showed substantially higher churn than the other groups.

---

### Churn by Customer Tenure

| Tenure Group | Churn Rate |
|---|---:|
| 0-12 months | 47.44% |
| 13-24 months | 28.71% |
| 25-48 months | 20.39% |
| 49-72 months | 9.51% |

Customers during their first year showed the highest churn rate, highlighting the importance of early-stage retention strategies.

---

### Monthly Charges

Average monthly charges were higher among customers who churned.

| Customer Group | Average Monthly Charges |
|---|---:|
| Retained | $61.27 |
| Churned | $74.44 |

Churned customers paid approximately **$13.18 more per month** on average.

---

### Churn by Payment Method

Electronic check customers presented the highest churn rate.

| Payment Method | Churn Rate |
|---|---:|
| Electronic check | 45.29% |
| Mailed check | 19.11% |
| Bank transfer (automatic) | 16.71% |
| Credit card (automatic) | 15.24% |

---

## 🔥 High-Risk Customer Profile

An exploratory segment was created combining:

- Month-to-month contract
- Electronic check payment method

This segment contained:

- **1,850 customers**
- **53.73% churn rate**

For comparison, the remaining customers showed a churn rate of approximately **16.85%**.

This segment represents a particularly relevant population for retention strategies.

> **Note:** This analysis identifies an association between customer characteristics and churn. It does not establish causality.

---

# 🤖 Machine Learning

Two classification models were evaluated:

- Logistic Regression
- Random Forest

The target variable was:

```text
Churn
No → 0
Yes → 1