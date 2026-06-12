---
title: "php making ....."
date: 2007-07-28
forum: Programming Talk
---

### Post by hockey97 on 2007-07-28
Hi I am trying to make a website in .php, I  want to make  an area where I can make an interactive 3d model,

like for example, like computer let's say a labtop, I want to make a website that will have my 3d models of all the labtops I am selling, but I want the user able to rotate the 3d model around so they can see the over all look.

could that be done in php?? or is it only dueable in java???.

and using php is it possible to run a program from my server and have client's use it without the need to install the software??

how does websites that make online games able to make a visial graphic real-time screen in their webpage and have mouse and keyboard controls on it??

just courious.  

Thanks for your time.

---

### Post by bbzbryce on 2007-07-28
Looks like you're going to have your hands full. I'll start with the easy ones:

> and using php is it possible to run a program from my server and have client's use it without the need to install the software??

This is correct. The user just needs a web browser to interface with your web server. Apache (and other web servers) serves static files (html, images) and through the use of CGI or modules you can add dynamic content through php, perl, python, asp, and so on.

> how does websites that make online games able to make a visial graphic real-time screen in their webpage and have mouse and keyboard controls on it??

For this I can think of four options (though there may be more). In order to get keyboard and mouse input from the user in real time you can use javascript, flash, or a java applet. Microsoft's active x may also support that, but seeing as your on a linux form we'll just ignore the Microsoft side. Most web based games are done in flash so that is what I suggest you go with.

I think were you may be confused is the line between client side and server side. Javascript, flash, and java applets are all run from the client side and they can communicate with a server however they wish. And as before the server can use any language to process the input from the client.

For your 3D model it can be done using a set of images and javascript. I'm sure there are some tutorials online, but basically you just need to switch images as the user rotates. This of course isn't a real 3d model, but it serves it's purpose.

I hope this helped a bit.

---

### Post by hockey97 on 2007-07-29
so your saying for the 3d model thing, I could use my 3d modeling software to make animations and then code it with java in the webpage?

well I have seen microsoft when they released the xbox360 page they had a 3d model  and I think they used flash or java, and they had arrows left,right,up,down.  Now when I played with it, I saw and felt as it was a 3d model object that I could rotate it anyway I wanted, like I can ramdomly pick to rotate the object up,down,laft,right.

but are you saying that to make an animation or at least take the pic's of movement of the object and then in code make a logic script to figure out what picture need's to be displayed so it makes it seem it's a 3d object that a person can control and rotate it in any way?

---

### Post by bbzbryce on 2007-07-29
> **hockey97 said:**
> so your saying for the 3d model thing, I could use my 3d modeling software to make animations and then code it with java in the webpage?

well I have seen microsoft when they released the xbox360 page they had a 3d model  and I think they used flash or java, and they had arrows left,right,up,down.  Now when I played with it, I saw and felt as it was a 3d model object that I could rotate it anyway I wanted, like I can ramdomly pick to rotate the object up,down,laft,right.

but are you saying that to make an animation or at least take the pic's of movement of the object and then in code make a logic script to figure out what picture need's to be displayed so it makes it seem it's a 3d object that a person can control and rotate it in any way?

If you had enough images then yes you can make it appear as a 3d model. But as far as I know neither flash nor javascript support actual 3d rendering. Since java does support opengl I'm going to assuming you can accomplish opengl through a java applet but as with any of this it's not going to be simple to get working.

---

### Post by kknd on 2007-07-29
You can use VRML, Java, etc.

---

### Post by hockey97 on 2007-07-29
do you guy's think it's possible to code the 3d model and scripts in python, and then try to include it in a php page on my website???

becuse for apache I have python modules for it.

I know this can be done since I seen it on micrsofts xbox360 before it was coming out they had a 3d model,

it was some sort of app, like i needed to load it had a loading bar then apperas an 3d model of xbox 360 and had white arrows up,down,left,right, but the page main menu, was an app also, like they had arrows and could see tv screes with a pic on it and underneat a word that tells what it is then if you want it you click it,
it had info on different part's of xbox 360 and also the games that will come out with it those were different pages.

but the main site of xbox 360 you can scroll through those tv screens which it rotated like vista did, like the screens you can see them go rotate inside the page if that makes any sence.

it was impressive and I want such a thing for my products.

also I tired making a custom submit button, what lang would be good for making alot of custom stuff, just like a custom submit button.

---

### Post by bbzbryce on 2007-07-29
> **hockey97 said:**
> do you guy's think it's possible to code the 3d model and scripts in python, and then try to include it in a php page on my website???

Python is run on the server side, so you could code the 3d modeling stuff in Python but it wont do any good. If you have mod-python installed why then use php?

Could you find the link to what you are describing, or something similar, and then we can try to figure out the exact method needed.

---

