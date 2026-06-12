---
title: "3D Desktop Swicher (neat Eye Candy)"
date: 2005-08-24
forum: Outdated Tutorials &amp; Tips
---

### Post by poofyhairguy on 2005-08-24
Like many people I love Eyecandy, and this one is pretty impressive. Many Ubuntuers already know about this, but I wanted there to be a how to for it.

Here is an easy trick to do that really impresses your friends and family (and you maybe).

Its a new way of switching desktops- in the 3rd dimension, and its pretty neat. To get it:

> sudo apt-get install 3ddesktop

Then after it installs, you have two options (I did both).

1. Use this program to make it so that the program runs when you mouse the moues out a corner (I picked bottom ones). Tell it to do a "custom action" and the command to get it to work is "3ddesk"

[http://www.ubuntuforums.org/showthread.php?t=27251&highlight=3ddesktop](http://www.ubuntuforums.org/showthread.php?t=27251&highlight=3ddesktop)

2. Make a launcher for it on your panel. Right click on the top panel. Select "custom application laucher". Put whatever name you want for it, but in the "command:" box put "3ddesk"

It actually works with Xcompgmr in Breezy, so the future is bright.

Have fun.

---

### Post by Tralobyte on 2005-08-24
Keep in mind if you do this that 3ddeskd, which is executed automatically when you run 3ddesk, takes up a fair amount of cpu power. A quick "ps aux" will tell you how much. It's a cool trick, though.

---

### Post by arnoct on 2005-08-24
Heh, I used to use it until I realized how slow it made my computer... But it's still a nifty effect :)

---

### Post by Ninnghizidha on 2005-08-24
I tried 3ddesktop several times, but it was a real resource-eater ... it will take screenshots of every workspace every 2 seconds, slowing down the system for this time at an cpu-usage of 100%.

Its a nice Trick for showing off the possibilities linux gives you, but it is not suitable for any usability-reasons.


kind reguards,
Ninnghizidha.

---

### Post by poofyhairguy on 2005-08-24
[QUOTE=Ninnghizidha]I tried 3ddesktop several times, but it was a real resource-eater ... it will take screenshots of every workspace every 2 seconds, slowing down the system for this time at an cpu-usage of 100%.

Its a nice Trick for showing off the possibilities linux gives you, but it is not suitable for any usability-reasons.


kind reguards,
Ninnghizidha.[/QUOTE]

Kinda. Runs like a charm on my P4 2.6GHZ machine. But I can see where its a CPU hog.

I started playing with it because my friend asked me "everybody in my classes makes fun of me for toying with Linux instead of using Windows, can you give me something to impress them?"

3ddesktop was the answer.

---

### Post by cutOff on 2005-08-25
We want screenshots  :smile:

---

### Post by Ninnghizidha on 2005-08-25
[img]http://666kb.com/i/10pihc3413ojk.png[/img]

---

### Post by Orunitia on 2005-08-25
That is nice. Too bad if I have it set to anything more than two desktops it takes a good minute just to get back to my screen. Damn laptop.

---

### Post by jeremytaylor on 2005-08-25
Hi,
if you're having problems with it making your machine really slow you can change the frequency at which it refreshes the images in /etc/3ddesktop/3ddesktop.conf (or something similar).

Also rather nice efffect if used in combination with brightside so it is activated as you move you mouse to a corner of the screen... even managed to impress a mac user with that  :) 

jeremy

---

### Post by pompeyjohn on 2006-05-07
does anyone have a groovy little icon they use which they are happy to share? :D

---

