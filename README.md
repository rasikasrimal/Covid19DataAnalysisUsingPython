# COVID19 Data Analysis using Python

This project provides a hands-on exploration of COVID19 data analysis techniques using Python. It covers data preparation, analysis, and visualization, aiming to understand correlations with happiness metrics.

## Project Overview

- **Course Objectives:** Learn data preparation, exploration, and visualization techniques.
- **Datasets Used:** COVID19 dataset (John Hopkins University) and World Happiness Report dataset.
- **Project Structure:** Divided into tasks covering dataset import, measure calculation, and result visualization.

## Getting Started

1. Clone the repository: `git clone https://github.com/rasikasrimal/Covid19DataAnalysisUsingPython.git`
2. Navigate to the project directory: `cd Covid19DataAnalysisUsingPython`
3. Explore the project files and tasks in the respective folders.

## Requirements

- Python 3
- Libraries: pandas, matplotlib, seaborn

## In Detail Overview Of The Project

1. Importing COVID-19 dataset
```python
import pandas as pd

corona_dataset_csv = pd.read_csv("Datasets/covid19_Confirmed_dataset.csv")
corona_dataset_csv.head(10)
```
![Importing Dataset](https://github.com/rasikasrimal/Covid19DataAnalysisUsingPython/raw/main/Screenshots/importing%20dataset.png)

2.Aggregating the rows by the country
```python
corona_dataset_aggregated = corona_dataset_csv.groupby("Country/Region").sum()
corona_dataset_aggregated.head()
```
![Aggregating the rows by the country](https://github.com/rasikasrimal/Covid19DataAnalysisUsingPython/blob/main/Screenshots/Screenshot%202024-05-14%20214017.png)

3.Visualizing data related to a country for example China
```python
corona_dataset_aggregated.loc["China"][1:].plot(label='China')  
corona_dataset_aggregated.loc["Italy"][1:].plot(label='Italy')

plt.legend()
plt.title('COVID-19 Cases in China and Italy')
plt.xlabel('Date')
plt.ylabel('Total Cases')
plt.grid(True)

plt.show()
```
![Visualizing data related to a country](https://github.com/rasikasrimal/Covid19DataAnalysisUsingPython/blob/main/Screenshots/2.4.png)

4.Calculating a good measure
```python
corona_dataset_aggregated.loc['China'][1:].plot()
```
![Calculating a good measure](https://github.com/rasikasrimal/Covid19DataAnalysisUsingPython/blob/main/Screenshots/3.png)
```python
corona_dataset_aggregated.loc['Italy'][1:].plot()
```
![Calculating a good measure](https://github.com/rasikasrimal/Covid19DataAnalysisUsingPython/blob/main/Screenshots/3.2.png)

5.caculating the first derivative of the curve
```python
countries = list(corona_dataset_aggregated.index)
max_infection_rates = []

for c in countries:
    try:
        numeric_data = corona_dataset_aggregated.loc[c]
        if numeric_data.dtype == 'int64' or numeric_data.dtype == 'float64':
            max_data_infection_rate = numeric_data.diff().max()
            max_infection_rates.append(max_data_infection_rate)
    except Exception as e:
        print(f"Error processing data for {c}: {e}")

max_infection_rates
```


