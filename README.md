![1698093059989](https://github.com/toyinyayu/Call_Center-Analysis/assets/31111105/34e0cbaa-b28e-4c60-aec1-5bddced03458)# Call Center Data Analysis
##Table of Content
- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Tools](#tools)
- [Data Cleaning and Transformation](#data-cleaning-and-transformation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Recommendation](#recommendation)
- [References](#references)


### Project Overview
This projects shows the analysis of a Call Center for October, 2020. In full details of the necessary KPIs needed to drive 
the growth and relevant Decision Making 

![1698093059989](https://github.com/toyinyayu/Call_Center-Analysis/assets/31111105/0754bdf3-6fa4-44fb-ab47-4c4e07ad6b76)


### Data Source
The primary source for the data is "call-center.csv" files, containing the day to day details of aall customers calls for the month of October 2020.

### Tools
- Excel - Data Cleaning and Dashboard
- SQL Server - Data Analysis

### Data Cleaning and Transformation
In the initial data preparation stage, I perform the following:

- Data Loading and Inspection
- Handling Missing Values
- Data Cleaning and Analysis

### Exploratory Data Analysis

- What is the total number of calls?
- What is the Average Satisfactory Calls?
- What is the Average Call Duration in Mins?
- What is the Call trends for the whole month?
- What is the Call Channel by total Call Center?
- How many Call Center By City?
- What are the highest reason for Customers Calls?
- What is the timeframe for Customers call?

### Total Calls

```SQL
SELECT COUNT(id) AS Total_Calls
  FROM [call_center].[dbo].[call_center]
```

### Average Satisfactory Calls

```SQL
SELECT 
	ROUND(AVG(CAST(csat_score AS DECIMAL(10, 2))), 2) AS Avg_Satisfactory_Call
 FROM call_center.dbo.call_center
 WHERE csat_score IS NOT NULL AND csat_score <> 0 ;

```

### Average Call Duration by Mins

```SQL
SELECT 
	ROUND(AVG(CAST(call_duration AS DECIMAL(10, 2))), 2) AS Avg_Call_Duration_by_Mins
  FROM
	call_center.dbo.call_center;

```

### Call Trends From Octobet 1st to October 31st, by Number of Call Centers

```SQL
SELECT call_timestamp, COUNT(call_center) AS COUNT_OF_CALL_CENTER
	FROM 
		call_center.dbo.call_center
	GROUP BY
	call_timestamp
	ORDER BY
	call_timestamp ASC;
```

### Call Channel by Call Centers

```SQL
SELECT channel, COUNT(call_center) AS call_channel_by_call_center
  FROM [call_center].[dbo].[call_center]
  GROUP BY channel 
  ORDER BY call_channel_by_call_center DESC

```
