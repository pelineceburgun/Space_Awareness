☀️ Solar Wind & Geomagnetic Activity Analysis (Last 5 Years)
Exploratory Data Analysis • Risk Assessment • Time Series Forecasting

This project provides a comprehensive analysis of solar wind and geomagnetic activity over the past five years. It includes a full Exploratory Data Analysis (EDA), a custom space weather risk scoring system, and time series forecasting using Facebook Prophet.

Dataset: SW-Last5Years.csv

📌 Dataset Description

The dataset contains daily observations of solar and geomagnetic parameters:

Column	Description
DATE	Observation date
KP1–KP7 (or KP8)	Kp-index values in 3-hour intervals
ISN	International Sunspot Number
F10.7_OBS	Observed 10.7 cm solar radio flux
F10.7_ADJ	Adjusted 10.7 cm solar radio flux
🎯 Project Objectives

Analyze trends and variability in geomagnetic and solar activity

Build a risk classification system based on Kp-index, ISN, and F10.7 flux

Predict future activity using Prophet forecasting

Perform seasonal decomposition and long-term trend detection

🧹 1. Data Preprocessing

Clean column names and remove whitespace

Convert DATE to datetime

Sort the data chronologically

Handle missing values

Create aggregated metrics:

df['KP_MEAN'] = df[['KP1','KP2','KP3','KP4','KP5','KP6','KP7']].mean(axis=1)

⚠️ 2. Space Weather Risk Assessment

Risk levels are assigned based on custom thresholds:

Metric	High	Medium	Low
KP_MEAN	≥ 5	3–4.9	< 3
F10.7_OBS	≥ 200	150–199	< 150
ISN	≥ 100	50–99	< 50

Scoring:

Low = 1

Medium = 2

High = 3

📌 Total Risk Score Range: 3–9

This score is used to track geomagnetic storm–like conditions over time.

📊 3. Visualizations

The analysis includes:

Time series plots (KP, ISN, F10.7)

30-day rolling averages

Correlation heatmaps

Histograms & boxplots

Seasonal decomposition (365-day period)

Total risk score trend

These visuals help reveal cycles, anomalies, and solar cycle progression.

🛠️ 4. Feature Engineering

Lag features:
KP_MEAN_lag1, lag3, lag7, etc.

Monthly aggregations:
Mean, min, max per month for each metric

These engineered features are later used for modeling and forecasting.

🔮 5. Forecasting with Prophet

The project uses Facebook Prophet to generate 90-day forecasts for:

KP_MEAN

ISN

F10.7_OBS

Prophet captures:

Long-term trend

Yearly seasonality

Short-term fluctuations

Forecast plots include uncertainty intervals and trend components.

📌 Sample Insights (Example Output)
Risk Score Summary:
count    2294.000000
mean        6.215780
min         3.000000
max         9.000000


Observations:

Early 2020 shows elevated Kp activity (solar minimum recovery phase)

F10.7 flux and ISN remain low → overall low solar activity

Elevated risk scores correspond to geomagnetic storm periods

🖼️ Example Visual Outputs

KP Index Trend

Prophet 90-day Forecast

Seasonal Decomposition

Risk Score Timeseries

(Add actual images in your repo using: ![Description](path/image.png))

🔧 Requirements
pandas
matplotlib
seaborn
statsmodels
prophet


Install:

pip install pandas matplotlib seaborn statsmodels prophet

▶️ How to Run

Place SW-Last5Years.csv in the project directory.

Run the analysis script:

python solar_analysis.py


Plots will appear inline in notebooks or in pop-up windows when run as a script.

🚀 Future Enhancements

Add ARIMA/SARIMA models for comparison

Automatic geomagnetic storm detection

Export Prophet forecasts to CSV

Build a Streamlit dashboard

Correlate data with satellite anomaly logs
