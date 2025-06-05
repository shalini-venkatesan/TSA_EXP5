### Name: Shalini V
### Reg.No: 212222240096
### Date: 
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### AIM:
To Illustrates how to perform time series analysis and decomposition on seattle weather Dataset.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data = pd.read_csv('/content/weather_data.csv')
print("FIRST FIVE ROWS:")
print(data.head())
data['DATE'] = pd.to_datetime(data['DATE'])
data.set_index('DATE', inplace=True)

# Extract a subset of the data if needed (e.g., first 120 rows)
# For demonstration, let's assume we're analyzing 120 rows
data = data.head(120)  # Adjust this number based on your needs

# Perform seasonal decomposition on the 'PRCP' (precipitation) column
# Adjust the period if you know the seasonality, here 30 assumes monthly seasonality
result = seasonal_decompose(data['PRCP'], model='additive', period=30)

# Plot the original data (precipitation)
print("\nPLOTTING THE DATA:")
plt.figure(figsize=(10, 5))
plt.plot(data['PRCP'])
plt.title('Precipitation Over Time')
plt.xlabel('Date')
plt.ylabel('Precipitation (inches)')
plt.show()

# Plot the seasonal component
print("\nSEASONAL PLOT REPRESENTATION:")
plt.figure(figsize=(10, 5))
result.seasonal.plot()
plt.title('Seasonal Decomposition (Precipitation)')
plt.ylabel('Seasonal Component')
plt.show()

# Plot the trend component
print("\nTREND PLOT REPRESENTATION:")
plt.figure(figsize=(10, 5))
result.trend.plot()
plt.title('Trend Decomposition (Precipitation)')
plt.ylabel('Trend Component')
plt.show()

# Overall decomposition: observed, trend, seasonal, and residuals
print("\nOVERALL REPRESENTATION:")
fig, (ax1, ax2, ax3, ax4) = plt.subplots(4, 1, figsize=(10, 10))
result.observed.plot(ax=ax1)
ax1.set_ylabel('Observed')
result.trend.plot(ax=ax2)
ax2.set_ylabel('Trend')
result.seasonal.plot(ax=ax3)
ax3.set_ylabel('Seasonal')
result.resid.plot(ax=ax4)
ax4.set_ylabel('Residual')
plt.tight_layout()
plt.show()

```
### OUTPUT:
![image](https://github.com/user-attachments/assets/037c7453-5089-4cbd-b701-f1e93af4af6e)

![image](https://github.com/user-attachments/assets/b8045aa7-3272-4210-8550-f77fbc24e856)

![image](https://github.com/user-attachments/assets/78ebf0bd-37b2-491a-80ae-a65896ec719c)

![image](https://github.com/user-attachments/assets/01311e6f-d3ef-4b6f-9ce9-73434c10ad96)

![image](https://github.com/user-attachments/assets/3cea13da-e76c-4d22-8e4d-a2f438a782a0)

![image](https://github.com/user-attachments/assets/d8984471-23c8-4404-b203-962455f9031b)


### RESULT:
Thus The python code has been created for the time series analysis and decomposition.
