# weather
weather api pulled in for coders' safe house forecast.

This is a poc designed to reduce the rate limits for the call to the weather api. The php does this by checking to see when the last call to a city has happened, and if it only happened beyond X seconds ago, refresh the data.

Dealing with websites that have taken millions a hit per day, it is important to deal with rate limits and potential down town. 

This is version .7 for loose release. The following items need to still be addressed:

In the php:
* make sure that null (bad calls to api) is handled to fall back to current data.
* make the php script more flexible to resolve "any" api data that it pulls. Beyond city, it should flex to handle "people" or any key, making variable names more flexible is first task.


In the front-end
* make sure that if no good data is available there is a front-end fall back.
* Put a trigger in the front end (init or main.js) that if the php is not available to use a straight call the the api. This will mean passing the API url to the php (instead of embedded). 

The object for filterning the json (data_object.js) is flexible. See the yahoo_object.js for more details. The purpose of this object is to spin through the json nodes and make a unified simple javascript object to pull the json data from. It is a neatness issue that this lookup file resolves.

Deployment:
This has been designed to use a backend script (cache_feed.php) to help with keeping rate limits down. This is for deployment in high volume environments.

Copy the file in the git (clone or zip download) to your deployment folder.
Make sure to give you php script files the correct chmod. There is an assumption you know how to do this and you work with backends. If not, contact me and I'll help with a one liner (sturentzler@gmail.com).

weather_data.json is the current file name for saving pulled in feeds before sending to the front-end. There are comments in the cached_feed.php file to explain the timing of the saving of data. From a php deploy, make sure this file has the 755 permission for writing data.

Overview
index.html uses a call to the php file to either pull info from stored text or pull in new data.
The rest is front-end

Next Up
Connecting to react framework for data binding.


Note for Deploying
All files in this git, in its structure are required for releasing this poc.
