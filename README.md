# Forecasting North-Eastern Home Values
# Overview
A Real Estate startup company based out of New York is looking where to invest in single family homes in the North East of the US.

# Data Source
We obtained our dataset from zillow and we downloaded the average price of a house per zipcode (all U.S. zipcodes) from January 31st, 2000 to August 31st, 2021

<b>Data Size:</b> Because our data is so big we decided not to load it onto our github. The data is over 35,000 rows and over 250 columns.

To download this data, please use this link https://www.zillow.com/research/data/, then change the 'Home Values' Geography to zipcode and download.
 
This is a csv file that gives us the average home values in the U.S. for each zipcode per month.

Our target is to forecast future home values in northeast to see which zipcodes would be good for investment purposes. 

Limitation on the dataset is that we don't know if there are any outliers in the average home values per zipcode or if there are any mistakes entered on behalf of the zipcode.

# Top 5 Zipcodes
First we found the top 5 zipcodes that had the highest annual average return per year. 
Next we ran a Dickey-Fuller on each zipcodes time series to check if the data is stationary (none of them were).

After that we made a baseline model for each zipcodes by taking the difference of each average value by the prior one.

![image](https://user-images.githubusercontent.com/83923459/136447015-df9d0ddf-5a4a-4f07-8476-85c38aa8509e.png)

# SARIMAX Model
In order to find the best parameters for our SARIMAX model we ran a gridsearch with some for loops to find the lowest AIC score,
Using the lowest AIC score to plug in we were able to fit and run the model.

# Validating the Model
We then validated the model by holding out the last 2 years.
![image](https://user-images.githubusercontent.com/83923459/136448495-751f47e3-c24a-4840-b84d-ad53d29863b6.png)

After that we checked for the Root Mean Squared Error to see how much our model was off by(typically about 1% of average cost of the house in that zipcode).

# Forecasting
We then forecasted out about 10 years with a confidence interval for prices.
![image](https://user-images.githubusercontent.com/83923459/136448978-ece3b786-e397-498a-a559-8cca36abf9f3.png)

