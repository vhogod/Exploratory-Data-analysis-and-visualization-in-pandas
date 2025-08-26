# Exploratory-Data-analysis-and-visualization-in-pandas

## Description

this project demonstrates Exploratory data analysisand manupulatio technique using the pandas library in python, Numpy for numerical computation, Matplotlib for creating static, animated, and interactive visualization, seaborn for statistical data visualization built on Matplotlib and jupiter. I process world population data to handle  data issues and preparing the data for analysis

Key steps in EDA covered:

•  Data loading and initial inspection.

•  Handling missing values and outliers.

•  Descriptive statistics.

•  Univariate, bivariate, and multivariate analysis.

•  Correlation analysis.

•  Advanced visualizations like pair plots and distribution plots.

## example of code

import pandas as pd

## Load a CSV file 
df = pd.read_csv('data/sample_data.csv')

## Inspect the first few rows
print(df.head())

## Get data types and non-null counts
print(df.info())

## Check for duplicates
print(df.duplicated().sum())

## Drop missing values
df_clean = df.dropna()

## Fill missing values with mean
df['column_name'].fillna(df['column_name'].mean(), inplace=True)

## Remove outliers using IQR method
Q1 = df['column_name'].quantile(0.25)
Q3 = df['column_name'].quantile(0.75)
IQR = Q3 - Q1
df_no_outliers = df[(df['column_name'] >= (Q1 - 1.5 * IQR)) & (df['column_name'] <= (Q3 + 1.5 * IQR))]

import matplotlib.pyplot as plt
import seaborn as sns

## Histogram for a single variable
df['numeric_column'].hist(bins=20)
plt.title('Distribution of Numeric Column')
plt.xlabel('Value')
plt.ylabel('Frequency')
plt.show()

## Scatter plot for bivariate analysis
plt.scatter(df['x_column'], df['y_column'])
plt.title('Scatter Plot')
plt.xlabel('X Axis')
plt.ylabel('Y Axis')
plt.show()

## Box plot for categorical vs. numerical
sns.boxplot(x='category_column', y='numeric_column', data=df)
plt.title('Box Plot by Category')
plt.show()

## Heatmap for correlations
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')
plt.title('Correlation Heatmap')
plt.show()

## Pair plot for multivariate analysis
sns.pairplot(df, hue='category_column')
plt.show()
