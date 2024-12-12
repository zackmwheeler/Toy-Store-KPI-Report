# Toy-Store-KPI-Report
####Created an interactive KPI report to track key metrics and explore high-level trends.
Can download the dataset used for the project <a href = "https://maven-datasets.s3.amazonaws.com/Maven+Toys/Maven+Toys.zip">**here**</a>.

### Step 1: Adding Tables and Cleaning Data:


First had to load in the four datasets being used:
![image](https://github.com/user-attachments/assets/72039477-4eb5-4e4b-a63a-ee3254a777a9)


and checked for any NULL values:
![image](https://github.com/user-attachments/assets/47260be6-e4ea-4b29-90c8-fc58607b2cae)


Then added two new columns for `start of month` and `start of week` in the `calendar` table.
![image](https://github.com/user-attachments/assets/35499868-f03d-4ac3-8c7d-91f7ad24bfaf)


### Step 2: Create a Relational Model


Using the `sales` table, added connections to the other three by `Date`, `Product_ID`, and `Store_ID`.
Then chose to 'Hide in report mode' for the `sales` table.
![image](https://github.com/user-attachments/assets/ee16445d-eb9f-411d-b862-20efe522c10a)


Created a date hierarchy containing the `start of month`, `start of week`, and `date` fields
![image](https://github.com/user-attachments/assets/12169d85-dab5-4097-ba37-05db56116671)


### Step 3: Add Calculated Measures & Fields


Created calculated columns in the `sales` table to pull in `cost` and `price` from the products table, then use those fields to calculate `revenue` and `profit` for each transaction
![image](https://github.com/user-attachments/assets/5df31346-f95b-478d-95cc-bdecb3394d70)

The Formulas for each were as follows:
**Cost**
```
Cost = 
RELATED(
    products[Product_Cost]
)
```
**Price**
```
Price = 
RELATED(
    products[Product_Price]
)
```
**Revnue**
```
Revenue = 
sales[Units] *
sales[Price]
```
**Profit**
```
Profit = 
sales[Revenue] -
(sales[Cost] * sales[Units])
```


Then created measures to calculate the count of orders (`total orders`), sum of revenue (`total revenue`) and sum of profit (`total profit`):
![image](https://github.com/user-attachments/assets/da2d18c6-e334-4063-98fd-60e8c0f52162)


### Step 3: Build the Report


Added KPI card visuals showing `total orders`, `total revenue` and `total profit` for the current month, along with monthly trends for each metric:
![image](https://github.com/user-attachments/assets/5cdc9b8f-207f-4072-8889-b94f7be54e63)


Added a slicer to filter the report page by store location:
![image](https://github.com/user-attachments/assets/cb82b3ca-1eb1-4fb4-8640-96d99b1610bb)


Added a bar chart showing ‘total orders’ by product category, and a line chart showing ‘total revenue’ with the date hierarchy on the x-axis:
![image](https://github.com/user-attachments/assets/fae31665-7b81-431c-98be-bfe05ebec5c6)
![image](https://github.com/user-attachments/assets/52d665c2-6404-40fa-892c-02717bbc3799)


Then Formatted the chart for the final product:
![image](https://github.com/user-attachments/assets/1cefa7a0-a0a7-4894-b813-eaba0957edcb)

Thank you for checking out this project!
