---
title: "Trying to create a GDM theme"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-08-26
I want to make my owm GDM and if successful upload it to gnome-look.org
Follwing some instructions, to learn, I used a working configuration file, only changed the picture. it works, but when I want to take the screenshot, then I bump and roll. If I logout or restart, It does nothing on ctrl+alt+f2, but when I switch user, I can. I copied this command and is the one I write:
> echo chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth Display=:0.0 import -window root /tmp/Screenshot.png > /tmp/capture 

After numerous frustrated error because of typo's I get then this message:

> import: unable to open x server`'

Help... or an easier way to get the screenshot?

---

### Post by nicedude on 2008-08-26
Try doing this first for starters, download a Gnome theme or login that is already working from gnome looks or whatever and then unzip it and modify its picture and then re compress and see if it works as this will help you learn what formats & etc are used. Its how I made my CIA login screen which freaks people out real nice :-)

---

### Post by arashiko28 on 2008-08-26
I already did that, what i want is to take the screenshot. Now, trying to do so, I have lost my shutdown and restart buttons from the exit menu.

---

