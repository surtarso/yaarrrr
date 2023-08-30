# Project Documentation

Welcome to the documentation for the **yaarrrr** (Yet Another Await-Return Responsive React Root) app! This documentation provides an overview of the main files in the project.

## Index

1. [index.html](#publicindexhtml)
2. [index.js](#srcindexjs)
3. [MovieCard.jsx](#srcmoviecardjsx)
4. [App.js](#srcappjs)
5. [Conclusion](#conclusion)
6. [Best Practices](#best-practices)
7. [OMDP API Disclaimer](#disclaimer)

## File Details

### public/index.html

The [public/index.html](public/index.html) file serves as the main HTML template for the React app. It acts as the entry point for rendering the React components into the browser.

Here's a detailed line-by-line documentation explaining the HTML code:

```html
<!DOCTYPE html>
```
- This declaration specifies the type of document being used, indicating that the content is an HTML document.

```html
<html lang="en">
```
- The opening tag of the `<html>` element, which represents the root of an HTML document.
- The `lang` attribute specifies the language of the document, in this case, English ("en").

```html
<head>
```
- The opening tag of the `<head>` element, which contains metadata and other information about the document.

```html
<link rel="shortcut icon" href="#">
```
- This line defines a link to the shortcut icon (favicon) for the webpage.
- The `rel` attribute specifies the relationship between the current document and the linked resource.
- The `href` attribute specifies the location of the linked resource, in this case, `#` which represents a placeholder or no actual resource.

```html
<meta charset="utf-8" />
```
- This line sets the character encoding for the document to UTF-8.
- UTF-8 is a widely used character encoding that supports a wide range of characters from different languages and scripts.

```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```
- This line defines a viewport meta tag that controls how the webpage is displayed on different devices and screen sizes.
- The `width=device-width` ensures that the width of the viewport matches the device's width.
- The `initial-scale=1` sets the initial zoom level to 1, which means the webpage is displayed at 100% zoom.

```html
<title>YAARRRR!</title>
```
- This line sets the title of the webpage, which is displayed in the browser's title bar or tab.

```html
</head>
```
- The closing tag of the `<head>` element, which encapsulates the metadata and other information in the document's header.

```html
<body>
```
- The opening tag of the `<body>` element, which contains the visible content of the webpage.

```html
<noscript>You need to enable JavaScript to run this app.</noscript>
```
- The `<noscript>` element provides content that is displayed when JavaScript is not enabled in the browser.
- In this case, it informs users that JavaScript needs to be enabled to use the app.

```html
<div id="root"></div>
```
- This line creates an empty `<div>` element with the `id` attribute set to "root."
- This empty `<div>` is where the React application's components will be dynamically rendered.

```html
</body>
```
- The closing tag of the `<body>` element, which marks the end of the visible content of the webpage.

```html
</html>
```
- The closing tag of the `<html>` element, which marks the end of the HTML document.

This HTML code is a typical structure for a web page and provides the basic setup for a React application to be rendered within the specified `<div id="root">` element. The metadata and elements in the `<head>` section control various aspects of how the webpage is displayed and behaves.

[Back to top](#index)

### src/index.js

The [src/index.js](src/index.js) file is the entry point for the React application. It initializes the ReactDOM rendering and sets up the root component for the app.

Here's a detailed line-by-line documentation explaining the JavaScript code:

```javascript
import React from 'react';
```
- This line imports the `React` object from the 'react' package.
- The `React` object is essential for creating and working with React components.

```javascript
import ReactDOM from 'react-dom/client';
```
- This line imports the `ReactDOM` object from the 'react-dom/client' package.
- `ReactDOM` is used to render React components into the DOM (Document Object Model).

```javascript
import App from './App';
```
- This line imports the `App` component from the './App' file.
- The `App` component is likely the main component of the application that will be rendered.

```javascript
const root = ReactDOM.createRoot(document.getElementById('root'));
```
- This line creates a React root using the `createRoot` method from `ReactDOM`.
- The `createRoot` method is used to create a root for a concurrent mode tree (experimental feature as of my knowledge cutoff in September 2021).
- `document.getElementById('root')` retrieves the DOM element with the id 'root' where the React application will be rendered.
- The `root` constant now holds a reference to the root element.

```javascript
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```
- This block of code renders the `App` component into the designated root using the previously created React root.
- `<React.StrictMode>` is a wrapper that activates strict mode checks for the rendered component and its descendants. It's used to highlight potential problems in the application during development.
- `<App />` is the usage of the `App` component. It is being rendered within the `React.StrictMode` wrapper.
- The `root.render(...)` function call effectively renders the `App` component into the DOM, starting the React application.

Overall, this code imports necessary dependencies, creates a React root, and renders the main `App` component within a `StrictMode` wrapper. This is the entry point for your React application, where the rendering process begins.

[Back to top](#index)

### src/MovieCard.jsx

The [src/MovieCard.jsx](src/MovieCard.jsx) file contains the component responsible for rendering individual movie cards. This component is used to display movie information within the app.

Here's a detailed line-by-line documentation explaining the JSX code for the `MovieCard` component in React:

```jsx
import React from 'react';
```
- This line imports the `React` object from the 'react' package.
- The `React` object is necessary for creating and working with React components.

```jsx
const MovieCard = ({ movie: { imdbID, Year, Poster, Title, Type } }) => {
```
- This declares a functional component named `MovieCard` that takes a destructured prop object.
- The prop object is destructured to extract properties like `imdbID`, `Year`, `Poster`, `Title`, and `Type` from the `movie` prop.

```jsx
const IMG_NOTFOUND = "https://via.placeholder.com/248x368/000000/00FFFF/?text=NO+POSTER+FOUND";
```
- This line defines a constant `IMG_NOTFOUND` with a URL for a placeholder image when no movie poster is available.

```jsx
const TARGET_URL = "https://thepiratebay.org/search.php?q=";
const IMDB_URL = "https://www.imdb.com/find?q=";
```
- These lines define constants `TARGET_URL` and `IMDB_URL` with URLs for The Pirate Bay and IMDb search pages, respectively.

```jsx
const openInNewTab = url => {
  window.open(url, '_blank', 'noopener,noreferrer');
};
```
- This declares a function `openInNewTab` that takes a URL and opens it in a new browser tab.
- The `'noopener,noreferrer'` attributes are security measures to prevent the newly opened tab from accessing the parent window.

```jsx
return (
  <div className="movie" key={imdbID} >
```
- This line starts the return of the JSX content. The `div` element represents the entire movie card.
- `className` assigns the CSS class `movie` to style the card.
- `key={imdbID}` provides a unique identifier for React to efficiently manage and update these components.

```jsx
<div>
  <p>{Year}</p>
</div>
```
- This `div` contains the year information of the movie.
- The `p` element displays the `Year` property.

```jsx
<div>
  <img
    src={Poster !== "N/A" ? Poster : IMG_NOTFOUND}
    alt={Title}
    onClick={() => openInNewTab(TARGET_URL + Title.replace(/\s/g,'+'))}
  />
</div>
```
- This `div` contains the movie poster image.
- The `img` element's `src` attribute uses the `Poster` property to display the movie poster if available; otherwise, it displays the placeholder.
- The `alt` attribute is set to the `Title` property for accessibility.
- An `onClick` event is attached to the image. When clicked, it opens a new tab with the URL constructed from `TARGET_URL` and the modified `Title`.

```jsx
<div>
  <span>{Type}</span>
  <h3>{Title}</h3>
  <button className="imdb-button" onClick={() => openInNewTab(IMDB_URL + imdbID)}>IMDB</button>
</div>
```
- This `div` contains the bottom section of the movie card.
- The `span` element displays the `Type` property.
- The `h3` element displays the `Title` property.
- A button with the CSS class `imdb-button` is created. When clicked, it opens a new tab with the URL constructed from `IMDB_URL` and the `imdbID`.

```jsx
</div>
```
- This line closes the outermost `div`, ending the JSX content of the `MovieCard` component.

```jsx
};

export default MovieCard;
```
- This block concludes the `MovieCard` component's code.
- The `export default` statement exports the `MovieCard` component for use in other parts of the application.

This `MovieCard` component represents a card displaying movie information, including the movie poster, year, title, type, and buttons to open related URLs in new tabs.

[Back to top](#index)

### src/App.js

The [src/App.js](src/App.js) file is the main component of the application. It contains the overall structure of the app, including the search functionality and the rendering of movie cards.

Here's a detailed line-by-line documentation explaining the JavaScript code for the `App` component in React:

```javascript
import React, { useState, useEffect } from "react";
import MovieCard from "./MovieCard";
import SearchIcon from "./pirate.svg";
import "./App.css";
```
- These lines import necessary modules and components for the `App` component.
- `React` is imported along with `useState` and `useEffect` hooks for state management and side effects.
- The `MovieCard` component is imported for rendering individual movie cards.
- `SearchIcon` is imported as the source for an image representing a search icon.
- The `App.css` stylesheet is imported for styling the `App` component.

```javascript
const API_URL = "http://www.omdbapi.com?apikey=b6003d8a";
```
- This line defines the API URL to fetch movie data from the OMDB API. The `apikey` parameter is provided for authentication.

```javascript
const App = () => {
  const [searchTerm, setSearchTerm] = useState("");
  const [movies, setMovies] = useState([]);

  //on load
  useEffect(() => {
    searchMovies("pirate");
  }, []); //empty array -> run once
```
- This defines the `App` component using a functional component approach.
- `useState` is used to declare two state variables: `searchTerm` and `movies`.
- The `searchTerm` state stores the current search query.
- The `movies` state stores an array of movie data fetched from the API.
- The `useEffect` hook is used to perform an initial search for movies with the term "pirate" when the component loads (runs once due to an empty dependency array).

```javascript
const searchMovies = async (title) => {
  const response = await fetch(`${API_URL}&s=${title}`);
  const data = await response.json();

  setMovies(data.Search);
};
```
- This defines an asynchronous function `searchMovies` that fetches movie data from the OMDB API based on a given `title`.
- The `fetch` function is used to make an API request.
- The response data is parsed using `response.json()` and then used to update the `movies` state with the array of search results.

```javascript
const checkForEnter = (k) => {
  if (k.key === "Enter") {
    searchMovies(searchTerm);
  }
};
```
- This function, `checkForEnter`, is used to check if the Enter key was pressed.
- If the Enter key is pressed (`key === "Enter"`), it triggers a search for movies using the current `searchTerm`.

```javascript
return (
  <div className="app">
    {/* HEADER */}
    <h1>&#9760; YAARRRR &#9760;</h1>
    <h2>Yet Another Await-Return Responsive React Root</h2>

    <div className="search">
      {/* search field */}
      <input
        value={searchTerm}
        onChange={(e) => setSearchTerm(e.target.value)}
        placeholder="Search for movies"
        onKeyDown={checkForEnter} // add check with ENTER
      />
      {/* search icon */}
      <img
        src={SearchIcon}
        alt="search PirateBay"
        onClick={() => searchMovies(searchTerm)}
      />
    </div>

    {/* BODY */}
    {movies?.length > 0 ? (
      <div className="container">
        {movies.map((movie) => (
          <MovieCard movie={movie} key={movie.imdbID} />
        ))}
      </div>
    ) : (
      <div className="empty">
        <h2>No movies found.</h2>
      </div>
    )}
  </div>
);
```
- This block contains the JSX that renders the `App` component.
- The component is wrapped in a `div` with the class name `app`.

- The header section contains an h1 element with a pirate ship emoji and the title "YAARRRR," and an h2 element describing the app.

- The search section contains a `div` with the class name `search`:
  - An `input` element is used for entering search terms. Its value is controlled by the `searchTerm` state. The `onChange` event updates the `searchTerm` state as the user types.
  - The `onKeyDown` event calls the `checkForEnter` function when a key is pressed. If the Enter key is pressed, it triggers a search using the `searchMovies` function.
  - An `img` element displays the search icon. When clicked, it triggers a search using the `searchMovies` function.

- The body section displays movie cards based on the `movies` state:
  - If `movies` has a length greater than 0, a container div is created, and each movie in the `movies` array is mapped to a `MovieCard` component using the `map` function.
  - The `key` attribute is added to each `MovieCard` component to ensure React can efficiently manage and update these components.
  - If `movies` is empty, a message is displayed indicating that no movies were found.

```javascript
};

export default App;
```
- The closing braces indicate the end of the `App` component code.
- The `export default` statement exports the `App` component for use in other parts of the application.

This `App` component represents the main user interface of the application, including a search bar, search icon, and a list of movie cards. It interacts with the OMDB API to fetch and display movie data.

[Back to top](#index)

## Conclusion

**yaarrrr** (Yet Another Await-Return Responsive React Root) is a React.js application that allows users to search for movies by title, retrieve information from the OMDB API, and conveniently navigate to IMDB and TPB pages. This application provides a user-friendly interface for searching and discovering movies while demonstrating key concepts in React development.

## Best Practices

While developing **yaarrrr**, the following best practices have been incorporated into the codebase:

1. **Componentization:** The code is organized into modular components, enhancing code reusability and maintainability.

2. **State Management:** The use of `useState` and `useEffect` hooks for state management ensures efficient and effective data handling.

3. **Responsive Design:** The layout and design elements are structured to be responsive, providing a seamless experience across various devices and screen sizes.

4. **Event Handling:** Event handling is well-structured, allowing for user interactions like clicking on movie posters and buttons.

5. **Code Comments:** The code is supplemented with meaningful comments that explain the purpose and functionality of various sections, enhancing code readability.

6. **API Integration:** The application fetches movie data from the OMDB API, demonstrating API integration and asynchronous operations.

## Disclaimer

Please note that the provided OMDB API key in the code (`API_URL = "http://www.omdbapi.com?apikey=b6003d8a"`) is a personal key and should be replaced with your own OMDB API key. You can obtain your API key by signing up on the [OMDB website](http://www.omdbapi.com/apikey.aspx). Using personal API keys is essential for security and rate limiting reasons.

When you obtain your API key, make sure to replace the existing key in the code to avoid any unauthorized usage and to ensure that your application works as intended.

Remember that API keys and sensitive information should not be hard-coded in your codebase when sharing your code publicly or deploying it to production environments. Consider using environment variables or secure configuration management for such sensitive information.

Feel free to customize and enhance **yaarrrr** to suit your needs and requirements.

[Back to top](#index)
