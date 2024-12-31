# Marketing Campaign Analysis and Customer Acquisition Prediction

## Table of Contents
1. [Project Overview](#project-overview)
2. [Business Understanding](#business-understanding)
3. [Data Understanding](#data-understanding)
4. [Data Cleaning](#data-cleaning)
5. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
6. [Data Preprocessing](data-preprocessing)
7. [Modeling and Prediction](#modeling-and-prediction)
8. [Results and Evaluation](#results-and-evaluation)
9. [Conclusion](#conclusion)

## Project Overview
Podha, a growing company, has been running multiple marketing campaigns to acquire new customers. However, due to a crunch in funds, the company has decided to limit its efforts to a single marketing campaign that optimizes budget utilization while maximizing customer acquisition and profitability. Additionally, there is a need to predict customer acquisition based on the available budget.

## Business Understanding
### Stakeholders
1. Company Executives. The results of this project will guide them in making data-driven decisions to maximize ROI and customer acquisition.
2. Marketing Team. The insights will help them focus their efforts on campaigns that generate the highest profitability and customer acquisition rates.

### Business Problem
The company must identify which marketing campaign has brought in the most profitable customers to ensure financial stability and growth. Furthermore, predicting customer acquisition based on budget will help in strategic planning and resource allocation.

Therefore, I aim to:
1. Evaluate the performance of past marketing campaigns.
2. Determine the best acquisition source based on profitability metrics.
3. Predict customer acquisition based on Podha's budget.
4. Provide actionable recommendations supported by data visualization to inform strategic decisions.

## Data Understanding
The dataset provides comprehensive information about customer transactions, including their demographics, purchasing behavior, product preferences, and the sources from which they were acquired.
- **Rows**: 55,910.
- **Columns**: 18.
- **Column Names**: 
     - `Customer Identification and Demographics`: CustID, Customer_Name, Gender.
     - `Transaction and Order Details`: OrderID, OrderLineItem, OrderQuantity, OrderDate, TransactionID.
     - `Geographic Data`: Region, Country.
     - `Product Information`: ProductSKU, Product_Category, ProductCost, ProductPrice.
     - `Customer Acquisition Data`: AcquisitionSource.
     - `Payment Information`: PaymentMethod, CardType.
     - `Risk and Fraud`: Fraud.
- **Data Types**:
     - `Numerical Columns`: 3.
     - `Categorical Columns`: 15.

     **NOTE**: `ProductPrice` is stored as an object and needs to be converted to a numeric format for meaningful statistics.
- **Missing Values**:
     - `Customer_Name`: 3 missing values.
     - `AcquisitionSource`: 1 missing value.
     - `Fraud`: 703 missing values.
     - `CardType`: 5,223 missing values.
     - `Gender`: 6,328 missing values.
- **Relevance to Objectives**
     - `Marketing Campaign Analysis`: Columns such as AcquisitionSource, ProductCost, ProductPrice, and OrderQuantity are directly relevant to calculating profitability and identifying effective campaigns.
     - `Customer Acquisition Prediction`: Fields like Region, Country, AcquisitionSource, and budget-related fields (ProductCost, ProductPrice) can be used to build predictive models.

## Data Cleaning
#### 1. Check for Duplicates:
The dataset was checked for duplicates using df.duplicated().sum(). No duplicates were found.
#### 2. Check for Missing Values:
The dataset was checked for missing values. The following columns had missing values:
- `Customer_Name`: 3 missing values.
- `AcquisitionSource`: 1 missing value.
- `Fraud`: 703 missing values.
- `CardType`: 5,223 missing values.
- `Gender`: 6,328 missing values.

**Dealing with Missing Values**:

The missing values were handled as follows:
- Customer_Name and AcquisitionSource: Missing values were replaced with "Unknown".
- Fraud, CardType, and Gender: These columns were dropped due to a high number of missing values.
#### 3. Filter Relevant Columns:
The dataset was filtered to include only the following relevant columns:
- `AcquisitionSource`: The source through which the customer was acquired.
- `OrderQuantity`: The number of products ordered by the customer.
- `ProductCost`: The cost of the product.
- `ProductPrice`: The selling price of the product.
- `CustID`: A unique identifier for each customer.
#### 4. Convert ProductPrice to Numeric:
The ProductPrice column was converted from object to numeric format.
