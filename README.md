
# Pharmaceutical Demand Forecasting

This project focuses on analyzing historical pharmaceutical sales data and forecasting future demand.

I used three different approaches — ARIMA, SARIMA, and XGBoost — and compared their performance to see which model works best for this dataset.

## Objective

The main goal of this project is to:

- Understand the demand patterns in pharmaceutical sales.
- Explore trends and weekly patterns in the data.
- Build different forecasting models.
- Compare ARIMA, SARIMA, and XGBoost.
- Evaluate the models using MAE, RMSE, and MAPE.
- Select the model with the best performance.
- Use the selected model to forecast future demand.

## About the Data

The dataset contains pharmaceutical sales data from 2014 to 2019.

The original data contains sales information for different pharmaceutical products, which are grouped into 8 ATC categories:

- M01AB
- M01AE
- N02BA
- N02BE
- N05B
- N05C
- R03
- R06

For this project, I worked mainly with the daily sales data and created a `total_demand` variable by combining the demand across the drug categories.

The daily dataset contains 2,106 observations.

### Dataset Source

Pharma Sales Data – Kaggle

https://www.kaggle.com/datasets/milanzdravkovic/pharma-sales-data

## Project Workflow

### 1. Data Preparation
- Loaded the pharmaceutical sales data.
- Converted the date column into datetime format.
- Checked the data for missing values and duplicates.
- Created the total daily demand.

### 2. Exploratory Data Analysis

I explored the data to understand how demand changes over time.

Some of the analysis included:

- Daily demand trends
- 7-day rolling average
- 30-day rolling average
- Monthly patterns
- Weekday patterns
- ACF and PACF analysis

### 3. Train-Test Split

The data was divided chronologically:

- Training data: 80%
- Testing data: 20%

The test data was kept separate so that the models could be evaluated on unseen observations.

## Models Used

### ARIMA

ARIMA was used as one of the traditional time-series forecasting approaches.

Best model selected:

`ARIMA(2,0,2)`

### SARIMA

SARIMA was tested to capture the weekly seasonal pattern observed in the data.

Best model:

`SARIMA(1,0,3)(1,0,1,7)`

The `7` represents the weekly seasonal period.

### XGBoost

XGBoost was used with time-based and historical demand features.

Features included:

- Lag 1, 2 and 3 days
- Lag 7, 14 and 30 days
- 7-day rolling mean
- 14-day rolling mean
- 30-day rolling mean
- Day of week
- Month
- Year

## Model Results

| Model | MAE | RMSE | MAPE |
|---|---:|---:|---:|
| ARIMA (2,0,2) | 17.98 | 23.80 | 27.48% |
| SARIMA (1,0,3)(1,0,1,7) | 33.82 | 39.27 | 49.23% |
| XGBoost | 15.34 | 20.79 | 23.31% |

## Final Result

Among the three models, **XGBoost performed the best on the test data**.

It had the lowest:

- MAE
- RMSE
- MAPE

The XGBoost model was also used to generate a 30-day future demand forecast.

## Tools Used

- Python
- Pandas
- NumPy
- Matplotlib
- Statsmodels
- Scikit-learn
- XGBoost
- Jupyter Notebook

## Key Takeaway

This project helped me compare traditional time-series models with a machine learning approach for pharmaceutical demand forecasting.

For this dataset, XGBoost gave better results than ARIMA and SARIMA on the test data.
