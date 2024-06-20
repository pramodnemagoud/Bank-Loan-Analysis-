# Bank Loan Analysis Dashboard: An End-to-End Project with SQL Server and Power BI

This project outlines the development of a comprehensive bank loan analysis dashboard suite using SQL Server for data storage and analysis, followed by data visualization in Power BI.

## Project Overview

Financial institutions require a robust system to analyze their loan portfolio performance, identify trends, and make informed decisions. This project delivers a data-driven solution by leveraging the combined strengths of SQL Server and Power BI.

### Workflow:

1. **Data Storage and Management:** Utilize SQL Server to store the bank loan data securely and efficiently.
2. **Data Analysis and Transformation:** Employ SQL queries within SQL Server to analyze the loan data to find insights and for verification with the results of powerBI.
3. **Data Visualization and Exploration:** Import the data into Power BI and transform the data according to requirements to create interactive dashboards that visually represent key insights and trends.

## Key Features

- **Consolidated Data Storage:** Maintain a centralized and secure data repository for all bank loan information within SQL Server.
- **Data Cleaning and Transformation:** Cleanse the raw loan data in SQL Server to address inconsistencies and prepare it for effective visualization in Power BI.
- **KPIs at a Glance:** Gain immediate insights into loan portfolio health through key performance indicators (KPIs) displayed in the Power BI dashboards.
- **Trend Analysis:** Analyze trends over time by visualizing loan applications, approvals, repayments, and other loan characteristics within Power BI.
- **Granular Loan Details:** Explore individual loan information in Power BI through interactive dashboards, allowing for focused analysis of specific loan attributes.
- **Interactive Filtering:** Leverage filters and slicers within Power BI dashboards to refine your analysis by loan term, purpose, employee tenure, application date, or other relevant data points.

## Tools and Technologies

- **Microsoft SQL Server:** This relational database management system acts as the central storage and analysis platform for the bank loan data.
- **SSMS (SQL Server Management Studio):** This acts as an integrated environment for managing any SQL infrastructure.
- **Microsoft Power BI:** This business intelligence tool serves as the primary platform for building and deploying the interactive dashboards for data visualization and exploration.

## Data Requirements

The project requires a dataset containing comprehensive bank loan information. Below is the description ofthe attributes - 
**
1. **ID**: Unique identifier for each loan application.
2. **Address_state**: State in which the borrower resides.
3. **Application_type**: Type of loan application (e.g., individual, joint).
4. **Emp_length**: Length of employment of the borrower.
5. **Emp_title**: Title or occupation of the borrower.
6. **Grade**: Grade assigned to the borrower based on credit risk.
7. **Home_ownership**: Type of home ownership (e.g., own, mortgage, rent).
8. **Issue_date**: Date on which the loan was issued.
9. **Last_credit_pull_date**: Date when the creditor last pulled the borrower's credit report.
10. **Last_payment_date**: Date of the borrower's last payment.
11. **Loan_status**: Status of the loan (e.g., current, fully paid, charged off).
12. **Next_payment_date**: Date of the borrower's next scheduled payment.
13. **Member_id**: Unique identifier for each member.
14. **Purpose**: Purpose of the loan (e.g., debt consolidation, home improvement).
15. **Sub_grade**: Sub-grade assigned to the borrower based on credit risk.
16. **Term**: Duration of the loan (e.g., 36 months, 60 months).
17. **Verification_status**: Indicates if income was verified by the lender.
18. **Annual_income**: Annual income of the borrower.
19. **DTI (Debt-to-Income ratio)**: Ratio of the borrower's total monthly debt payments to their gross monthly income.
20. **Installment**: Monthly payment amount.
21. **Int_rate**: Interest rate on the loan.
22. **Loan_amount**: Total amount of the loan.
23. **Total_acc**: Total number of credit accounts.
24. **Total_payment**: Total amount paid by the borrower**.

### Phase 1: Data Storage and Analysis in SQL Server

# Bank Loan Data Processing Overview

