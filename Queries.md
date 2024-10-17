### **Basic Level Questions:**

1. **Find Total Rainfall by District:**
   ```sql
   SELECT District, SUM("Rain (mm)") AS Total_Rainfall
   FROM rainfall_data
   GROUP BY District;
   ```

2. **List the Dates with No Rainfall:**
   ```sql
   SELECT Date, District, Mandal
   FROM rainfall_data
   WHERE "Rain (mm)" = 0;
   ```

3. **Find the Maximum Humidity in a Specific Mandal ('Adilabad Rural'):**
   ```sql
   SELECT MAX("Max Humidity (%)") AS Max_Humidity
   FROM rainfall_data
   WHERE Mandal = 'Adilabad Rural';
   ```

---

### **Intermediate Level Questions:**

1. **Average Rainfall for Each Mandal:**
   ```sql
   SELECT Mandal, AVG("Rain (mm)") AS Average_Rainfall
   FROM rainfall_data
   GROUP BY Mandal;
   ```

2. **Find the Top 5 Wettest Days Across the State:**
   ```sql
   SELECT Date, SUM("Rain (mm)") AS Total_Rainfall
   FROM rainfall_data
   GROUP BY Date
   ORDER BY Total_Rainfall DESC
   LIMIT 5;
   ```

3. **Identify Districts with Consistent Humidity:**
   ```sql
   SELECT District
   FROM rainfall_data
   WHERE ("Max Humidity (%)" - "Min Humidity (%)") <= 10
   GROUP BY District;
   ```

---

### **Advanced Level Questions:**

1. **Find Mandals with Extreme Weather (High Rainfall & Humidity):**
   ```sql
   SELECT District, Mandal, Date
   FROM rainfall_data
   WHERE "Rain (mm)" > 50
   AND "Min Humidity (%)" > 90
   AND "Max Humidity (%)" > 90;
   ```

2. **Compare Rainfall Patterns Between Two Districts (e.g., 'Adilabad' and 'Nizamabad'):**
   ```sql
   SELECT District, Date, COUNT(*) AS Rainy_Days
   FROM rainfall_data
   WHERE District IN ('Adilabad', 'Nizamabad') 
   AND "Rain (mm)" > 30
   GROUP BY District, Date
   ORDER BY District, Rainy_Days DESC;
   ```

3. **Trend Analysis – Rainfall Variation (Day-to-Day):**
   ```sql
   SELECT District, Date, 
          "Rain (mm)" - LAG("Rain (mm)", 1) OVER (PARTITION BY District ORDER BY Date) AS Rainfall_Variation
   FROM rainfall_data
   ORDER BY District, Date;
   ```

These SQL queries for each of the questions based on TG rainfall dataset for September 2024.
