---
title: "question about javascript function not defined."
date: 2010-06-09
forum: Programming Talk
---

### Post by hockey97 on 2010-06-09
Hi, I have a problem with my javascript code. I know the code is right.

The problem is I got 2 files. One first is runned which is called accounts.php and the other is apps.php 

so accounts.php is first runned. Now  in this php file I have the whole page layed out so that there is a application menu of nothing but images where when you click on one it loads in that app.

I am using jquery to use ajax. So when you click a image it would use jquery to use ajax to grab html code from apps.php  the apps.php has nothing but html and javascript code well php code that has if statements. The if statements grabs a value from a variable named app. if you click a image from the app menu in accounts.php it will send the app variable to apps.php. 

So I have html and javascript for each app in the apps.php

now here is the problem I made a javascript function and put it in the apps.php  file with the html code to be loaded into accounts.php

The problem I face is an error saying that the function isn't defined.

I move the javascript code around in apps.php and got no luck then decided to put it in accounts.php and got no luck.

So accounts.php is the main page and the apps.php is nothing but html and javascript code being loaded into accounts.php when the user clicks on a image in the apps menu in accounts.php

So my question is how to fix it? Is this a time load issue?

I would like to know or understand why this is happening.


I am loading in html and javascript to accounts.php from apps.php 

Does it matter when the javascript is loaded?

I tried this code in accounts.php and apps.php in many places and get the same error saying function isn't defined.

I ran into this error before working on another part of my website and was told once that I would need to put the javascript code after the html code that gets loaded from apps.php and the code should be in apps.php

I followed that persons advice and it worked but that was a different part of the website but similar code.

I tried that with this and it didn't work. 


I know that php code gets render first by the server and javascript is rendered after on the clients side.

I would like to know what I need to know about when loading javascript from another tile into the main file.

---

