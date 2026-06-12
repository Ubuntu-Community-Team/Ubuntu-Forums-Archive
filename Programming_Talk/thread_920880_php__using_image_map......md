---
title: "php  using image map....."
date: 2008-09-15
forum: Programming Talk
---

### Post by hockey97 on 2008-09-15
HI I am trying to get a image map to be used as a gui kinda.

It's a map of the U.S and when a person clicks on the state I want it to be submitted when clicked which will take off the map and load that state listings.

the problem I am facing is making the image map to use the post method to pass the value that was clicked to back to the page script which would then do a mysql query that would grab all posted items that were posted on that state and then the image map would be taken out and then I would display a table that has a list of items in that state.

I tried doing the nohref onclick="formname.submit() 

this would when clicked submit but the problem Is how can I submit a name or value.


I have the U.S map so I need a way where I can assign values to each state so when clicked it would pass the state and country name.

any ideas that would be the best way to do this???

do you think javascript is better for this problem???

I am still going to have to use php to do a database lookup and display the results.

---

### Post by drubin on 2008-09-15
This is more of a html/javascript issue. :) 
[http://www.htmlgoodies.com/tutorials/image_maps/article.php/3479741](http://www.htmlgoodies.com/tutorials/image_maps/article.php/3479741)
[http://www.w3schools.com/TAGS/tag_map.asp](http://www.w3schools.com/TAGS/tag_map.asp)

---

### Post by hockey97 on 2008-09-15
I know how to make the image map.

It's just how can I make it as a gui where the user just clicks the state they want see the lists of items in that state.

so when a person clicks the state I don't want to make a link where it would take them to a html page or something.

The problem I have is grabbing info from the client on what they click so I can grab that value meaning the state name and then generate a list from my database and take out the image map to display a table with that list.

---

### Post by drubin on 2008-09-15
onclick=" return loadDiv('texas')"...

Yes the only way to archive what you would like is with jscript and most likely ajax.

also try 
[HTML]<a href="#" onclick"jscriptFunction();return false;">..[/HTML]The return false to stop the page from reloading as you are going to want to show/hide the divs in your javascript

---

### Post by hockey97 on 2008-09-15
I have the image map in a form the form is using php.

I want to get a value from post method to input it in my php code.

so will onclick=" return loadDiv('texas')" be the only thing I need???

I want to know  if I just need the code above or would I need that and the return false and also  the onclick submit???

like for example in a form..

we would have <input type"text" name"Texas" value"Click here for Texas">

I want this effect kinda... the example is a input text that when I want to plug it in the php script I would use the $post["Texas"];

I want do somthing like this so when the person clicks a state I would be able with php grab what they user click and then input it in my script.

I just want them to click the image map which state they want and then the php script would grab it and know what state the person click with this info it would be plugged into a class that I used to search my database for all the listings that are in that state and then if I can in anyway take off the the image map so at the same place I can then display a table that would display the listings in the data base??

---

### Post by kjohansen on 2008-09-15
if you want the results returned from a php page without reloading the page:

1)you will need to use the ugly solution of seperate frames, one to hold the image map and the other to reload with the php page with a state id.

or

2)you will need to use ajax to return the php results to javascript and process the results with javascript

---

### Post by hockey97 on 2008-09-15
ok well I would like to do : 2)you will need to use ajax to return the php results to javascript and process the results with javascript

but I don't understand how I can proccess the results with a javascript...

I am using mysql as the database. I thought javascript is for the browser and was meant to be client-sided  so how would I go abouts doing this using ajax and javascript??

I have coded in javascript but been using the lib jquery so I am no expert on javascript.

---

### Post by drubin on 2008-09-16
> **hockey97 said:**
> I have coded in javascript but been using the lib jquery so I am no expert on javascript.

This is very hard to explain with out knowing what you have currently done. Could you please post your html/jscript. (It seems you have the php side covered).

Then we can work from what you already have. 

ps Frames in html != good...

---

### Post by Tony Flury on 2008-09-16
Another option is to have the image map call a simple piece of javascript - that function would take an argument that is the State name (or abbreviation). The javascript then sets a field in the form equal to the text argument it just received - and then calls submit - and since the field is filled in your php can do something sensible and fetch the data.

I am no javascript expert, and it has been a while since i have done any image maps, but that is what I would look to try to do.

---

### Post by hockey97 on 2008-09-16
ok I will show what I have so far....here is the code..:

```
<form name=\"marketstate\" action=\"Market.php\" method=\"POST\">
<IMG id=\"map\" SRC=\"/Artwork/USAMAPWHITE.gif\" USEMAP=\"#USAMAPWHITE\" WIDTH=598 HEIGHT=365 BORDER=0>
```
That was html that I have so far and yes I do have a image map which is long so I tought to not put it here but the java code I am running is:```

nohref onClick=\"marketstate.submit();\"
```

then I would run my php class;[php]$marketobjects= new Marketobjects;
$marketobjects->set('select','postings');[/php]

that is a class which would do a lookup in mysql database for the listings.

then in the class I have this[php] while($noOfPages > 0){
echo"<a href=\"$count\">$count</a>";}
$count++;[/php]

This would generate a link for every page needed. I have a limt of 20 postings allowed so if I have 21 posts then I would generate 1 link since it's 2 pages.

I haven't coded yet the image map events type like if the user clicks a state to take off the image map and put in a Table with  the list of posts and if more then 20 I would generate links that if clicked would send a value to php to grab the posts that is supposed to be displayed.

I don't want to make pages but want to use all this on one page.

---

