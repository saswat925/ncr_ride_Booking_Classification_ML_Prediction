# 🚖 Ride Booking Status Classification using Machine Learning

## 📌 Project Overview

This project uses Machine Learning to predict the status of a ride booking based on booking-time information, such as vehicle type, pickup location, drop location, booking hour, day of the week, weekend indicator, and month.

The project covers data analysis, feature selection, classification algorithms, model evaluation, prediction on new bookings, and deployment through a FastAPI REST API.

## 🎯 Business Problem

Ride-booking platforms receive bookings that may be completed, cancelled, left incomplete, or fail to find a driver.

Predicting booking outcomes may help businesses understand booking patterns and investigate factors associated with unsuccessful rides.

**Objective:** Build a multi-class classification model to predict the booking status using information available at booking time.

## 📊 Dataset

* **Dataset:** Ride Booking Dataset
* **Records:** 150,000
* **Time period:** January–December 2024
* **Target variable:** `booking_status`
* **Problem type:** Multi-class classification

### Target Classes

The target variable contains five classes:

1. Completed
2. Cancelled by Driver
3. Cancelled by Customer
4. No Driver Found
5. Incomplete

### Features Used

| Feature           | Description                               |
| ----------------- | ----------------------------------------- |
| `vehicle_type`    | Type of vehicle selected                  |
| `pickup_location` | Ride pickup location                      |
| `drop_location`   | Ride destination                          |
| `booking_hour`    | Hour of booking                           |
| `day_of_week`     | Day of the week                           |
| `is_weekend`      | Whether the booking occurred on a weekend |
| `month_name`      | Month of booking                          |

## 🔍 Exploratory Data Analysis

Exploratory Data Analysis (EDA) was used to understand the dataset, examine booking-status distribution, investigate patterns, and prepare features for Machine Learning.

## ⚙️ Machine Learning Workflow

1. Data loading and preparation
2. Exploratory Data Analysis
3. Feature selection
4. Chronological train-test split
5. Model training
6. Model comparison
7. Classification evaluation
8. Saving the trained model
9. Predicting new ride bookings
10. Building a FastAPI prediction service

## 🤖 Algorithms Evaluated

The following classification algorithms were evaluated during the project:

* Logistic Regression
* Decision Tree
* Random Forest
* Extra Trees
* XGBoost
* LightGBM
* CatBoost
* Dummy Classifier as a baseline

## 📈 Model Evaluation

The project evaluates models using accuracy and Macro F1-score.

Macro F1-score is important because the dataset contains imbalanced target classes.

### Current Best Trained Model

The latest verified CatBoost V2 results are:

| Metric         |  Score |
| -------------- | -----: |
| Accuracy       | 26.57% |
| Macro F1-score | 16.95% |

**Important:** These results indicate weak classification performance. The model requires further investigation and improvement before it can be considered suitable for real-world operational use.

The model's predicted probabilities should not be interpreted as calibrated confidence without additional evaluation.

## 🔮 Prediction on New Bookings

A separate notebook, `05_Ride_Booking_Prediction.ipynb`, loads the saved model and predicts the booking status of new ride inputs.

The notebook can also display the model's predicted probabilities for the available booking-status classes.

## 🚀 FastAPI Deployment

FastAPI exposes the trained model through a REST API.

### API Endpoints

| Method | Endpoint   | Purpose                          |
| ------ | ---------- | -------------------------------- |
| GET    | `/`        | Check whether the API is running |
| GET    | `/health`  | Check API health                 |
| POST   | `/predict` | Predict a ride booking status    |

### Example Request

```json
{
  "vehicle_type": "Auto",
  "pickup_location": "AIIMS",
  "drop_location": "Anand Vihar",
  "booking_hour": 10,
  "day_of_week": 2,
  "is_weekend": 0,
  "month_name": "January"
}
```

### Example Response

```json
{
  "predicted_booking_status": "No Driver Found",
  "prediction_probability": 0.214
}
```

*This is an illustrative example. Actual results depend on the trained model and input values.*

## 🛠️ Technologies Used

* Python
* Pandas
* Machine Learning
* CatBoost
* Scikit-learn
* XGBoost
* LightGBM
* FastAPI
* Pydantic
* Joblib
* Jupyter Notebook
* REST API
* Swagger UI

## 📁 Project Files

```text
Ride_Booking_Classification/
│
├── 03_Exploratory_Data_Analysis.ipynb
├── 04_Ride_Booking_ML_Classification.ipynb
├── 05_Ride_Booking_Prediction.ipynb
├── main.py
├── catboost_ride_booking_model.joblib
├── requirements.txt
└── README.md
```

*This is the recommended repository structure. Organize the downloaded files accordingly before uploading them to GitHub.*

## ▶️ Installation and Usage

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Start the API

Make sure `main.py` and the trained model file are in the expected locations.

```bash
uvicorn main:app --reload
```

### 3. Open Swagger UI

Open the following address in your browser:

`http://127.0.0.1:8000/docs`

Use the `/predict` endpoint to submit a ride booking and receive a prediction.

## ⚠️ Limitations and Future Improvements

* Improve classification performance, especially for minority classes.
* Investigate feature quality and potential data leakage.
* Validate that all features are available at the time of booking.
* Evaluate the model on a suitable chronological holdout set.
* Check and improve probability calibration.
* Test the API with valid and invalid inputs.
* Monitor model performance before considering real-world deployment.

## 👨‍💻 Author

**Saswat Betta Aptakam**

GitHub: [saswat925](https://github.com/saswat925)

LinkedIn: [Saswat Betta Aptakam](https://www.linkedin.com/in/saswat-betta-aptakam-65a90919a/)

## 📄 Disclaimer

This project is intended for learning and portfolio demonstration. The current model's performance is limited and should not be used for real-world booking decisions without further validation and improvement.
