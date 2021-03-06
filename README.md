# Pager Parser
A Python script that parses regional 911 pager traffic in order to extract useful data such as call type, dispatched units/department, and incident location. The data is then stored in an external MongoDB database.

## Usage
This script was written in order to parse the POCSAG 1200 pager traffic utilized by fire departments in King County, WA. This script is only one part of a system that was built in order to accomplish that task.

I utilize an RTL2832 dongle in conjunction with SDR# in order to monitor pager traffic on 152.0075 MHz. That signal is then routed into PDW using Virtual Audio Cable (VAC) where the pages are decoded. Each time a decoded page makes it through all filters it is passed as an argument to this Python script.

![Decoding POCSAG 1200 Pager Traffic](http://s10.postimg.org/wutwaxdgp/pager.png)

## Implementation
The script stores all pertinent information in a MongoDB database. Addresses extracted from pages are geocoded using the Google Maps API and the corresponding lat/lng pair are also stored in the MongoDB document for each page.

In order to create a real time feed for users to view active 911 calls in the area, I decided to use Meteor for its reactive and real time capacities. The code for the site built upon Meteor can be found in another one of my repos. To view a live version of the site, [click here](http://trimed.co).