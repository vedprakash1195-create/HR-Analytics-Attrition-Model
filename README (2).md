# HR Analytics Dashboard – Power BI/ SQL

## 📊 Project Overview

An interactive HR Analytics Dashboard developed using Microsoft Power BI
to analyze employee attrition and identify key HR trends.

## 🎯 Objectives

- Analyze employee attrition
- Understand attrition across different age groups
- Analyze attrition by salary slab
- Analyze attrition by job role
- Analyze attrition by education
- Analyze attrition by tenure
- Compare attrition by gender
- Track key HR KPIs

## 📌 Key KPIs

- Total Employees: 1,470
- Total Attrition: 237
- Attrition Rate: 16.1%
- Average Age: 37
- Average Salary: 6.5K
- Average Tenure: 7.0 Years

## 📈 Dashboard Analysis

The dashboard includes:

- Attrition by Education
- Attrition by Age
- Attrition by Salary Slab
- Attrition by Tenure
- Attrition by Job Role
- Attrition by Gender
- Job Role and Tenure analysis

## 🗄️ SQL Analysis

SQL Server was used to calculate the core HR KPIs and attrition breakdowns before/alongside the Power BI visualization.

**Sample Queries:**

```sql
-- Total employees and attrition count
SELECT 
    COUNT(*) AS Total_Employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Total_Attrition,
    ROUND(SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 1) AS Attrition_Rate
FROM Employee_Data;

-- Attrition by Age Group
SELECT 
    CASE 
        WHEN Age BETWEEN 18 AND 25 THEN '18-25'
        WHEN Age BETWEEN 26 AND 35 THEN '26-35'
        WHEN Age BETWEEN 36 AND 45 THEN '36-45'
        ELSE '46+' 
    END AS Age_Group,
    COUNT(*) AS Total,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count
FROM Employee_Data
GROUP BY 
    CASE 
        WHEN Age BETWEEN 18 AND 25 THEN '18-25'
        WHEN Age BETWEEN 26 AND 35 THEN '26-35'
        WHEN Age BETWEEN 36 AND 45 THEN '36-45'
        ELSE '46+' 
    END;

-- Attrition by Job Role
SELECT 
    JobRole,
    COUNT(*) AS Total_Employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count,
    ROUND(SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 1) AS Attrition_Rate
FROM Employee_Data
GROUP BY JobRole
ORDER BY Attrition_Rate DESC;

-- Attrition by Salary Slab
SELECT 
    CASE 
        WHEN MonthlyIncome <= 5000 THEN 'Up to 5K'
        WHEN MonthlyIncome BETWEEN 5001 AND 10000 THEN '5K-10K'
        WHEN MonthlyIncome BETWEEN 10001 AND 15000 THEN '10K-15K'
        ELSE '15K+' 
    END AS Salary_Slab,
    COUNT(*) AS Total,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count
FROM Employee_Data
GROUP BY 
    CASE 
        WHEN MonthlyIncome <= 5000 THEN 'Up to 5K'
        WHEN MonthlyIncome BETWEEN 5001 AND 10000 THEN '5K-10K'
        WHEN MonthlyIncome BETWEEN 10001 AND 15000 THEN '10K-15K'
        ELSE '15K+' 
    END;
```

These query results were then connected to Power BI for interactive visualization and dashboard reporting.

## 🛠️ Tools & Technologies

- Power BI
- SQL Server
- DAX
- Data Visualization
- Data Analysis
- Microsoft Excel


## 💡 Key Insights

- The highest number of attritions comes from employees earning up to 5K.
- The 26–35 age group has the highest attrition.
- Laboratory Technicians and Sales Executives show relatively high attrition.
- Attrition varies significantly across education and job roles.

## 👨‍💻 Author

Ved Prakash
