---
title: "Passing a javascript array to php...?"
date: 2008-06-08
forum: Programming Talk
---

### Post by lucas4ce on 2008-06-08
I'm trying to pass a javascript array, called say InputData to a php page, which will then do some calculations and produce a php array, say $Results.  $Results is then read back into a javascript array and then into a table on my website with the results.  This is all done without a refresh.

The bits I can do:
Read $Results back into a javascript array and populate the webpage table.  This works great thanks to some previous help form this forum.

The bit I can't seem to do:
Send the values of the javascript array Inputdata to a php page.  I've been trying to use something like the XMLHttpRequest function []("http://www.w3schools.com/php/php_ajax_suggest.asp") from W3Schools without success.  I don't get any html errors or anything like that, the webpage runs fine, just doesn't seem to pass the information to the php page.

Before we start ripping my code apart, and no doubt it needs it, is this the direction I should be going in order to pass information to the server?

Any help would be great!:confused:

---

### Post by lordnacho on 2008-06-08
I prefer using Prototype and it's Ajax calls:
[Prototype-Ajax]("http://www.prototypejs.org/learn/introduction-to-ajax")

Then to debug, use Firefox and install Firebug
[Firebug]("https://addons.mozilla.org/en-US/firefox/addon/1843")

Hope that helps a bit

---

### Post by lucas4ce on 2008-06-08
Thanks, unfortunately that confused me little more.

Just to add a bit of information, in my php page the 

$q=$_GET['q'];

code doesn't see to be retrieving a value from 'q', the webpage table cells are empty.  If I add the test line

$q="hello";

after this the webpage table is successfully updated with "hello" everywhere, so I know everything works.  Except for the javascript to php pass of course.

As I said earlier I'm trying to us ethe xmlHttpRequest() feature, infact I copied and pasted it from W3Schools.  Something isn't playing nicely.  

The URL in my browser doesn't change to myurl.php?q=variable, is remains as myurl.php, could this be an indication o fthe problem?

---

### Post by mike_g on 2008-06-08
First off: this is probably not the best way to go about it. But the way I did it in the past was to write the array content (seperated by a delimiter) to a hidden input field, then post it. When it reaches the php page then use the split() function to break it back down into an array. Its a dirty hack, but it worked for me.

---

### Post by lucas4ce on 2008-06-08
Thanks Mike,

I tried something similar usingthe exmaple here :