1. **Data Loading:** The specific method for loading data depends on your environment. However, the provided queries assume the data already resides in a table named bank_loan_data.
2. **Key Performance Indicators (KPIs):** The provided queries calculate various KPIs that can be used to understand the overall health of the loan portfolio. These include:
- Loan Applications:
  - Total Loan Applications: `SELECT COUNT(id) AS Total_Applications FROM bank_loan_data`
  - Month-to-Date (MTD) and Previous Month-to-Date (PMTD) Loan Applications: `SELECT COUNT(id) AS Total_Applications FROM bank_loan_data WHERE MONTH(issue_date) = 12` (and similar for PMTD)
- Loan Funding:
  - Total Funded Amount: `SELECT SUM(loan_amount) AS Total_Funded_Amount FROM bank_loan_data`
  - MTD and PMTD Total Funded Amount: (similar queries as applications)
- Loan Repayments:
  - Total Amount Received: `SELECT SUM(total_payment) AS Total_Amount_Collected FROM bank_loan_data`
  - MTD and PMTD Total Amount Received: (similar queries as applications)
- Loan Performance:
  - Average Interest Rate: `SELECT AVG(int_rate)*100 AS Avg_Int_Rate FROM bank_loan_data`
  - MTD and PMTD Average Interest Rate: (similar queries as applications)
  - Average Debt-to-Income Ratio (DTI): `SELECT AVG(dti)*100 AS Avg_DTI FROM bank_loan_data`
  - MTD and PMTD Average DTI: (similar queries as applications)
- Loan Status Analysis:
  - Good Loan vs. Bad Loan Categorization: Define conditions based on specific loan status codes to categorize loans as good or bad. Calculate percentages, application counts, funded amounts, and received amounts for each category.
  - Loan Status Breakdown: `SELECT loan_status, ... FROM bank_loan_data GROUP BY loan_status` - provides various aggregations like loan count, total funded amount, total received amount, average interest rate, and average DTI for each loan status.
3. **Detailed Loan Analysis:** The provided queries demonstrate how to analyze loan data by various dimensions:
- Loan Status
- Month
- State
- Loan Term
- Employee Length
- Loan Purpose
- Home Ownership
4. **Filtering for Dashboards:** The last query showcases how to filter data based on specific criteria (e.g., grade = 'A'). This demonstrates the power of SQL Server in preparing data for visualizations in Power BI dashboards, where users can interact with filters and explore the data in more detail.
  ### Phase 2: Data Visualization and Exploration in Power BI

1. **Connect to SQL Server:** Establish a secure connection between Power BI and the SQL Server database containing the prepared loan data.
2. **Data Import and Modeling:** Import the data from SQL Server into Power BI. Clean and Transform the data for further shaping and modeling.
3. **Dashboard Design and Development:** Create interactive dashboards in Power BI that effectively visualize KPIs, trends, and loan details using measures and new tables using DAX queries.
4. **Testing and Refinement:** Test the dashboards for functionality, usability, and visual appeal. Refine and iterate on the design based on user feedback.

### Importance of Date Table

A dedicated date table created within SQL Server is crucial for time-based analysis in Power BI as mentioned in step 2 of phase 2.
<img width="947" alt="image" src="https://github.com/pramodnemagoud/Bank-Loan-Analysis-/assets/164920277/78e146d9-3598-42d1-b4ac-aea376ae3c8e">
<img width="947" alt="image" src="https://github.com/pramodnemagoud/Bank-Loan-Analysis-/assets/164920277/ba137b1e-652c-40d1-876f-2d3dafca5fdb">
<img width="947" alt="image" src="https://github.com/pramodnemagoud/Bank-Loan-Analysis-/assets/164920277/4998fa8b-0195-4040-9928-d89a3a799178">



## Deliverables

- A secure and well-managed SQL Server database containing the bank loan data.
- A set of interactive Power BI dashboards providing insightful visualizations of KPIs, trends, and loan details according to the ETL process.
- Project documentation outlining the complete workflow, data preparation steps, and functionalities of the dashboards.
