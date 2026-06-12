---
title: "[SOLVED] Google Images Not Showing Images??"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by JBrehm on 2008-11-09
Hey all,

This is a google issue, but I'm hoping someone here can help anyway. When I search for something in google images, the results only show the description underneath the photo, as opposed to that plus the photo itself. Here's a screenshot of what I'm talking about:

[[IMG]http://img340.imageshack.us/img340/5359/screenshotobamagoogleimgy8.th.png[/IMG]](http://img340.imageshack.us/my.php?image=screenshotobamagoogleimgy8.png)[[IMG]http://img340.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

This JUST happened yesterday randomly as I was searching for victorian furniture. Before that it worked just fine. I've tried restarting my computer several times, reinstalling firefox (even though when I reinstalled it all of my setting were still there from before). Does anyone know what happened and what I can do to fix it?

Thanks!

Josh

---

### Post by steeleyuk on 2008-11-09
Have you got any extensions installed?

Also, have you tried creating a new profile. It could be a dodgy setting in there...

---

### Post by Crafty Kisses on 2008-11-09
Have you installed the codecs?
```
sudo apt-get install ubuntu-restricted-extras
```
When you're in Firefox you can also see what plugins you need and or are missing, by going into Firefox and typing this in the address bar:
```
about:plugins
```
You may want to try another browser and see if you get the same results.

---

### Post by brandoncolorado on 2008-11-09
> **Codename said:**
> Have you installed the codecs?
```
sudo apt-get install ubuntu-restricted-extras
```
When you're in Firefox you can also see what plugins you need and or are missing, by going into Firefox and typing this in the address bar:
```
about:plugins
```
You may want to try another browser and see if you get the same results.

The McCain 2008 - *Sore Loser Plugin* - does this to users to keep them from celebrating the Obama victory.

---

### Post by stephanvaningen on 2008-11-09
In Firefox: Check Edit -> Preferences -> Content -> Load images automatically -> Exceptions and remove 'google.com'

---

### Post by JBrehm on 2008-11-09
Bingo! The post from stephanvaningen solved it. Thanks!

---

