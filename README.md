# dinedash-databricks-dlt-workflows-dashboards
Big data pipeline built on Databricks and Apache Spark for real-time insights. Utilizes a Data Lake for centralized storage, Delta Live Tables (DLT) for ETL, structured streaming for live order analytics, and dashboards to visualize customer trends and delivery performance.

• Data Lake: A centralized repository for storing all structured and unstructured data, 
including order details, customer information, menu data, and delivery logs. 
• ETL Pipelines: Using Delta Live Tables (DLT) to manage the transformation of raw 
data into usable formats for analysis. The pipeline will clean, enrich, and structure the 
data for downstream analytics. 
• Real-Time Streaming: Processing incoming orders in real-time using structured 
streaming to calculate metrics like order volume, delivery times, and detect any 
operational anomalies as they occur. 
• Analytics Dashboards: Developing dashboards to visualize customer trends, restaurant 
performance, order patterns, and delivery efficiency.

### Attributes
DineDash will track the following key attributes across different tables: 
1. Customers 
• customer_id: Unique identifier for each customer. 
• name: Name of the customer. 
• email: Email address of the customer. 
• signup_date: Date customer signed up

2. Restaurants 
• restaurant_id: Unique identifier for each restaurant. 
• name: Name of the restaurant. 
• cuisine: Type of cuisine (e.g., Italian, Chinese, Indian). 
• location_id: Geographic location (latitude/longitude) of the restaurant

3. Menu Items 
• item_id: Unique identifier for each menu item. 
• restaurant_id: Foreign key referencing restaurants. 
• item_name: Name of the menu item (e.g., "Margherita Pizza"). 
• price: Price of the menu item.

4. Orders 
• order_id: Unique identifier for each order. 
• timestamp: Time the order was placed. 
• customer_id: Foreign key referencing customers. 
• restaurant_id: Foreign key referencing restaurants. 
• agent_id: 
• delivery_location_id:  
• items_ordered: List of items in the order (can be a list of menu_item_ids). 
• Total_amount: 
• Tip: 
• payment_method: Payment method used (e.g., "Credit Card", "Cash"). 
• order_status: Status of the order (e.g., "Pending", "Delivered").

5. Delivery Agent 
• agent_id: Unique identifier for each delivery. 
• name:  
• phone: 
• rating:

## Data Model
<img width="631" height="457" alt="image" src="https://github.com/user-attachments/assets/43b164e3-5d0a-4f62-8373-00828d30434e" />

## Process Flow

Pipeline Creation using DLT (Medallion Architecture):
Designed a Delta Live Tables (DLT) pipeline in SQL following the Medallion Architecture (Bronze → Silver → Gold).
1. Bronze Layer: Ingested raw data from various sources (orders, customers, restaurants, menu items, agents).
2. Silver Layer: Cleaned, transformed, and standardized the raw data by applying joins, filters, and schema enforcement.
3. Gold Layer: Created aggregated and business-ready tables for analytics — including metrics like total revenue, average delivery time,                and top-performing restaurants.

Dashboard Development:
Queried the Gold tables to extract relevant KPIs and visual metrics.
Built interactive dashboards within Databricks to display insights such as:
1.Customer activity trends
2.Restaurant performance
3.Delivery agent efficiency
4.Order volume and success rates
Dashboards update automatically as new data flows into the pipeline.

Workflow Automation with Databricks Jobs
1.Created a Databricks Job to automate the full process.
2.The job runs the DLT pipeline first, ensuring all Bronze, Silver, and Gold tables are refreshed with the latest data.
3.Once the pipeline run completes successfully, the dashboard refresh is triggered, ensuring real-time metrics and visualizations are always up to date.
4.This setup enables end-to-end automation, minimal manual intervention, and continuous data-driven insights.

### Summary:
Data Ingestion → DLT Pipeline (Bronze → Silver → Gold) → Gold Tables → Dashboards → Automated Job Workflow


