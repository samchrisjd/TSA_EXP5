# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 07.10.2025


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

data = pd.read_csv('World_Population.csv')

print("FIRST FIVE ROWS:\n")
print(data.head())

data['Population 2020'] = data['Population 2020'].replace({',': ''}, regex=True)
data['Population 2020'] = pd.to_numeric(data['Population 2020'], errors='coerce')

data.index = pd.RangeIndex(start=1, stop=len(data) + 1, step=1)

plt.figure(figsize=(10, 5))
plt.plot(data['Population 2020'], color='blue', linewidth=2)
plt.title("PLOTTING THE DATA:", fontsize=14, fontweight='bold')
plt.xlabel("Index (Countries / Time Steps)")
plt.ylabel("Population in 2020")
plt.grid(True)
plt.tight_layout()
plt.show()

decomposition = seasonal_decompose(data['Population 2020'], model='additive', period=12)

plt.figure(figsize=(10, 4))
plt.plot(decomposition.seasonal, color='green', linewidth=2)
plt.title("SEASONAL PLOT REPRESENTATION :", fontsize=14, fontweight='bold')
plt.xlabel("Index")
plt.ylabel("Seasonal Component")
plt.grid(True)
plt.tight_layout()
plt.show()

plt.figure(figsize=(10, 4))
plt.plot(decomposition.trend, color='orange', linewidth=2)
plt.title("TREND PLOT REPRESENTATION :", fontsize=14, fontweight='bold')
plt.xlabel("Index")
plt.ylabel("Trend Component")
plt.grid(True)
plt.tight_layout()
plt.show()

plt.figure(figsize=(10, 12))

plt.subplot(411)
plt.plot(data['Population 2020'], label='Original Data', color='blue')
plt.legend(loc='upper left')
plt.title('Original Population Data')

plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Component')

plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonal Component')

plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Component')

plt.tight_layout()
plt.suptitle("OVERAL REPRESENTATION:", fontsize=16, fontweight='bold', y=1.02)
plt.show()

```

### OUTPUT:
FIRST FIVE ROWS:

<img width="1749" height="493" alt="image" src="https://github.com/user-attachments/assets/0fdfc794-9cc3-4960-9a46-114988fb3624" />

PLOTTING THE DATA:

<img width="1735" height="599" alt="image" src="https://github.com/user-attachments/assets/4aac5cb5-4987-408f-a492-dc01af5e1af5" />

SEASONAL PLOT REPRESENTATION :

<img width="1693" height="373" alt="image" src="https://github.com/user-attachments/assets/20232e2a-d67d-430d-b64f-a70fa753af1e" />

TREND PLOT REPRESENTATION :

<img width="1721" height="381" alt="image" src="https://github.com/user-attachments/assets/3dc29217-36f3-4ca3-8963-486b6f568a14" />

RESIDUAL PLOT :

<img width="1709" height="369" alt="image" src="https://github.com/user-attachments/assets/4b222766-f1da-4782-9795-292d483dcdb6" />

### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
