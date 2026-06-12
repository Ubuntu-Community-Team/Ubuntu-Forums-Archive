---
title: "Need help to understand ajax."
date: 2010-03-17
forum: Programming Talk
---

### Post by hockey97 on 2010-03-17
Hi, I am using jquery ajax.  I am new to ajax. 

I know what it stand for and it's nothing totally new.

Right now for my website I want a input type image that onced clicked to run a javascript function that then uses ajax to use a php script to grab data from the database and inject it into a div.

on the jquery api area here: [http://api.jquery.com/jQuery.post/](http://api.jquery.com/jQuery.post/)

they give examples on how to use the .post function.

```
Example: Alert out the results from requesting test.php with an additional payload of data (HTML or XML, depending on what was returned).

$.post("test.php", { name: "John", time: "2pm" },
   function(data){
     alert("Data Loaded: " + data);
   });


```

I am confused on the example used above. What is the data variable?

what mine so far is doing is just redirecting me to the php file. 

I don't want to load a new page. just grab the data from the database and display it on the website.

---

### Post by CyberJack on 2010-03-17
The data variable contains the result from the post.

To explain the example:
$.post makes a post request to "test.php" and posts the variable "name" and "time".
test.php then does something which generates some output.
The output will be placed in the data variable and alerted.

Depending on the data you want to use you could use this in 2 ways:
- generate full html code (in test.php)
- use json to transfer only data (no html) and generate the html in javascript.

In both cases you can overwrite a complete div like so:
[PHP]
$("#divid").html( data );
[/PHP]
of append the data to a div like so:
[PHP]
$("#divid").append( data );
[/PHP]

---

### Post by era86 on 2010-03-17
The last argument supplied to jQuery.post() is a callback function that will handle the response after the request is complete.  In this case, they print out the response from test.php as an alert.

If you want to push the data (which is assumed to be HTML in your case) to a div, you can follow CyberJack's example.

---

### Post by hockey97 on 2010-03-18
ok, so this is what I understand so far don't know if it's right but what I am thinking right now.

the .post  first arguement is the url of the php file. Then followed by the the variables being passed to the php file as inputs to the file something similar to forms in php how they pass the post variables. Then after that is the code that passes a variable back to the javascript.

So the data variable is made in the php file and gets sent back to the javascript. 

My question is that is the output only in the variable data like is data the default name for the result variable from the request?

I understand the last part is a callback function.



here is what I am doing. I am making a navigation menu that  once you click the image icon which is a html input type image. It will run a javascript function which will use ajax to load in data in a div for that user by grabing the data from the mysql database. 

So my question would be is the data variable a default variable or are these made up names... like could I instead of using data as the variable name use simple  or load_app.

or is this data variable created in the php file and holds the results of the query of the database in this variable and passed to the javascript?

---

### Post by era86 on 2010-03-18
*data* is simply the response from the server.  You do any sort of seraialization and preparation (JSON, XML, HTML, etc.) on the server side.

I think to better understand AJAX, you might benefit from reading here: [http://www.interaktonline.com/Support/Articles/Details/AJAX:+Asynchronously+Moving+Forward-How+does+AJAX+work%3F.html?id_art=36&id_asc=308](http://www.interaktonline.com/Support/Articles/Details/AJAX:+Asynchronously+Moving+Forward-How+does+AJAX+work%3F.html?id_art=36&id_asc=308)

Or the VERY beginning of this article: [http://www.noupe.com/ajax/how-ajax-works.html](http://www.noupe.com/ajax/how-ajax-works.html)

> 
Here is how the usual AJAX script goes:

    * Some action triggers the event, like the user clicking a button.
    * The AJAX call fires, and sends a request to a server-side script, using XML
    * The server-side script (PHP, ASP, or whatever) takes the input from JavaScript, can access the database if it needs to, and processes the data.
    * Using XML again, the script sends the data back to the original client-side page that made the request
    * A second JavaScript function, called a callback function,catches the data, and updates the web page


---

