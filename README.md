# Weather App

## 1. Introduction

A web application designed to provide users with accurate and up-to-date weather information. This documentation will guide you through the various aspects of the application, including its features, technologies used, and code structure.

## 2. Technologies Used

The following technologies were employed to build the weather web application:

- **HTML**: Markup language for structuring the application's content.
- **CSS**: Stylesheet language for designing the application's layout and appearance.
- **JavaScript**: Programming language for implementing dynamic features and interactions.
- **Geolocation API**: Used to obtain the user's geographical location.
- **Weather API**: Utilized to fetch weather data based on either the user's location or a specified city.

## 3. Project Structure

The project is organized into several files and directories:

- **index.html**: The homepage, featuring geolocation access and weather display.
- **styles.css**: Stylesheet governing the overall look and feel of the application.
- **index.js**: JavaScript file containing the application's logic.

## 4. Features

### 4.1 Homepage (index.html)

#### User Location Access:

Users are prompted to grant access to their device's location upon visiting the homepage. The application employs the Geolocation API to obtain latitude and longitude coordinates.

```javascript
// Code snippet for geolocation access
function getLocation() {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(showPosition);
  } else {
    alert("Geolocation is not supported by this browser.");
  }
}
```
#### Weather Display:

Upon successful geolocation access, the application makes an asynchronous API call to retrieve weather data based on the user's coordinates. The UI is dynamically updated to showcase temperature, conditions, and other relevant information.
```javascript
// JavaScript function for fetching weather information from the OpenWeatherMap API
async function fetchSearchWeatherInfo(city) {
  loadingScreen.classList.add("active");
  userInfoContainer.classList.remove("active");
  grantAccessContainer.classList.remove("active");

  try {
    const response = await fetch(
      `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${API_KEY}&units=metric`
    );
    const data = await response.json();
    loadingScreen.classList.remove("active");
    userInfoContainer.classList.add("active");
    renderWeatherInfo(data);
  } catch (err) {
    //hW error handling
    alert("City not found");
  }
}
```
### 4.2 Search Page (search.html)

#### City Search:

Users can input a city name into the search box. The application processes this input, making an API call to fetch weather information for the specified city.
```javascript
// Code snippet for city search
async function fetchSearchWeatherInfo(city) {
  loadingScreen.classList.add("active");
  userInfoContainer.classList.remove("active");
  grantAccessContainer.classList.remove("active");

  try {
    const response = await fetch(
      `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${API_KEY}&units=metric`
    );
    const data = await response.json();
    loadingScreen.classList.remove("active");
    userInfoContainer.classList.add("active");
    renderWeatherInfo(data);
  } catch (err) {
    //hW error handling
    alert("City not found");
  }
}
```

## 5. Screenshots

#### User Location Access:
<img width="1280" alt="Screenshot 2023-11-14 at 1 59 54 PM" src="https://github.com/abhi-yo/weather-app/assets/112682702/a1932539-6610-48fa-95c9-0f57e50ae495">

#### Weather Display:
<img width="1280" alt="Screenshot 2023-11-14 at 2 00 31 PM" src="https://github.com/abhi-yo/weather-app/assets/112682702/04ef2baa-0e75-4ec7-b412-7b6cb3775bb1">

#### City Search:
<img width="1280" alt="Screenshot 2023-11-14 at 2 00 11 PM" src="https://github.com/abhi-yo/weather-app/assets/112682702/ae0894e9-e463-40b3-bd34-dd302b4d474e">
