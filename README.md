# Estimating Demand Function for Train Travel

This repository contains the code and analysis for estimating the **demand function for train travel** using transaction-level ticket sales data from a single train station.

## Objective

The objective of this project is to estimate the causal relationship between **ticket prices and demand (seats sold)** while accounting for booking behavior, trip characteristics, customer segmentation, and potential **price endogeneity**.

## Data

The analysis uses `Data-GP1.csv`, which includes the following key variables:

* `num_seats_total`: Number of seats sold
* `mean_net_ticket_price`: Average ticket price
* `Dept_Date`, `Purchase_Date`: Departure and purchase dates
* `Train_Number_All`: Masked train identifier
* `Cumulative_sales`: Cumulative tickets sold
* `isNormCabin`: Normal vs special cabin indicator
* `isReturn`, `isOneway`: Trip type indicators
* `Customer_Cat`: Customer segment

## Feature Engineering & Preprocessing

* Computed **days to departure** from purchase and departure dates
* Log-transformed seats and prices for elasticity estimation
* Constructed trip-type categories (one-way, return, neither)
* Added train and year–month fixed effects
* Removed invalid transactions and winsorized outliers

## Methodology

* Baseline **OLS** and **log–log** demand models
* **Instrumental Variables (2SLS)** to address price endogeneity
* **Poisson IV (2SRI)** model to handle count-based demand
* Instrument: leave-one-out train × month mean price
* Model validation using first-stage relevance tests and calibration analysis

## Key Findings

* Price has a **negative and statistically significant** effect on demand
* IV estimates show demand is **elastic**, with price elasticity close to −1
* OLS models underestimate true price sensitivity
* Significant heterogeneity across customer segments and cabin types

## Managerial Insights

* Dynamic and segment-specific pricing strategies are critical
* Early-booking discounts and targeted promotions can increase demand
* Endogeneity-corrected estimates support more reliable pricing decisions

## Reproducibility

All feature engineering, regressions, and plots are implemented in Python.
The analysis is fully reproducible by running the provided notebooks with access to the dataset.


