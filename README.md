# Hospitality_Project
Project on Hospitality Industry giving insights into Booking Data
SQL Analysis
SQL queries were used to extract and process data for the KPIs and visualizations. Some key queries include:

Total Bookings:

sql
Copy code
SELECT SUM(successful_bookings) AS total_bookings
FROM fact_aggregated_bookings;
Average Daily Rate (ADR):

sql
Copy code
SELECT SUM(revenue_realized) / SUM(successful_bookings) AS ADR
FROM fact_bookings;
Revenue per Available Room (RevPAR):

sql
Copy code
SELECT SUM(revenue_realized) / SUM(total_capacity) AS RevPAR
FROM fact_bookings
JOIN fact_aggregated_bookings USING(hotel_id);
Occupancy Rate by City:

sql
Copy code
SELECT 
    h.city,
    SUM(fab.successful_bookings) AS total_successful_bookings,
    SUM(fab.total_capacity) AS total_capacity,
    (SUM(fab.successful_bookings) / SUM(fab.total_capacity)) * 100 AS occupancy_rate
FROM 
    fact_aggregated_bookings fab
JOIN 
    dim_hotels h ON fab.hotel_id = h.hotel_id
GROUP BY 
    h.city
ORDER BY 
    occupancy_rate DESC;
Visualizations
Tableau Dashboards:

Bookings Over Time: Visualizes the number of bookings over different time periods.
Revenue Analysis: Shows revenue trends and comparisons across different hotels and time periods.
Occupancy and ADR: Displays occupancy rates and ADR for different cities and hotels.
Power BI Dashboards:

Revenue Performance: Interactive charts showing revenue performance and KPIs.
City-wise Analysis: Provides insights into the performance of hotels across different cities.
Monthly Trends: Highlights monthly trends in bookings, revenue, and other KPIs.
Repository Structure
graphql
Copy code
|-- data/                   # Contains the raw and processed data files
|-- sql/                    # Contains the SQL scripts used for data extraction and processing
|-- tableau/                # Contains Tableau workbook files
|-- powerbi/                # Contains Power BI report files
|-- images/                 # Contains screenshots of dashboards
|-- README.md               # Project summary and details
How to Run
SQL Scripts: Execute the SQL scripts in the sql/ directory to create and populate the database tables.
Tableau: Open the Tableau workbook files in the tableau/ directory to view and interact with the dashboards.
Power BI: Open the Power BI report files in the powerbi/ directory to explore the visualizations.
Conclusion
This project provides valuable insights into the hotel booking patterns and key performance metrics. The use of SQL for data processing and Tableau and Power BI for visualization showcases the effective use of these tools in the analysis of hospitality industry data.


