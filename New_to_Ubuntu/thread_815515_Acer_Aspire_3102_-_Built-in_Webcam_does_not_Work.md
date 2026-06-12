---
title: "Acer Aspire 3102 - Built-in Webcam does not Work"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by CSquared on 2008-06-01
Hijacking a thread slightly, but better that than repetition.  I'm having trouble with my webcam, but it's not going to be quite so easy with me.  Mine's built into my laptop, you see.  So there's no neat sticker on it telling me what model it is, and no amount of Googling has turned up the relevant information.

It's an Acer Aspire 3102WLMi, and if anyone knows what camera it is, I can probably go from there on my own.  But Easycam2 gives me the 'No camera' error.

Anyone got any ideas?

---

### Post by joshsmith on 2008-06-01
csquared, make a new thread. people will be better be able to help you

---

### Post by Sef on 2008-06-01
Do not hijack a thread.  Repetition is better.  Since you do not have many posts, I will forgo giving you an infraction this time, but not next time.

---

### Post by CSquared on 2008-06-01
Ah, OK.  Sorry, I misunderstood the 'search for threads like yours first' rule.  Won't happen again. ^_^

---

### Post by spiderbatdad on 2008-06-01
Can you run ```
lsusb
```see if it is a microdia.

---

### Post by hotweiss on 2008-06-01
Try installing the uvc drivers:

A) First we’ll need to install the files needed to build the driver by typing the following in Terminal:
> sudo apt-get install build-essential subversion linux-headers-`uname -r`

B) Now we will build the driver by typing the following commands in Terminal:
> cd /usr/src
and then
> sudo svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
and then
> cd trunk
and then
> sudo make
and then
> sudo cp -a uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/

C) Reboot, and your webcam will now be working.

---

### Post by joshsmith on 2008-06-01
@hotweiss
woah woah, we dont even know what webcam he has, should we really be advising checking out subversion code, and compiling stuff to put in /lib/modules straight away, 

and considering this is probably a new user....

tell me if im wrong

@csquared, of course, try it if you really feel like it

---

### Post by hotweiss on 2008-06-01
> **joshsmith said:**
> @hotweiss
woah woah, we dont even know what webcam he has, should we really be advising checking out subversion code, and compiling stuff to put in /lib/modules straight away, 

and considering this is probably a new user....

tell me if im wrong

@csquared, of course, try it if you really feel like it

Hey, it worked for me. Doesn't hurt to try. The UVC drivers are like a universal webcam antidote.

---

### Post by siddi on 2011-02-09
> **hotweiss said:**
> Try installing the uvc drivers:

A) First we’ll need to install the files needed to build the driver by typing the following in Terminal:


B) Now we will build the driver by typing the following commands in Terminal:

and then

and then

and then

and then


C) Reboot, and your webcam will now be working.


Hey.. sorry to butt into this thread... But i have an acer 5571 with the same trouble.. the webcam was working and then suddenly stopped with a 'gnome error' message..
i tried doing this but, in step 3 it says no repository found... can u guys help?

---

