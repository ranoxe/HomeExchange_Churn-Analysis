# 🔗 Project Resources (Google Drive)
All project materials are available in the Drive folder, including:  
- The interactive **dashboard file**  
- The **Demo Day presentation** from the Le Wagon Bootcamp  

👉 **Drive link:** *[https://drive.google.com/drive/folders/1acpF85OpPgenaN2YI-FU53jnpezqjBro?usp=sharing]*

---

# 👥 Team Members
This project was completed as part of the **Le Wagon Data analysis Bootcamp** by:

- **YASSINE EZZAARATE**  
- **YASMINE EL KHALTI**  
- **Rania El Abyad**

---
# 🏡 HomeExchange_Churn-Analysis

This project analyzes subscription rates and churn on the HomeExchange platform from a financial and transactional perspective.  
It examines user behavior to identify the key factors that influence subscription renewal.  
The study focuses on data from **2019 to 2021** to provide actionable insights for improving retention.

---

# 📌 Project Overview
This project focuses on understanding why users renew or cancel their HomeExchange subscription.  
It integrates subscription history, user activity, and exchange behavior to detect drivers of churn and renewal, and includes financial analysis, behavioral analysis, and machine learning modeling.

---

# 🎯 Objectives
- Analyze subscription rates and churn for HomeExchange members.  
- Understand how exchange activity influences renewal.  
- Identify user segments and behavioral patterns.  
- Build a predictive model to estimate churn probability.  
- Provide recommendations to increase retention and loyalty.

---

## 🛠️ Data Pipeline & Tools

This project follows a clear data workflow using specialized tools for each phase:

### 1. Data Processing and Preparation

This phase includes data cleaning, transformation, and joining of the two main data sources (Exchanges and Subscriptions).

- **Cleaning & Initial Aggregation:** **BigQuery (SQL)**
- **Joining & Feature Engineering:** **Python** (via Google Colab)

### 2. Analysis and Visualization

- **Dashboarding:** **Power BI**

### 3. Machine Learning

- **Modeling & Prediction:** **Python**

---

# 🗂️ Data Schema & Description

## **1. Exchanges Table**

Represents **all conversation/exchange requests** initiated or received by subscribed users.  
Used to understand how user activity impacts renewal likelihood.

> ⚠️ Note: Multiple user profiles exist (users active all year, summer-only travelers, etc.).  
> So **volume alone is not enough** to explain renewal — we analyze context, duration, and success.

### **Exchanges Fields**
- `conversation_id` – ID of the conversation initiated  
- `exchange_id` – ID of the exchange  
- `created_at` – date the exchange request was created  
- `creator_id` – ID of the user who initiated the exchange  
- `guest_user_id` – user acting as guest  
- `host_user_id` – user acting as host  
- `finalized_at` – date when the exchange was finalized (null if not successful)  
- `canceled_at` – date when a finalized exchange was cancelled  
- `start_on` – requested exchange start date  
- `end_on` – requested exchange end date  
- `guest_count` – number of guests  
- `night_count` – number of nights  
- `user_cancellation_id` – user who canceled  
- `exchange_type` – *GuestPoints* or *Reciprocal*  
- `home_type` – house or apartment  
- `residence_type` – primary or secondary residence  
- `capacity` – hosting capacity  
- `country`, `region`, `department`, `city` – host house location  

### ⚠ Important Notes
- For **reciprocal exchanges**, *one conversation = two exchanges*  
  (roles are reversed: guest ↔ host).  
- When counting activity, pay attention to:  
  - **requests sent**  
  - **requests received**  
  - **finalized exchanges**  

---

## **2. Subscriptions Table**

Sample of user subscriptions since 2019.  
If a user subscribed for multiple years, there is **one line per subscription year**.

If `renew = 1`, the dataset contains:
- the subscription line  
- the renewal line for the following year  

### **Subscription Fields**
- `subscription_date` – date of subscription  
- `user_id` – user identifier  
- `renew` – 1 if user renewed the following year  
- `first_subscription_date` – first time the user subscribed  
- `first_subscription` – 1 if it is the user’s first subscription  
- `referral` – 1 if user has been sponsored  
- `promotion` – 1 if user had a discount  
- `payment3x` – 1 if user paid in 3 installments  
- `payment2`, `payment3` – paid installments  
- `country`, `region`, `department`, `city` – user location  

---

# 🧹 Data Preparation & Merge
- Cleaning of duplicates and invalid rows  
- Standardization of dates and locations  
- Feature engineering  
- Merge of Exchanges + Subscriptions

### 🔗 Join Keys
- **user_id = guest_user_id**  
- **subscription_year = created_year**

### 📊 Final Dataset
- Rows: **3,627,602**  
- Columns: **37**

---

# 🤖 Machine Learning
A binary classification model was built to predict churn/renewal.

### Results:
- **Accuracy: 68.6%**  
Indicates a reasonable ability to distinguish between users likely to renew and those at risk of churn.

---

# 📝 Recommendations
1. Personalized reminders for availability updates or renewal.  
2. Optional insurance to increase trust.  
3. Mandatory location data during registration.  
4. Mandatory review system after exchanges.  

---

# 📁 Project Structure
