---
title: "CSS or Javascript for what I want to do?"
date: 2011-01-26
forum: Programming Talk
---

### Post by rcayea on 2011-01-26
Which language do you think would be easiest to create the following: 

On my website, I have a line with the alphabet and when clicked on a viewer would read poems that would have started with that letter. 

I would like to make it so that when someone puts their cursor hovering over a letter they see a list of titles (instead of having to click on the letter to see the titles). 

Assuming I know (x)html, css and a bit of javascript (but could learn more if this is the answer to my question:

Would it be easier to accomplish what I want with css or javascript?

Please don't tell me it will be easier with css because I know that already, because I am willing to learn more javascript if that will, in the long run save time and be easier.

thanks,
Randy

---

### Post by worksofcraft on 2011-01-26
> **rcayea said:**
> Which language do you think would be easiest to create the following: 

On my website, I have a line with the alphabet and when clicked on a viewer would read poems that would have started with that letter. 

I would like to make it so that when someone puts their cursor hovering over a letter they see a list of titles (instead of having to click on the letter to see the titles). 

Assuming I know (x)html, css and a bit of javascript (but could learn more if this is the answer to my question:

Would it be easier to accomplish what I want with css or javascript?

Please don't tell me it will be easier with css because I know that already, because I am willing to learn more javascript if that will, in the long run save time and be easier.

thanks,
Randy

Well honestly... I would use server-side PhP to generate the lists of options but... that isn't one of your options :(

---

### Post by rcayea on 2011-01-26
> **worksofcraft said:**
> Well honestly... I would use server-side PhP to generate the lists of options but... that isn't one of your options :(

I could learn that too. :)

Would that be something that would take a while to learn or since I know html/css it would be a bit easier to learn?

---

### Post by worksofcraft on 2011-01-26
> **rcayea said:**
> I could learn that too. :)

Would that be something that would take a while to learn or since I know html/css it would be a bit easier to learn?

PhP is very similar to javascript except javascript runs on the client side... i.e. in the browser of the visitor who is viewing your page... while php runs on the server BEFORE dishing out the html.. so like it can find out what files you have on your server and create an html menu from them.

Your best way to learn it is to set up your own server on your own computer. Simply install a package called LAMP (Linux Apache PhP and MySQL) and you got yourself a bonafide web server... just don't tell all your friends to surf on over to your I.P. address as the default configuration is riddled with security compromises ;)

---

### Post by dileepm on 2011-01-27
Assuming you have worked on CSS and JavaScript to an extent. You can try jQuery. They have a real cool widgets to do the stuff you need.

---

### Post by rcayea on 2011-02-14
> **worksofcraft said:**
> PhP is very similar to javascript except javascript runs on the client side... i.e. in the browser of the visitor who is viewing your page... while php runs on the server BEFORE dishing out the html.. so like it can find out what files you have on your server and create an html menu from them.

Your best way to learn it is to set up your own server on your own computer. Simply install a package called LAMP (Linux Apache PhP and MySQL) and you got yourself a bonafide web server... just don't tell all your friends to surf on over to your I.P. address as the default configuration is riddled with security compromises ;)

Thanks for the tips. I have a home server. I guess I could try out my php skills on that.

---

### Post by llanitedave on 2011-02-14
You could also use Python, and keep the "P".  It's nicer than PHP, and a lot more versatile.

---

### Post by CptPicard on 2011-02-14
I would also suggest ditching PHP and looking into something more modern. Python and Ruby are both far more general-purpose programming languages, and have nice web frameworks (Rails, in particular), although this may not require the use of a whole framework...

The hover-functionality you're describing does require Javascript anyway, though.

---

### Post by WitchCraft on 2011-02-14
> **rcayea said:**
> 
I would like to make it so that when someone puts their cursor hovering over a letter they see a list of titles (instead of having to click on the letter to see the titles). 

Assuming I know (X)HTML, CSS and a bit of JavaScript (but could learn more if this is the answer to my question:

Would it be easier to accomplish what I want with CSS or JavaScript?

Please don't tell me it will be easier with CSS because I know that already, because I am willing to learn more JavaScript if that will, in the long run save time and be easier.

thanks,
Randy

The answer is really simple: 
You need both to do so.
(And PHP also, if you don't want to get bloody fingers from typing 26 letters + markup :-)) )

First, you make the list of letters in HTML (actually PHP, if you prefer a loop instead of 26 characters).

Then you have 2 possibilities:

For each letter, you store the titles information either in JavaScript arrays, or in a invisible tag, like the alt tag of images, or you use AJAX to retrieve the titles in JSON format (requires PHP/ASP.NET/Python), then you use JavaScript onmouseover to display the titles.

You need a div with a id, and then set the css property visibility initially to hidden, onmouseover to display, and manipulate the CSS position and visibility with JavaScript.

You will need JQuery to dynamically populate and depopulate the div, because IE is a big bitch when it comes to innerHTML...

---

### Post by rcayea on 2011-03-08
Thanks for the detailed information, WitchCraft. I actually am about 200 pages into learning Javascript and I actually know what arrays are :) and I am also becoming more familiar with php.

I will be referring to this info as I learn more.

thanks,
Randy 

If anyone wants to know, I would recommend the two books I am reading to help learn Javascript and PHP. 
1. Beginning Javascript by Wilton, McPeak. A Wrox title. 
2. I Hate PHP. A Beginners guide to PHP and MySQL.


> **WitchCraft said:**
> The answer is really simple: 
You need both to do so.
(And PHP also, if you don't want to get bloody fingers from typing 26 letters + markup :-)) )

First, you make the list of letters in HTML (actually PHP, if you prefer a loop instead of 26 characters).

Then you have 2 possibilities:

For each letter, you store the titles information either in JavaScript arrays, or in a invisible tag, like the alt tag of images, or you use AJAX to retrieve the titles in JSON format (requires PHP/ASP.NET/Python), then you use JavaScript onmouseover to display the titles.

You need a div with a id, and then set the css property visibility initially to hidden, onmouseover to display, and manipulate the CSS position and visibility with JavaScript.

You will need JQuery to dynamically populate and depopulate the div, because IE is a big bitch when it comes to innerHTML...

---

### Post by myrtle1908 on 2011-03-08
An excellent free JavaScript book/tutorial can be found @ [http://eloquentjavascript.net/](http://eloquentjavascript.net/).  Very good for noobs.  The author is excellent and has a great grasp of JS and all of its complexities.

Check out his winning winning JS1K entry---a JavaScript platform game that fits in 1024 bytes ... [http://marijnhaverbeke.nl/js1k/](http://marijnhaverbeke.nl/js1k/).  Good stuff.

Anyhoo, just another thing to check out and good luck with JS, it's a nice language.

---

