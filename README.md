# ASTR Prediction Model

a very basic explanation from a novice making a machine learning model

- Features to add
  - [ ] Add granules price as a feature

---

### Introduction

ASTR Pet Industries is one of the leading PET preform manufacturer of central India I create this project with the aim to determine/predict the demand of preforms for the company to maintain enough quantity to crater the demand.

### Data Acquiring and Data Cleaning

First step was to gather the sales data from the erp software. So the company was setup in 2018 and was in production since 2019. So we currently have the data of about 6 years from 2019 to 2024. Now we have the year wise sales data in the excel format.

Next step was to clean the data. In this case the data was very mis managed. There were multiple values clubbed into one column. There very many anomalies which needed to be fixed.

So to clean the data for further steps I first of all organised all the data into one file then one by one using excel formulas and filters sorted the whole data, which is now ready to be used for the next steps.

This process could also be done using python, but since the data was very unorganised so I felt it easier to do it in excel itself.

---

### Exploratory Data Analysis and its conclusion

![montlysales vs quantity.png](Images/montlysales%20vs%20quantity.png)

Bar Plot of the monthly sales

From the bar plot labeled **“Monthly Sales vs Quantity”**, we can infer several key trends and patterns regarding the **Quantity (in KGs)** sold over time (on a monthly basis):

1. **Seasonal Trends:**
   There are seasonal fluctuations in the data. The sales tend to rise and fall in a cyclical manner, particularly visible around the end of each year or early in the following year.
   Peaks in sales are evident in several months, for example, early **2020**, **2021**, and **2022**, while dips are seen particularly in mid-2020 and mid-2023. This may suggest seasonal demand fluctuations or external factors influencing production or sales during those periods.
2. **Overall Stability:**
   Despite fluctuations, there’s a relatively consistent range in the majority of sales quantities. It suggests that even though there are spikes and dips, the overall quantity stabilizes after recovery periods, indicating a somewhat resilient business model.
3. **Long-Term Growth and Declines:**
   Long-term, the data suggests periodic growth in sales quantity followed by subsequent dips. The cause of these dips is the market off-season, which is generally the monsoons (July-October)

---

### Trying Different Models and their inference

### Linear Regression:

While applying linear regression the MAE (mean absolute error) comes out to be very high.

MAE = ~9579.64

This linear regression model cannot capture relationship between date and quantity very well. This may be for various reasons such as:

1. **Time Series nature of data**: LR does not take into account the sequential nature of the data. This leads to poor performance, especially if there are trends, seasonality, or autocorrelations in the data.
2. **Scaling of DATE:** The DATE column is being converted into a numerical timestamp, which can result in very large values.  Large numeric values can skew the regression model. You may want to **normalize or scale** the DATE values before fitting the model.
3. **Non-linear Relationships:** Linear regression assumes a linear relationship between DATE (time) and Quantity. If the relationship between the time and quantity is **non-linear**, linear regression won’t capture that complexity, leading to higher errors.
   You could experiment with polynomial regression or other regression techniques like **Random Forest Regressor** or **Gradient Boosting**.

### Polynomial Regression:

MAE = ~ 9829.74

1. **Polynomial Degree Might Not Be Optimal:** You used a polynomial regression model of degree 2. It’s possible that a higher degree polynomial might fit the data better, but at the risk of **overfitting**. You can experiment with different polynomial degrees (e.g., 3, 4, 5), but higher degrees also introduce the risk of modeling noise rather than the underlying pattern.
2. **Time Series Patterns Not Captured:** Polynomial regression fits based on the numeric transformation of the DATE (timestamp), but it doesn’t take into account the **time series nature** of the data. Time series data often has trends, seasonality, and autocorrelation that linear and polynomial models fail to capture.
3. **Possible Non-Linear Relationship Between Time and Quantity: T**he relationship between DATE and Quantity is **non-linear**, but polynomial regression might not be flexible enough to model it. For instance, polynomial models assume that the underlying relationship is smooth, which might not be true for your data.
4. **Potential Data Anomalies or Trends: H**igh MAE suggests that there might be **outliers**, **sudden jumps** in Quantity, or a significant **underlying trend** that is not being captured by these models.

### Random Forest Regressor

---
