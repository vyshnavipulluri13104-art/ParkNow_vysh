# ParkNow – Smart Parking Prediction System

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Tech Stack](#tech-stack)
- [Project Highlights](#project-highlights)
- [Demo](#demo)
- [Appwrite Setup](#appwrite-setup)
- [Local Setup](#local-setup)
- [Flask Prediction Server](#flask-prediction-server)
- [Future Improvements](#future-improvements)

## Overview

ParkNow is a real-time smart parking solution designed to simplify parking management and improve the parking experience. It provides:

- Live parking availability updates.
- Machine learning-based waiting-time predictions.
- Future parking availability planning for cars, bikes, and physically abled users.

Designed for both users and administrators, ParkNow helps streamline parking decisions, particularly during peak hours and events.

## Key Features

| Feature | Description |
|---|---|
| OTP Login | Secure authentication for users. |
| Live Tracking | Real-time vacancy updates across three parking slot categories. |
| Wait-Time Predictions | Machine learning-powered waiting-time estimates when parking slots are full. |
| Trip Planner | Check future parking availability probabilities. |
| Admin Panel | Manage parking slots, events, and view analytics. |

## Tech Stack

- **Frontend:** React Native with Expo
- **Backend:** Appwrite Cloud Database
- **Machine Learning Server:** Flask (Python)
- **Machine Learning Algorithm:** Linear Regression
- **Styling:** Tailwind CSS (NativeWind)

## Project Highlights

### 1. Predictive Parking Wait-Time Estimation

- Developed a predictive Flask microservice exposing REST API endpoints that uses Linear Regression to estimate parking wait times.
- Achieved a Mean Absolute Error (MAE) of **4.2 minutes** on the test set.
- Integrated the prediction service to provide estimated waiting times when parking slots are occupied.

### 2. Real-Time Parking Management

- Integrated Appwrite cloud backend services, including database collections and live status updates, for parking availability management.
- Implemented live status toggling and booking management across **20+ simulated parking slots**.
- Connected the Appwrite backend with a React Native (Expo) client for real-time data consumption.

### 3. Administrative Dashboard

- Built an admin panel for real-time parking slot status control.
- Implemented booking oversight and parking management functionality.
- Enabled administrators to manage parking slots and events.

## Demo

Watch the [ParkNow Demo Video](https://drive.google.com/file/d/1TblDwl9gicRjzqaBoa8vXxgzsFtwGBh7/view?usp=sharing).

## Appwrite Setup

### Collections Structure

#### 1. `parking` Collection

**Attributes:**

| Key | Type | Required |
|---|---|---|
| Slotid | String | Yes |
| Vacancy | Boolean | Yes |
| check_in | String | No |
| check_out | String | No |
| slot_type | Enum | Yes |

#### 2. `waiting` Collection

**Attributes:**

| Key | Type | Required |
|---|---|---|
| slotid | String | Yes |
| wait_time | Double | No |
| check_in | String | Yes |
| check_out | String | No |
| category | Enum | Yes |

#### 3. `event` Collection

**Attributes:**

| Key | Type | Required |
|---|---|---|
| event_name | String | Yes |
| event_type | Enum | Yes |
| event_date | DateTime | Yes |

## Local Setup

### 1. Clone the Repository and Install Dependencies

```bash
git clone https://github.com/vyshnavipulluri13104-art/ParkNow_Vysh.git
cd ParkNow_Vysh
npm install
```

### 2. Configure Environment Variables

Create a `.env` file in the project root directory with the following configuration:

```env
EXPO_PUBLIC_APPWRITE_PROJECT_ID=your_project_id
EXPO_PUBLIC_APPWRITE_DATABASE_ID=
EXPO_PUBLIC_APPWRITE_PARKING_COLLECTION_ID=
EXPO_PUBLIC_APPWRITE_WAITLOG_COLLECTION_ID=
EXPO_PUBLIC_APPWRITE_EVENT_COLLECTION_ID=
EXPO_PUBLIC_FLASK_SERVER=http://localhost:5000
```

Replace the placeholder values with your respective Appwrite project and database configuration.

### 3. Start the Application

```bash
npx expo start
```

## Flask Prediction Server

The machine learning prediction server is maintained in a dedicated repository:

[Parking Availability Predictor](https://github.com/Pudi-Sravan/Parking_avl_predictor)

To connect the Flask server locally:

1. Visit the repository linked above.
2. Follow the setup instructions provided in that repository.
3. Start the Flask server.
4. Ensure that port `5000` is open on your system to connect locally.

### API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/predict_wait` | Returns estimated parking waiting times. |
| POST | `/predict_availability` | Predicts future parking slot availability probabilities. |

## Future Improvements

- Camera-based parking slot detection.
- Google Maps integration.

---

**ParkNow — Plan. Predict. Park.**
