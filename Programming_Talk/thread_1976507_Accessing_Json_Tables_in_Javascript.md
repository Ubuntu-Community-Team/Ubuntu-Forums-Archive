---
title: "Accessing Json Tables in Javascript"
date: 2012-05-08
forum: Programming Talk
---

### Post by scott-ian on 2012-05-08
I am developing an app for mobile devices using Phonegap and jQuery Mobile.  I want to store a bunch of links in a json file, with names and categories.  This obviously is not exactly the code I am using but here is the general idea:
```

{
"links": [
{ "url":"http://www.example.com/example1" , "category":"examples" , "name":"Example Page One"},
{ "url":"http://www.example.com/example2" , "category":"examples" , "name":"Example Page Two"},
{ "url":"http://www.example.com/test1" , "category":"tests" , "name":"Test Page One"},
{ "url":"http://www.example.com/test2" , "category":"tests" , "name":"Test Page Two"}
]
}

``` 
This should be easy, but I have not been able to find out how to access the data in javascript!  I don't know to much javascript or json, and I found the documentation available was a bit confusing.  What I want to do is something I could manage in PHP with a MySQL database, but it must run client side.  I simply want to have a list of categories (showing each only once of course) and then list the content of the category as links.

---

### Post by myrtle1908 on 2012-05-09
JSON *is* JavaScript  


```
var data = {links:[{url:'http://www.google.com'}]};
alert(data); // object
alert(data.links); // object
alert(data.links instanceof Array); // true
alert(data.links.length); // 1
alert(data.links[0].url); // http://www.google.com
```


Use Firebug or Chrome Dev Tool to play around with JS.

---

### Post by scott-ian on 2012-05-09
I know json is a subset of Javascript, but I need to load from an external file.  Such as links.json.

---

### Post by scott-ian on 2012-05-10
Okay, I have working code:
```
var getdat = new XMLHttpRequest();
var daturl = "database.json";

getdat.open("GET",daturl,false);
getdat.setRequestHeader("User-Agent",navigator.userAgent);
getdat.send(null)
var database = eval('(' + getdat.responseText + ')');
document.write(database.links[0].url);
```But as I mentioned in the first post, I want to create a list (preferably alphabetized) of all the categories.  With my limited knowledge of programming, I would expect this involves a while loop, but exactly how to use it I do not know.

Edit: I worked out how to do it.
```
var categories = "0";
var category;
while (categories)
  {
  categories = database.links[categories]category;
  document.write(category);
  document.write("<br />");
  categories++;
  }
```

---

