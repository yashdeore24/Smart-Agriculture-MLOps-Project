# 🌱 Smart Agriculture MLOps

An **AI-powered Smart Agriculture application** designed to help farmers make data-driven decisions using Machine Learning, FastAPI, React, and MLOps practices.

The application provides intelligent recommendations and predictions for crop selection, fertilizer usage, irrigation planning, agricultural commodity prices, and crop yield estimation.

## 🚀 Features

- 🌾 **Crop Recommendation:** Recommends suitable crops based on soil and environmental conditions.
- 🧪 **Fertilizer Recommendation:** Suggests suitable fertilizers to support crop growth.
- 💧 **Smart Irrigation:** Predicts irrigation requirements to help optimize water usage.
- 📈 **Price Prediction:** Forecasts agricultural commodity prices to support better market planning.
- 🌿 **Yield Prediction:** Estimates agricultural production using machine learning models.
- 🌦️ **Live Weather Integration:** Fetches current weather information and a five-day forecast using OpenWeatherMap.
- ⚡ **FastAPI Backend:** Provides REST APIs for model predictions and weather data.
- 🖥️ **React Frontend:** Offers a user-friendly interface for interacting with the application.
- 🔄 **MLOps Integration:** Organizes model training, artifact storage, and backend model integration.

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| Programming Language | Python |
| Machine Learning | Scikit-learn |
| Backend | FastAPI |
| Frontend | React, Vite |
| Model Serialization | Joblib |
| Weather API | OpenWeatherMap |
| Package Management | pip, npm |
| Version Control | Git, GitHub |
| Environment | Python Virtual Environment |

## 📁 Project Structure

```text
Smart-Agriculture-MLOps/
│
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   ├── model_service.py
│   │   ├── api/
│   │   │   └── routes/
│   │   └── models/
│   │       └── *.joblib
│   └── requirements.txt
│
├── ml/
│   ├── crop_recommendation/
│   │   └── train.py
│   ├── fertilizer/
│   │   └── train.py
│   ├── irrigation/
│   │   └── train.py
│   ├── price_prediction/
│   │   └── train.py
│   └── yield_prediction/
│       └── train.py
│
├── data/
│   └── Training datasets
│
├── frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── vite.config.js
│
├── .gitignore
└── README.md
```

## ⚙️ Installation and Setup

### 1. Prerequisites

Make sure the following tools are installed:

- Python 3.11 or higher
- Node.js and npm
- Git
- OpenWeatherMap API key

### 2. Clone the Repository

```bash
git clone https://github.com/yashdeore24/Smart-Agriculture-MLOps-Project.git
cd Smart-Agriculture-MLOps-Project
```

### 3. Set Up the Backend

Create a Python virtual environment:

```powershell
python -m venv .venv
```

Activate the virtual environment:

```powershell
.venv\Scripts\Activate.ps1
```

Install the required Python packages:

```powershell
pip install -r backend\requirements.txt
```

### 4. Configure Environment Variables

Create a `.env` file inside the `backend` directory.

**File:** `backend/.env`

```env
OPENWEATHER_API_KEY=your_openweathermap_api_key
WEATHER_CITY=Hyderabad
```

Replace `your_openweathermap_api_key` with your actual API key.

**Important:** Never share or commit your API key. Make sure `backend/.env` is included in `.gitignore`.

### 5. Start the Backend Server

Run the following command from the project root:

```powershell
uvicorn backend.app.main:app --reload
```

The backend server will be available at:

- **API Base URL:** http://127.0.0.1:8000
- **Swagger API Documentation:** http://127.0.0.1:8000/docs
- **Alternative API Documentation:** http://127.0.0.1:8000/redoc

### 6. Set Up the Frontend

Open a new terminal and navigate to the frontend directory:

```powershell
cd frontend
```

Install the required dependencies:

```bash
npm install
```

Start the frontend development server:

```bash
npm run dev
```

The frontend will be available at:

**http://localhost:5173**

By default, the frontend communicates with the backend at `http://localhost:8000`.

To configure a different backend URL, create a `.env` file inside the `frontend` directory:

```env
VITE_API_URL=http://localhost:8000
```

### 7. Build the Frontend for Production

To create a production build:

```bash
npm run build
```

The generated build files will be stored in the frontend's `dist/` directory.

## 🔗 API Endpoints

The backend exposes the following REST API endpoints:

| HTTP Method | Endpoint | Description |
|---|---|---|
| GET | `/health` | Checks backend health |
| POST | `/api/crop/recommend` | Recommends suitable crops |
| POST | `/api/fertilizer/predict` | Generates fertilizer recommendations |
| POST | `/api/irrigation/predict` | Predicts irrigation requirements |
| POST | `/api/price/predict` | Predicts agricultural commodity prices |
| POST | `/api/yield/predict` | Estimates crop yield |
| GET | `/api/weather` | Retrieves current weather and a five-day forecast |

For request formats, required parameters, and response schemas, visit:

**http://127.0.0.1:8000/docs**

## 🧠 Model Training

The project includes separate training scripts for each machine learning task.

Each training script reads its corresponding dataset from the `data/` directory and saves the trained model as a Joblib artifact inside `backend/app/models/`.

Run the following commands from the project root:

**Crop Recommendation**

```powershell
python ml\crop_recommendation\train.py
```

**Fertilizer Recommendation**

```powershell
python ml\fertilizer\train.py
```

**Irrigation Prediction**

```powershell
python ml\irrigation\train.py
```

**Price Prediction**

```powershell
python ml\price_prediction\train.py
```

**Yield Prediction**

```powershell
python ml\yield_prediction\train.py
```

Retrain the models whenever the source datasets or preprocessing logic changes. Ensure the generated model artifacts are compatible with the backend's prediction service.

## 🧪 Backend Verification

After starting the backend server, verify its functionality using the following commands:

**Check API Health**

```powershell
curl http://127.0.0.1:8000/health
```

**Check Weather API**

```powershell
curl http://127.0.0.1:8000/api/weather
```

If the weather endpoint returns a `503` error:

1. Check that `backend/.env` exists.
2. Verify that the OpenWeatherMap API key is configured correctly.
3. Restart the backend server.
4. Confirm that the API key is active and that the weather service is accessible.

## 🔐 Security and Best Practices

- Store API keys and other sensitive information in environment variables.
- Never commit `.env` files containing credentials.
- Keep the OpenWeatherMap API key on the backend.
- Use the backend to proxy external weather requests instead of exposing API keys to the browser.
- Keep Python dependencies organized in `backend/requirements.txt`.
- Retrain and validate machine learning models when datasets or preprocessing logic change.
- Use Git and GitHub to track project changes and maintain version history.

## 🔮 Future Improvements

- 📊 Interactive dashboards for agricultural insights.
- 🌍 Integration with additional weather and agricultural data sources.
- 📱 Mobile-friendly interface for farmers.
- 🤖 Improved model performance through experimentation and evaluation.
- ☁️ Cloud deployment for wider accessibility.
- 🔄 Automated model retraining and model version management.
- 📉 Advanced monitoring for model performance and prediction quality.

## 👨‍💻 Author

**Yash Deore**

Aspiring AI and Data Science Engineer

- GitHub: [@yashdeore24](https://github.com/yashdeore24)
- LinkedIn: [Yash Deore](https://www.linkedin.com/in/yashdeore25/)

---

⭐ If you find this project useful, consider giving the repository a star!

**Built with Python, Machine Learning, FastAPI, React, and MLOps practices.**
