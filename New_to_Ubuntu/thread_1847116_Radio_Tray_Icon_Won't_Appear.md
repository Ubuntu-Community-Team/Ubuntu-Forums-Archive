---
title: "Radio Tray Icon Won't Appear?"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by P-rench on 2011-09-20
I'm using a wubi install of Ubuntu 10.04. My issue is with the Radio Tray Icon. Usually I click and load radio tray from cairo dock and then another little icon appears in the right hand corner of the top panel where I can access Radio Tray and my radio stations. Recently though that little icon stopped appearing as you can see in the picture below. Instead a little space appears which I put a black circle around. I can still click on that space and access radio tray and my radio stations, its just really annoying that there is no icon present. Anyone have any idea's why this happened and how I can get the icon to appear again in the top panel??? I'm pretty lost as to what to do. 

[IMG]http://i167.photobucket.com/albums/u149/spiralnebula42o/TopPanel.png[/IMG] 


This is what the Radio Tray icon looks like for those who are unfamiliar. 
[IMG]http://radiotray.sourceforge.net/radio.png[/IMG]

---

### Post by P-rench on 2011-09-20
Surely there is a way to make an icon re-appear in the top panel?

---

### Post by ron999 on 2011-09-20
Hi
The "**config.xml**" file is stored in **/home/user/.local/share/radiotray** folder.
Maybe it's corrupted.
Rename it "**config.BAK**" then when you re-start RadioTray it will create a brand new config file.

---

### Post by P-rench on 2011-09-21
I can not seem to figure out how to change this config.xml file to config.BAK can someone help me out with this cause I dunno what I'm missing.

---

### Post by P-rench on 2011-09-21
Bump

---

### Post by P-rench on 2011-10-26
I figured this out. I had to be in root in order to change the .xml file. In order to do this I opened up a terminal and did sudo nautilus. Once the root directory was open I was able to navigate to the .xml file via what was originally posted by ron999: 

"The "config.xml" file is stored in /home/user/.local/share/radiotray folder.
 Maybe it's corrupted.
 Rename it "config.BAK" then when you re-start RadioTray it will create a brand new config file."

---

### Post by savoym on 2012-01-23
Thanks for your post.  I just loaded RadioTray a couple of weeks ago but could not understand why the icon had not come up in my tray.  That got it fixed. 

Thanks again.

---

