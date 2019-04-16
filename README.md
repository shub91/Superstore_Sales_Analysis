# Superstore_Sales_Analysis

1. Forecasting future sales for a store using time-series forecasting (SARIMAX)
2. Created a tableau dashboard for the most important KPIs relevant for decision making

This project goes over two important types of analyses and tools that can be done and employed on online sales data. The world of ecommerce is generating data in billions per hour today. A prudent approach and sound statistical techniques can unlock the hidden value resulting in better decision making.

User Life-time Value(LTV) is a measure that tells us how valuable is the user to the business and vice versa. This analysis is used in almost all the verticals today. Be it ecommerce, insurance or any other vertical, knowing what a customer is worth helps the business spend the right amount of resources and effort in the right direction.
Product recommendation Engine is the most widely used and most sophisticated tool being used and adopted by ecommerce and entertainment industry. It can be overlaid on the LTV model to suggest the best product for customers who belong to a certain range of LTV values.

Combined together these methods can boost the marketing campaigns and cause an uplift in online sales for an ecommerce company. The data is available at - https://raw.githubusercontent.com/curran/data/gh-pages/superstoreSales/superstoreSales.csv.



## Data Exploration
Null value treatment - There are 63 records showing null value in the product base margin column. Since 63 just contributes to 0.01% of the data therefore we can safely exclude these records

Data Analysis Trend of profit and sales over the time period (2009-2012) - A plot.ly plot to show the trend of profit and sales over the entire time range. It is an interactive graph and we can zoom in and out to look at different time ranges. The data was aggregated by summing up sales and profit at date level

Shop's response to orders of different priority - This was done to see what kind of response does the shop has for orders of different priority levels. Ideally the shop should react fastest
for critical orders but the data shows a different story. 
Firstly we took a look at the mean value but since we were still unsure about the data we made boxplots to look at other central tendancies

Profit share for different provinces - Folium was used to plot a choropleth map which shows avg. profit coming from different regions of Canada.
Firstly the data was aggregated at a province level and this was used to plot the map.
The .json file used for this is included is geo.json

Correlation between different variables - This correlation plot helps us understand the relationship between different variables. Since there is a component of no. of units sold
in profit and sales, in the second iteration we remove that component by dividing the sales and profit figures by it.
Findings are mentioned in the notebook.

Customer Behaviour/Performance - This analysis helps us understand which customer is more profitable for the business. The graph was plotted keeping profit on y-axis, frequency of purchase
on the x-axis, size of the bubble as the sales value and color representing the consumer segment.
This is done for all the 4 years so that it's easier to compare the performance and to see the top performers yearwise
Modeling

Since the data is such that we cant really define a target variable, we can't really perform a supervised learning method. I chose to do time series because it is one of the most useful analyses in the ecommerce domain. Also the type and structure of data supports that analysis

Firstly we check the stationarity of the original trend using Dicky-fuller test. The result shows that the time series is stationary. We then removethe seasonality and trend from the time series to generalize the series and in order to make a more generalized forecast We then apply SARIMAX model since it has an extra factor of seasonality(in order to factor out the remaining seasonality) as compared to ARIMA arma_order_select_ic was used to determine the best combination of AR and MA. Seasonality factor was chosen as 12 since the yearly trend is quite apparent visually The forecasted time series is generated using the above information

## Prediction

The time series modelled was tested on how good it performs prediction of future events. An RMSE of 0.5 was achieved

## Model 2 - Product recommendation System

An item based recommendation engine was created based on the transaction data to help the shop recommend products to people who buy a particular product in future Collaborative filtering method was used with a similarity measure as cosine similarity The data was first converted into a suitable format(product, customer and sales) product and customer ID are label encoded in order to make the task computationally easier A matrix of product vs. users was created with values indicating number of units bought The values were normalized to bring down to a smaller scale. This was done eeping in ming the similarity measure(cosine) to be used Cosine similarity was used to assign the score to different products with respect toa given product

## Prediction - Product recommendation System

Top 10 relevant products are recommended for a given product

## Tableau workbook

A tableau workbook is created for easier punchy visualizations. There is a filter of measure - profit/sales. User can toggle between these measuers and the graphs will change accordingly.

Link for dashboard: https://tabsoft.co/2UbgwBw
