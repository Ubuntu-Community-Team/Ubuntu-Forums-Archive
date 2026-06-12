---
title: "How to burn movies?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by slammed87d21 on 2008-07-01
How do I burn movies that will play in DVD players with Linux Ubuntu? I switched from Windows XP and Vista, and I could burn movies with menus. I'm new to Ubuntu, but I can't find a program that will do menus, unless I'm just overlooking something. Oh, and if someone could tell me where to get the program, that would be awesome. Any help would be greatly appreciated. Thanks.

---

### Post by superprash2003 on 2008-07-01
try this application called k3b .. you could find it under synaptic.. system->administration->synaptic

---

### Post by tjwoosta on 2008-07-01
devede will burn movies awesome (much faster then vista)

it also does menus (not as fancy as vista though)

Edit: 
yea, vista burns dvds all in one long action, but with devede you first convert the movie to .iso (takes awile) then you burn the .iso to a disc (very quick)

---

### Post by Rhubarb on 2008-07-01
devede is an excellent program for this.
It allows you to create an iso file (an image of the video DVD) from any videos that you can play in Ubuntu.
You can download it in Synaptic, or open up a terminal and run this:
```
sudo aptitude install devede
```
Once installed you'll find it in Applications --> Sound & Video --> Devede.

Devede allows you to create a simple menu with several titles, different fonts / background image.  It's quite easy to learn too.
Once you've got the iso file from devede, you can burn it with Brasero / right click on the file and select "Burn to disc".

K3B is only good at burning CDs / DVDs, it won't let you author video DVDs.

---

### Post by nothingspecial on 2008-07-01
I find tovidgui works well. Get it here

[http://tovid.sourceforge.net/download/ubuntu/](http://tovid.sourceforge.net/download/ubuntu/)

Instructions here

[http://tovid.wikia.com/wiki/Using_the_tovid_GUI](http://tovid.wikia.com/wiki/Using_the_tovid_GUI)

---

### Post by bhadotia on 2008-07-01
You can also use tovid .Read these guides for the instructions on usage: 
1   [ http://ubuntuforums.org/showthread.php?t=183936]("http://ubuntuforums.org/showthread.php?t=183936")
2   [http://tovid.wikia.com/wiki/Using_the_tovid_GUI#Usage](http://tovid.wikia.com/wiki/Using_the_tovid_GUI#Usage)

---

### Post by bhadotia on 2008-07-01
> **nothingspecial said:**
> I find tovidgui works well. Get it here

[http://tovid.sourceforge.net/download/ubuntu/](http://tovid.sourceforge.net/download/ubuntu/)


nothingspecial , there is No need to go there . Just install it using synaptic or APT.
Open a terminal and do this:

[B]sudo apt-get install devede todiscgui tovidgui


[/B]

---

### Post by slammed87d21 on 2008-07-02
Ok, before I install anything, does anyone know which program will let you create chapters in movie files?

---

### Post by slammed87d21 on 2008-07-09
anyone?

---

### Post by tjwoosta on 2008-07-09
well..

im pretty sure you could create chapters in devede

but first you would need to split the video file into segments (one for each chapter)

ive never personally done it but i have heard avidmux will split videos

---

