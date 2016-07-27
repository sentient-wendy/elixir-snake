# Command Line Version of elixir-snake

## Description

Turning Github user arthurcolle's elixir-snake project into a command line tool 
using escript. See http://erlport.org/ for info about calling Python
code from Elixir, and http://ieftimov.com/writing-elixir-cli-apps for info
about making an Elixir app into a command line tool. 



Original readme from arthurcolle follows below.

Example repository to show what the equivalents of the Erlang/Python examples on [this page](http://erlport.org/docs/python.html) look like so that they work in an Elixir/Mix application.

Currently both functionalities work, as well as calling your own Python scripts from BEAM. 

## Usage
```
git clone http://github.com/arthurcolle/elixir-snake
cd elixir-snake
source activate <name of python virtualenv>
mix deps.get
mix compile
iex -S mix run
```
Other than having Python 2.7.9 installed (I used Anaconda) you should be good. Please feel free to submit pull requests, or even add cooler examples! 

**Example 1**: *Simple call to Python*

**```Snake.a```**

```
iex(3)> Snake.a

"2.7.9 |Continuum Analytics, Inc.| (default, Dec 15 2014, 10:37:34) \n[GCC 4.2.1 (Apple Inc. build 5577)]"
```

**Example 2**: *More complicated call to your own Python script*

**```Snake.b```**


```
iex(2)> Snake.b
What's your name?
Arthur Colle
"Arthur Colle is a boss"
```

**Example 3**: *Ouroboros - Elixir script that calls Python that calls Erlang (spawns processes)*

**```Snake.c```**

```
iex(1)> Snake.c
You just spawned 1000 processes in BEAM VM.
Here they are!

[#PID<0.101.0>, #PID<0.102.0>, #PID<0.103.0>, #PID<0.104.0>, #PID<0.105.0>,
 #PID<0.106.0>, #PID<0.107.0>, #PID<0.108.0>, #PID<0.109.0>, #PID<0.110.0>,
 #PID<0.111.0>, #PID<0.112.0>, #PID<0.113.0>, #PID<0.114.0>, #PID<0.115.0>,
 #PID<0.116.0>, #PID<0.117.0>, #PID<0.118.0>, #PID<0.119.0>, #PID<0.120.0>,
 #PID<0.121.0>, #PID<0.122.0>, #PID<0.123.0>, #PID<0.124.0>, #PID<0.125.0>,
 #PID<0.126.0>, #PID<0.127.0>, #PID<0.128.0>, #PID<0.129.0>, #PID<0.130.0>,
 #PID<0.131.0>, #PID<0.132.0>, #PID<0.133.0>, #PID<0.134.0>, #PID<0.135.0>,
 #PID<0.136.0>, #PID<0.137.0>, #PID<0.138.0>, #PID<0.139.0>, #PID<0.140.0>,
 #PID<0.141.0>, #PID<0.142.0>, #PID<0.143.0>, #PID<0.144.0>, #PID<0.145.0>,
 #PID<0.146.0>, #PID<0.147.0>, #PID<0.148.0>, #PID<0.149.0>, #PID<0.150.0>, ...]
```

**Example 4**: *(requires geocoder 1.4.0 on the py side)*


**```Snake.d```**

```
iex(1)> Snake.d
<[OK] Google - Geocode [New York, NY, USA]>
NY
{'status': 'OK', 'city': 'NY', 'confidence': 1, 'ok': True, 'encoding': 'utf-8', 'geometry': {'type': 'Point', 'coordinates': [-74.0059413, 40.7127837]}, 'country': 'US', 'provider': 'google', 'location': 'New York City', 'state': 'NY', 'bbox': {'northeast': [40.91525559999999, -73.70027209999999], 'southwest': [40.4913699, -74.25908989999999]}, 'address': 'New York, NY, USA', 'lat': 40.7127837, 'lng': -74.0059413, 'quality': u'locality', 'method': 'geocode', 'accuracy': 'APPROXIMATE'}
<[OK] Google - Geocode [New York, NY, USA]>
NY
{'status': 'OK', 'city': 'NY', 'confidence': 1, 'ok': True, 'encoding': 'utf-8', 'geometry': {'type': 'Point', 'coordinates': [-74.0059413, 40.7127837]}, 'country': 'US', 'provider': 'google', 'location': 'New York City', 'state': 'NY', 'bbox': {'northeast': [40.91525559999999, -73.70027209999999], 'southwest': [40.4913699, -74.25908989999999]}, 'address': 'New York, NY, USA', 'lat': 40.7127837, 'lng': -74.0059413, 'quality': u'locality', 'method': 'geocode', 'accuracy': 'APPROXIMATE'}
:undefined
```
