---
title: "split screen probelm"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by elvatonadam on 2008-04-29
I'm trying to install xubuntu on an old P3 1.0 GHz 192 RAM Dell Inspiron 8000.  Unfortunately, I keep getting a wierd split screen thing where at certain points, i can't see the mouse, and certain points i see two of them... it looks like this:[IMG]http://home.comcast.net/~elvatonadam/0429082216.jpg[/IMG]

Is this the ATI driver situation I keep hearing about, and if so, is there an easy fix to it?... I can't seem to find it in the threads...

---

### Post by overdrank on 2008-04-29
Hi and welcome, what is the model of the ATI graphics card? There has been some issues with the ATI cards in Hardy. There is some help for correcting the issue. Have you tried changing the resolution. You can find the model of the graphics card with the command ```
lspci
``` in the terminal located under applications.

---

### Post by elvatonadam on 2008-04-30
It's an ATI Rage Mobility M4 AGP... works fine in safe graphics mode, but is obviously much smaller

---

### Post by Techpenguin on 2008-06-09
Yeah, I had this problem too, I then attempted to get rid of it by uninstalling Xubuntu and installing Ubuntu, didn't work. How am I supposed to fix this?

---

### Post by abn91c on 2008-06-09
change the monitor frequency to 60hz

---

### Post by Techpenguin on 2008-06-09
Thanks, but, uh... how? (sorry to be a n00b)

---

### Post by abn91c on 2008-06-09
i use kubuntu, but i think its under places, administration, screen resolution

---

### Post by Techpenguin on 2008-06-09
For some reason, this isn't working. I changed the resolution and the refresh rate but it still won't change.

P.S. I am installing this on a Dell Inspiron 5000e with an ATI card

---

### Post by abn91c on 2008-06-12
try using generic lcd monitor 1024 x768 at 60hz

---

### Post by buick1946-2 on 2008-06-16
Yup, Got this problem myself. It is pretty much an Ubuntu/Kubuntu issue, and maybe some other Linux flavors.

Get Kubuntu running by using the VESA driver and a generic 1600 x 1200 LCD display driver (boot int safe graphics mode and open the system settings, go to monitor and display settings, get into administrator mode and configure your monitor and primary display adaptors as above)

This will give good static a good static display, but no hardware acceleration, so video playback will be awful.

Puppy 4.0 and PCLinuxOS 2007 work fine with this card. The Ubuntu/Kubuntu solution involves a lot of complex command line work and even kernel compiling. This stuff is the heart and soul of linux flexibility, however, if you just want it to work my best advice is to go distro hopping until you finone that you like that works with your hardware.

---

