# CustomerSegmentation
# Customer Segmentation using K-Means Clustering

## Project Overview

Customer segmentation is the process of dividing customers into groups based on common characteristics. This project uses the K-Means Clustering algorithm to analyze customer purchasing behavior and group customers with similar spending patterns.

The goal is to help businesses understand their customers better and develop targeted marketing strategies for different customer groups.

---

## Objective

To create a K-Means Clustering model that groups customers of a retail store based on their Annual Income and Spending Score.

---

## Dataset

### Dataset Name
Mall Customers Dataset

### Dataset Description

The dataset contains information about customers visiting a shopping mall. It includes demographic details and spending behavior.

### Features

- CustomerID – Unique customer identifier
- Gender – Male/Female
- Age – Customer age
- Annual Income (k$) – Annual income in thousand dollars
- Spending Score (1-100) – Score assigned by the mall based on customer spending behavior

### Features Used for Clustering

- Annual Income (k$)
- Spending Score (1-100)

These features were selected because they provide valuable insights into customer purchasing habits.

---

## Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Scikit-Learn

---

## Project Workflow

### 1. Import Libraries

Required libraries such as Pandas, NumPy, Matplotlib, and Scikit-Learn were imported.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
```

### 2. Load Dataset

The dataset was loaded into a Pandas DataFrame.

```python
data = pd.read_csv("Mall_Customers.csv")
```

### 3. Data Exploration

The first few records of the dataset were displayed to understand its structure.

```python
data.head()
```

### 4. Feature Selection

Two important features were selected:

```python
X = data[['Annual Income (k$)', 'Spending Score (1-100)']]
```

### 5. Determine Optimal Clusters

The Elbow Method was used to find the optimal number of clusters.

```python
wcss = []

for i in range(1,11):
    kmeans = KMeans(n_clusters=i, random_state=42)
    kmeans.fit(X)
    wcss.append(kmeans.inertia_)
```

A graph was plotted between:

- Number of Clusters
- WCSS (Within Cluster Sum of Squares)

The "elbow point" indicated the best value for K.

### 6. Apply K-Means Clustering

The K-Means algorithm was trained using 5 clusters.

```python
kmeans = KMeans(n_clusters=5, random_state=42)

y_kmeans = kmeans.fit_predict(X)
```

### 7. Visualize Customer Segments

The clustered customer groups were visualized using a scatter plot.

```python
plt.scatter(X.iloc[:,0], X.iloc[:,1], c=y_kmeans)
plt.xlabel('Annual Income (k$)')
plt.ylabel('Spending Score (1-100)')
plt.title('Customer Segmentation')
plt.show()
```

## Results

The K-Means algorithm successfully divided customers into five distinct groups based on:

- Annual Income
- Spending Score

The generated clusters help identify:

1. High Income – High Spending Customers
2. High Income – Low Spending Customers
3. Low Income – High Spending Customers
4. Low Income – Low Spending Customers
5. Average Income – Average Spending Customers

## Applications

Customer segmentation can be used for:

- Targeted Marketing
- Personalized Recommendations
- Customer Retention Strategies
- Business Decision Making
- Sales and Revenue Optimization

## Conclusion

This project demonstrates the use of the K-Means Clustering algorithm for customer segmentation. By analyzing customer income and spending behavior, meaningful customer groups were identified. These insights can help businesses improve marketing strategies and enhance customer satisfaction.
