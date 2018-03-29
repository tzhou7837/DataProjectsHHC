<!doctype html>
<html>
    <head>
        <title>Hospital Lists</title>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
        <link href="https://fonts.googleapis.com/css?family=Montserrat" rel="stylesheet">
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
        <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
    </head>
        <style>
            body {
                font: 20px Montserrat, sans-serif;
                line-height: 1.8;
                color: black;
            }
            p {font-size: 16px;}
                .margin {margin-bottom: 45px;}
            .bg-1 { 
                background-color: #0BBDFE;
                color: white;
            }
			.bg-2 { 
                background-color: #474e5d;
                color: white;
            }
            .bg-3 { 
                background-color: darkgray;
                color: black;
            }
		    .bg-4 { 
                background-color: #2f2f2f;
                color:white;
            }

            }
            .container-fluid {
                padding-top: 70px;
                padding-bottom: 70px;
            }
            .navbar {
                padding-top: 15px;
                padding-bottom: 15px;
                border: 0;
                border-radius: 0;
                margin-bottom: 0;
                font-size: 12px;
                letter-spacing: 5px;
            }
            .navbar-nav  li a:hover {
                color: #1abc9c !important;
            }
  
            .button {
                background-color: #4CAF50; /* Green */
                border: none;
                color:white;
                padding: 15px 32px;
                text-align: center;
                text-decoration: none;
                display: inline-block;
                font-size: 16px;
                margin: 4px 2px;
                opacity: 0.6;
                cursor: pointer;
                -webkit-transition-duration: 0.4s; /* Safari */
                transition-duration: 0.4s;
            }

            .button:hover {
                box-shadow: 0 12px 16px 0 rgba(0,0,0,0.24),0 17px 50px 0 rgba(0,0,0,0.19);
            }
        
                .button:hover {opacity: 1;}
        </style>

        <body>
            <body>

                <!-- Navbar -->
                <nav class="navbar navbar-default">
                  <div class="container">
                    <div class="navbar-header">
                      <button type="button" class="navbar-toggle" data-toggle="collapse" data-target="#myNavbar">
                      </button>
                      <a class="navbar-brand" href="#">NYC Hospitals Dataset</a>
                    </div>
                    <div class="collapse navbar-collapse" id="myNavbar">
                      <ul class="nav navbar-nav navbar-right">
                      </ul>
                    </div>
                  </div>
                </nav>
                
                <!-- First Container -->
                <div class="container-fluid bg-1 text-center">
                  <h4><br></h4>
				  <h1 class="margin">Hospitals in NYC</h1>      
                  <img src="http://2sei0v2s93y31n9ndy1lrzmh.wpengine.netdna-cdn.com/wp-content/uploads/2017/05/DTP_0367_8_9_cover_1_flat-1-1024x682.jpg" style="width:824px; height:570px;">
                  <h1><br></h1>
				</div>
                
                <div class="container-fluid bg-2 text-center">
                  <h4><br></h4>
				  <h1>Info</h1>
                  <h4>This is the “Health and Hospitals Corporation (HHC) Facilities” dataset. We incorporated it into a website for this project, <br> where the you can search up the hospital location by its ZIP code or its entire name (case sensitive). <br><br> Scroll down for the search bar and map.</h4>
				  <h1><br></h1>
				</div>

				<div class="container-fluid bg-3 text-center">    
                    <h2><br></h2>
					<h2 class="margin">Search Location</h2><br>
                    <div class="row">
 			    
            </body>
        </body>

        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
        <script>
            function myMap() {
                var mapProp = {
                    
                    center: new google.maps.LatLng(latitude, longitude),
                    zoom: 15,
                };
                var myLatLng = { lat: latitude, lng: longitude};
                var map = new google.maps.Map(document.getElementById("map"), mapProp);
                var marker = new google.maps.Marker({
                        position: myLatLng,
                        map: map,
                        title: 'Hello World!'
                    })
            }
        var build = "";
        var longitude;
        var latitude;
        function place() {
            var output = document.getElementById("output");
            var place = document.getElementById("place").value;
            $.getJSON("https://data.cityofnewyork.us/resource/w7a6-9xrz.json", function (data) {
                    for(var number = 0; number < data.length; number++){
                        if(place == data[number].facility_name){
                        latitude = parseFloat(data[number].latitude);
                        longitude = parseFloat(data[number].longitude);
                        build += "<div>";
                        build += "<div class='container'>"
                        build += "<div class='row'>"
                        build += "<div class='col-sm-4'>"
                        build += "<h3>" + data[number].facility_name + "</h3>"
                        build += "<p>" + data[number].facility_type + "</p>"
                        build += "<p>" + data[number].location_1_address + " " + data[number].location_1_city + " " + data[number].location_1_state + " " + data[number].location_1_zip + "</p>"
                        build += "<button onclick = \"myMap()\" class = \"button button\"> Show Map </button><br>"
                        build +="<br>";   
                        build += "</div>";                    
                    }
                    if(place == data[number].location_1_zip){
                        latitude = parseFloat(data[number].latitude);
                        longitude = parseFloat(data[number].longitude);
                        build += "<div>";
                        build += "<div class='container'>"
                        build += "<div class='row'>"
                        build += "<div class='col-sm-4'>"
                        build += "<h3>" + data[number].facility_name + "</h3>"
                        build += "<p>" + data[number].facility_type + "</p>"
                        build += "<p>" + data[number].location_1_address + " " + data[number].location_1_city + " " + data[number].location_1_state + " " + data[number].location_1_zip + "</p>"
                        build += "<button onclick = \"myMap()\" class = \"button button\"> Show Map </button><br>"
                        build +="<br>";   
                        build += "</div>";                    
                    }
                }       
                output.innerHTML = build;
            })
        } 
        </script>
        </head>
		
    <body>
        <div id="map" style="width:1582px;height:500px;"></div>
        <script src="https://maps.googleapis.com/maps/api/js?key=AIzaSyBC_D_je8Y6ZpWCoXBlLtVgu0wSaw5n2BI&callback=myMap"></script>

        <input id="place" placeholder="Search Zip or Hospital" type="text"><br>

        <button onclick = "place()" class="button button">
            Search
        </button>
		<h6>*The page may need to be reloaded to search for another location</h6>
		<h2><br></h2>
        <div id = "output"></div>
    </body>
	<body>
		<div class="container-fluid bg-4 text-center">
            <p><br></p>
			<h1 class="margin">JSON</h1>      
            <img src="json2.png">
			<h1><br></h1>
		</div>
	</body>
</html>