[http://www.boutell.com/newfaq/creating/scriptpass.html]("http://www.boutell.com/newfaq/creating/scriptpass.html")

but I ended up being redirected to the php page I was posting to and couldn't get back.  I'd like to pass the array without refreshing or leaving the page I'm on.

---

### Post by lucas4ce on 2008-06-08
Am i likely to be having problems because my web page and script pages are .php files, not .html and .js ?

---

### Post by mike_g on 2008-06-08
That shouldent be a problem. 

Out of curiosity, where is you javascript running? If its after the page has loaded then the only way you can get php to deal with the updated content is to serve a new page. 

You could maybe write the data to a cookie in JS, then grab the cookie in php:
[http://satya61229.blogspot.com/2007/05/php-and-javascript-cookie.html](http://satya61229.blogspot.com/2007/05/php-and-javascript-cookie.html)
(section 2)

---

### Post by lucas4ce on 2008-06-08
The cookie idea works a treat, but only with a page reload, which I'm trying to avoid.

Basically I enter some data into text fields, click an area of the page and an onclick event triggers a javascript function that calls the xmlHttpRequest() function to send data to my php page via the GET method.  But the string that comes back is empty.

I've set up an alert to tell me what url is being sent and the ?q=somedata is correctly added to the url.  

The php page deals with a $q variable correctly when I set that up manually.

As far as I know the only code between them is:

```
xmlhttp.open("GET",url,true);
xmlhttp.send(null);
```

both in the javascript, and:

```
$q=$_GET["q"];
```

in the php page.

I did set up the full W3Schools "suggest a name from the server" example on my system and it works perfectly so I know the server is set up ok.  

I'm stumped.

---

### Post by LoneWolfJack on 2008-06-08
If you want to send a JavaScript-Array to PHP, you have three options:
1. use a JS lib that serializes the array (ugh... libs...)
2. do it bit by bit, parameter by parameter (ugh, too)
3. serialize it yourself

After you have serialized the data, you can use a 1x1px transparent dummy graphic to send it to a PHP script through GET and put it into the user session if you feel like it.

---

### Post by lucas4ce on 2008-06-08
I'm having trouble getting a single string across at the moment, at some point the string seems to simply empty.

The transparent dummy graphic sounds impressive, how does that work then?

---

### Post by lordnacho on 2008-06-08
Just a note: xmlHttpRequest is the basis of Ajax.  No need for cookies or reloading.

If you need to debug, install Firebug for Firefox.  It will show in the Console, the ajax call(the link with url parameters), the results, how long it took.  I wouldn't be able to do ajax apps without it.

For the data, I'd use JSON or xml.  Both widely documented on the web.
JSON isn't as bulky as XML, but not as human readable

---

### Post by lucas4ce on 2008-06-08
Installed and tried it using Firefox, the Ajax request seems ok.

---

### Post by LoneWolfJack on 2008-06-08
> The transparent dummy graphic sounds impressive, how does that work then?

Use
```
<img id=myimg src="image.php">
```

Let image.php return a gif graphic that is 1x1 pixel and with the only color is set to alpha.

Once you have your serialized array, call
```
document.getElementById('myimg').src='image.php?mydata=foo';
```

The image will be reloaded and the data gets passed along the way and you can process it. If you need to do this multiple times with the same data, make sure to add a random string to the image call to avoid caching.

---

### Post by lucas4ce on 2008-06-08
The example I set up previously that does work looks something like this:

Html code with onkeyup event call to javascript function in linked .js script page.  The javascript then sends the HttpRequest to a php page and the php page echo's a resonse back to an html span.

My webpage setup is slightly different and I think this is where I'm having a problem.  

My javascripts exist in a .php file rather than a .js file so that I can include php scripts as required.  This php script file is currently included using require("phpscriptfile.php") in the head section of the webpage.

The javascript function that calls the HttpRequest is therefore loaded before the body of the webpage.  This function first calls the HttpRequest function if a change has occured, hopefully sending the some data to a php file, then in the same javascript function a ```
<?php require("calculations.php") ?>
``` section retrieves data back from the php calculation file, populating a javascript array and then calls another javascript function to update repopulate a table on the webpage.

Am I having problems sending the HttpRequest because it's already been sent?

In which case can anyone (if my explanation has be adequate) suggest a different way to set out my webpage, scripts, php etc?

---

### Post by lordnacho on 2008-06-08
Doesn't really matter where you store your JavaScript, what does matter, is how the source looks to the browser.

I'd do a body onload to call your ajax request.  This usually fires when the entire page is done loading.  So, if your responder needs to do something to the DOM(like access a textfield), then there's less of a chance it will f--- up :)

---

### Post by Verminox on 2008-06-09
I would suggest sending the data as a POST or GET array using XMLHttpRequest....

For example: 
```
var xhr = new XMLHttpRequest();
**var params = "myarray[]=one&myarray[]=two&myarray[]=three";**
var url = "get_data.php?"+params;
xhr.open("GET", url, true);

xhr.onreadystatechange = function() {//Call a function when the state changes.
	if(xhr.readyState == 4 && xhr.status == 200) {
		// Do something with xhr.responseText here
	}
}
xhr.send(null);
```

Notes:
1. You can create the 'params' string by looping through the array in JavaScript and appending each item to the string
2. In the PHP script that receives this request, $_GET['myarray'] will be an array. In the above example, $_GET['myarray'][0] will be "one".
3. To get the response to load back into the original JS array, make your target PHP script (as specified in the 'url' variable) echo the results in a serialized form (for example comma separated list of items) and use the JavaScript string methods to split the string at commas and build it into an array. 
4. You might need to [add some statements](http://en.wikipedia.org/wiki/XMLHttpRequest#History_and_support) before the first line to make sure the XMLHttpRequest function is available on browsers like IE, etc.

Edit: From your previous post I see you expect the URL in the browser to chagne but that won't happen. XMLHttpRequest silently requests another page and gets the response in the background without the user knowing (no page reload). However, you will need to make a new PHP script that accepts the request because your echo should not be a full fledged HTML page but should just be the response you need in your JS (for example a comma separated list of items for an array).

---

### Post by lucas4ce on 2008-06-09
Brilliant post!! Thank you, it's working great now.

And yes to the post above, I will need to send the httprequest in my onload() function, becuase I'm currently finding that I need to send it twice at the moment in order for the stateChanged function to kick in.

At least I guess that's why it's only working the second time, i.e. the first time I send the request from a buttons onclick event, the responseText is blank.

That's my next job.

Thanks to everyone!

---

