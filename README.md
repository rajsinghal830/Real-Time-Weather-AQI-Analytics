# 🌦️ Real-Time Weather & AQI Analytics Dashboard

A modern and interactive Power BI dashboard that provides **real-time weather insights, 7-day forecasts, and Air Quality Index (AQI) analytics** using data from WeatherAPI.

![Dashboard Preview](Images/dashboard.png)

---

## 📌 Project Overview

This project integrates **WeatherAPI** with **Power BI** to create a visually appealing weather analytics dashboard. Users can monitor current weather conditions, forecast trends, precipitation probability, air quality metrics, and environmental indicators across multiple cities.

The dashboard is designed to demonstrate:

* API Integration
* Power BI Data Modeling
* Power Query Transformations
* DAX Measures
* Interactive Dashboard Design
* AQI Analytics & Conditional Formatting

---

## 🚀 Features

### 🌡️ Weather Monitoring

* Current Temperature
* Weather Condition
* Humidity
* Wind Speed
* Visibility
* Pressure
* UV Index
* Precipitation

### 📅 Forecast Analytics

* 7-Day Temperature Forecast
* Daily Weather Cards
* Chance of Rain Analysis
* Sunrise & Sunset Information

### 🌍 Air Quality Analytics

* Overall AQI Status
* AQI Category Classification
* AQI Health Suggestions
* Pollutant Monitoring:

  * PM10
  * PM2.5
  * CO
  * SO₂
  * NO₂
  * O₃

### 🎨 Interactive Features

* Dynamic City Selection
* Conditional Formatting
* AQI Color Coding
* Responsive Dashboard Layout
* Modern Dark-Themed UI

---

## 🛠️ Tech Stack

| Technology  | Purpose                          |
| ----------- | -------------------------------- |
| Power BI    | Dashboard Development            |
| Power Query | Data Extraction & Transformation |
| DAX         | Calculated Measures              |
| WeatherAPI  | Real-Time Weather Data           |
| JSON        | API Response Format              |
| GitHub      | Version Control                  |

---

## 🔗 Data Source

Weather data is fetched from WeatherAPI.

API Endpoint Example:

```bash
https://api.weatherapi.com/v1/forecast.json?key=YOUR_API_KEY&q=CITY_NAME&days=7&aqi=yes
```

Data includes:

* Current Weather
* Forecast Weather
* Air Quality Information
* Astronomy Data
* Location Details

---

## 📂 Data Model

The dashboard uses multiple tables:

### Current

Stores current weather and AQI metrics.

### Forecast_Day

Stores daily forecast information.

### Forecast_Hour

Stores hourly forecast data.

### Astronomy

Stores sunrise and sunset timings.

---

## 📊 Key DAX Measures

### Current Temperature

```DAX
Curr_Temp_C =
SUM('Current'[current.temp_c]) & " °C"
```

### Forecast Temperature

```DAX
For_Temp_C =
FORMAT(
AVERAGE(Forecast_Day[forecast.forecastday.day.avgtemp_c]),
"0.0"
) & " °C"
```

### AQI Status

```DAX
AQI_Status_Text =
SWITCH(
TRUE(),
AQI <= 50, "Good",
AQI <= 100, "Moderate",
AQI <= 150, "Unhealthy for Sensitive",
AQI <= 200, "Unhealthy",
AQI <= 300, "Very Unhealthy",
"Hazardous"
)
```

### AQI Suggestion

```DAX
AQI_Suggestion =
SWITCH(
TRUE(),
AQI <= 50, "Air is clean and healthy",
AQI <= 100, "Acceptable air quality, stay active",
AQI <= 150, "Sensitive groups should reduce outdoor time",
AQI <= 200, "Limit prolonged outdoor exertion",
AQI <= 300, "Avoid outdoor activity if possible",
"Stay indoors, wear a mask if outside"
)
```

---

## 🎨 AQI Color Coding

| AQI Range | Status                     |
| --------- | -------------------------- |
| 0 – 50    | Good 🟢                    |
| 51 – 100  | Moderate 🟡                |
| 101 – 150 | Unhealthy for Sensitive 🟠 |
| 151 – 200 | Unhealthy 🔴               |
| 201 – 300 | Very Unhealthy 🟣          |
| 300+      | Hazardous ⚫                |

---

## 📈 Dashboard Components

### Left Panel

* Current Weather
* City Selector
* Weather KPIs

### Center Panel

* Temperature Forecast Trend
* AQI Gauge
* Pollutant Indicators

### Right Panel

* Sunrise & Sunset
* Rain Probability Analysis

---

## 🔄 Dashboard Workflow

```text
WeatherAPI
      ↓
Power Query
      ↓
Data Transformation
      ↓
Data Model
      ↓
DAX Measures
      ↓
Power BI Dashboard
```

---

## 📷 Dashboard Preview

Add screenshots inside the Images folder:

```text
Images/
├── dashboard.png
├── forecast.png
├── aqi.png
```

---

## 📌 Future Enhancements

* Historical Weather Analysis
* Real-Time Refresh
* Weather Alerts
* Multi-City Comparison
* PostgreSQL Integration
* Power BI Service Deployment

---

## 👨‍💻 Author

**Raj Singhal**

B.Tech Student | Data Analytics | Power BI | SQL | Python


