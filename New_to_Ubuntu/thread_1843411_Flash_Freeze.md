---
title: "Flash Freeze"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by (Nes) on 2011-09-13
Okay this time it's not a sudo problem :D

I'm trying to install flash player 10 in wine, I did it once before but I had to set up wine again (didn't do it correctly the first time), and now every time I try to start up the installer it freezes right at the beginning.

Any ideas? 

I have tried downloading new copies to no avail. 

I'm running the install command from a terminal (I've tried from inside wine as well) and it's giving me the xrender alphablend error but I don't really understand how to fix that or if it's even related.

---

### Post by gandaran on 2011-09-13
> **(Nes) said:**
> Okay this time it's not a sudo problem :D

I'm trying to install flash player 10 in wine, I did it once before but I had to set up wine again (didn't do it correctly the first time), and now every time I try to start up the installer it freezes right at the beginning.

Any ideas? 

I have tried downloading new copies to no avail. 

I'm running the install command from a terminal (I've tried from inside wine as well) and it's giving me the xrender alphablend error but I don't really understand how to fix that or if it's even related.
installing the flash in wine is easy, download the windows .exe flash, mark the allow executing program in permissions then just double click to run the installer.
just a question, why do you want flash installed in wine? flash in wine will only work on windows browsers installed in wine too.

---

### Post by haqking on 2011-09-13
> **gandaran said:**
> installing the flash in wine is easy, download the windows .exe flash, mark the allow executing program in permissions then just double click to run the installer.
just a question, why do you want flash installed in wine? flash in wine will only work on windows browsers installed in wine too.

+1

If you think you need flash for your Linux system and that you do so by installing Flash through wine then thats not what you do.

if you want Flash in your linux system i suggest [Flash-Aid ]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/")which will install into firefox and be used across browsers on the system

---

### Post by (Nes) on 2011-09-13
I need flash in wine so I can run Leap Frog Connect for my son's Tag reader. 

I did the double click... thing first, and had the same problem. The installer is freezing, it worked yesterday before I had to change the wine install :S

---

### Post by Johnb0y on 2011-09-13
> **haqking said:**
> +1

If you think you need flash for your Linux system and that you do so by installing Flash through wine then thats not what you do.

if you want Flash in your linux system i suggest [Flash-Aid ]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/")which will install into firefox and be used across browsers on the system

+1 i did this... worked perfect!

---

### Post by (Nes) on 2011-09-13
Well I got it to work by installing a new prefix. Anyone have a really good intro to wine? #-o

Here's hoping tag can get through this time...

---

### Post by haqking on 2011-09-13
> **(Nes) said:**
> Well I got it to work by installing a new prefix. Anyone have a really good intro to wine? #-o

Here's hoping tag can get through this time...


[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

