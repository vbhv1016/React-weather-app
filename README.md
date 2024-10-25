
# React Weather Dashboard

This is a weather dashboard application built using **React + Vite**. The application provides real-time weather information and a 7-day forecast for different cities. Users can search for cities and view current weather data as well as a 7-day forecast, conversion of Celsius to Fahrenheit powered by the **OpenWeatherMap API**.

## Table of Contents
1. [Features](#features)
2. [Prerequisites](#prerequisites)
3. [Installation](#installation)
4. [Running the Application](#running-the-application)
5. [Docker Setup](#docker-setup)
6. [Environment Variables](#environment-variables)
7. [Dependencies](#dependencies)
8. [Contributing](#contributing)
9. [License](#license)

---

## Features

- **Current Weather:** Displays the current weather, temperature, and conditions for searched cities.
- **7-Day Forecast:** Provides weather predictions for the next 7 days.
- **Responsive Design:** Optimized for both mobile and desktop.
- **Search Functionality:** Users can search for cities to get relevant weather data.

---

## Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- OpenWeatherMap API Key

---

## Installation

### 1. Clone the Repository

\`\`\`bash
git clone https://github.com/vbhv1016/React-weather-app
cd React-Weather-App
\`\`\`

### 2. Install Dependencies

Make sure to navigate to the project directory and install the necessary dependencies:

\`\`\`bash
npm install
\`\`\`

### 3. Set Up Environment Variables

Create a `.env` file in the root of the project and add your OpenWeatherMap API key:

\`\`\`
REACT_APP_WEATHER_API_KEY=your_openweather_api_key
\`\`\`

### 4. Running the Application

Start the development server using Vite:

\`\`\`bash
npm run dev
\`\`\`

The application will be running at:

\`\`\`
http://localhost:3000
\`\`\`

---

## Docker Setup

To run the application inside a Docker container, follow these steps:

### 1. Create a `Dockerfile`

\`\`\`Dockerfile
# Stage 1: Build the React app
FROM node:18-alpine AS build

WORKDIR /app

COPY package.json package-lock.json ./
RUN npm install

COPY . .
RUN npm run build

# Stage 2: Serve the app using a simple web server
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
\`\`\`

### 2. Build and Run the Docker Container

#### Step 1: Build the Docker image

\`\`\`bash
docker build -t react-weather-app .
\`\`\`

#### Step 2: Run the Docker container

\`\`\`bash
docker run -p 3000:80 react-weather-app
\`\`\`

The app will be available at:

\`\`\`
http://localhost:3000
\`\`\`

---

## Environment Variables

To use the OpenWeatherMap API, you need to set an environment variable for the API key. Create a `.env` file in the root of your project with the following content:

\`\`\`
REACT_APP_WEATHER_API_KEY=your_openweather_api_key
\`\`\`

---

## Dependencies

This project uses the following major dependencies:

- **React**: A JavaScript library for building user interfaces.
- **Vite**: A fast development build tool for modern web projects.
- **axios**: Promise-based HTTP client for the browser.
- **react-router-dom**: Routing library for React.
- **OpenWeatherMap API**: Provides weather data including forecasts and current conditions.

---

## Contributing

Feel free to open issues or submit pull requests if you'd like to contribute to this project.

---

## License

This project is licensed under the MIT License.
