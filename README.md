# Manitoba Transit API Documentation Mockup  

The Transit API enables users to access comprehensive information about various transit options available throughout Manitoba. By providing details on modes of transportation, destinations, routes, and more, this API proves highly beneficial for several sectors, including the tourism industry, local transit applications, and map features.

### Endpoints:

The API offers the following endpoints. 

- `GET /api/route?start_point=value&end_point=value&mode=value`

##### Parameter:

* start_point (string) - The place where the route begins.(optional)
* end_point (string) - The final point of the route. (optional)
* mode (string) - The mode of transport. (optional)

### Resources:  

This API has the following resources:-  

#### 1. Route

The Route resource returns the specified route based on the provided parameters. It contains the following information:

```JSON
{
    "Mode": [{ "Name": "string","Time": "string"},....],
    "City": "string",
    "Start Point": "string",
    "End Point": "string",
    "Duration": "string",
    "Frequency": "string",
    "Stops": ["string_1","string_2",...]
}
```

In this response, Mode represents the method of travel (e.g., bus, train, car),City is where the transit is located in, Start_Point is the location where the transit originates, and End_Point is the final destination. Duration is the estimated time it takes to travel the route, Frequency indicates the interval between two consecutive trips, and Stops list the names of all stations along the way. 


### Example:

1. `GET /api/route?start_point=Winnipeg`
    * On a STATUS Code 200 OK the response is a list of all the routes with start point as winnipeg, one of the example of the route is given below:
    ```JSON
    {
        {
            "Mode": ["Train","Bus","Plane"],
            "City": "Winnipeg"
            "Start Point": "Winnipeg",
            "End Point": "Churchill",
            "Duration": "2 days",
            "Frequency": "Once a week",
            "Stops": ["The Pas","Pukatawagan","Thompson"]
        },....
    }
    ```
    * On a STATUS Code of 400 it returns ***INVALID_REQUEST***
    * On a STATUS Code of 404 it returns ***NO_ROUTE_FOUND***
    
2. `GET /api/route?end_point=Osborn Station`
    * On a STATUS Code of 200 it returns a list of all the destinations that end at Osborn station:
    ```JSON
    {   
        {
            "Mode": ["Bus","Train"],
            "City": "Winnipeg",
            "Start Point": "Chancellor Matheson",
            "End Point": "Osborn Station",
            "Duration": "15 mins",
            "Frequency": "Every 15 minutes",
            "Stops": ["Pembina@Bison Nort","SouthWest Transit Way@Chancellor Station","SouthWest Transit Way@Plaza"]
        },...
    }
    ```
    * On a STATUS Code of 400 it returns ***INVALID_REQUEST***
    * On a STATUS Code of 404 it returns ***NO_ROUTE_FOUND***
    
3.  `GET /api/route?mode=Bus`
    * On a STATUS Code of 200 it returns:
    ```JSON
        {
            {
                "Mode": ["Bus"],
                "City": "Winnipeg",
                "Start Point": "Chancellor Matheson",
                "End Point": "Osborn Station",
                "Duration": "15 mins",
                "Frequency": "Every 15 minutes",
                "Stops": ["Pembina@Bison Nort","SouthWest Transit Way@Chancellor Station","SouthWest Transit Way@Plaza"]
            },...
         }
    ```
    * On a STATUS Code of 400 it returns ***INVALID_REQUEST***
    * On a STATUS Code of 404 it returns ***NO_ROUTE_FOUND***
