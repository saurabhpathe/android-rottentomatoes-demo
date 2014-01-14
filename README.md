# RottenTomatoes BoxOffice Demo

This is an Android demo application for displaying the latest box office movies using the [RottenTomatoes API](http://www.rottentomatoes.com/). See the [RottenTomatoes Networking Tutorial](http://guides.thecodepath.com/android/RottenTomatoes-Networking-Tutorial) on our cliffnotes for a step-by-step tutorial.

![Screen](http://i.imgur.com/zQPzAxD.png)

## Overview

The app does the following:

1. Fetch the box office movies from the [Box Office Movie API](http://developer.rottentomatoes.com/docs/read/json/v10/Box_Office_Movies) in JSON format
2. Deserialize the JSON data for each of the movies into `BoxOfficeMovie` objects
3. Build an array of `BoxOfficeMovie` objects and create an `ArrayAdapter` for those movies
4. Define `getView` to define how to inflate a layout for each movie row and display each movie's data.
5. Attach the adapter for the movies to a ListView to display the data on screen

To achieve this, there are four different components in this app:

1. `RottenTomatoesClient` - Responsible for executing the API requests and retrieving the JSON
2. `BoxOfficeMovie` - Model object responsible for encapsulating the attributes for each individual movie
3. `BoxOfficeMoviesAdapter` - Responsible for mapping each `BoxOfficeMovie` to a particular view layout
4. `BoxOfficeActivity` - Responsible for fetching and deserializing the data and configuring the adapter

The app leverages the [Box Office Movies API](http://developer.rottentomatoes.com/docs/read/json/v10/Box_Office_Movies) which returns the following JSON response:

```json
{
  "movies": [{
    "id": "770687943",
    "title": "Harry Potter and the Deathly Hallows - Part 2",
    "year": 2011,
    "mpaa_rating": "PG-13",
    "runtime": 130,
    "critics_consensus": "Thrilling, powerfully acted, and visually dazzling...",
    "release_dates": {"theater": "2011-07-15"},
    "ratings": {
      "critics_rating": "Certified Fresh",
      "critics_score": 97,
      "audience_rating": "Upright",
      "audience_score": 93
    },
    "synopsis": "Harry Potter and the Deathly Hallows, is the final adventure...",
    "posters": {
      "thumbnail": "http://content8.flixster.com/movie/11/15/86/11158674_mob.jpg",
      "profile": "http://content8.flixster.com/movie/11/15/86/11158674_pro.jpg",
      "detailed": "http://content8.flixster.com/movie/11/15/86/11158674_det.jpg",
      "original": "http://content8.flixster.com/movie/11/15/86/11158674_ori.jpg"
    },
    "abridged_cast": [
      {
        "name": "Daniel Radcliffe",
        "characters": ["Harry Potter"]
      },
      {
        "name": "Rupert Grint",
        "characters": [
          "Ron Weasley",
          "Ron Wesley"
        ]
      }
    ]
  }, 
  {
     "id": "770687943",
     ...
  }]
}
```

See the [RottenTomatoes Networking Tutorial](http://guides.thecodepath.com/android/RottenTomatoes-Networking-Tutorial) on our cliffnotes for a step-by-step tutorial.

## Libraries

This app leverages two third-party libraries:

 * [Android AsyncHTTPClient](http://loopj.com/android-async-http/) - For asynchronous network requests
 * [Picasso](http://square.github.io/picasso/) - For remote image loading