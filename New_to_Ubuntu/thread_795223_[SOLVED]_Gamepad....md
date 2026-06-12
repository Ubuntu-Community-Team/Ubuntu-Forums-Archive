---
title: "[SOLVED] Gamepad..."
date: 2008-05-15
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-15
I'm trying to install  (In hardy) a game pad i bought on eBay and i followed these instructions

```

sudo apt-get update

then

sudo apt-get install joystick

tell it to load at boot.

then

sudo apt-get install jscalibrator

tell apt-get yes when it asks something.

Then, after these packages are installed, plug in you USB gamepad. Wait a minute. Then type in the terminal:

sudo chmod 666 /dev/input/js0 
```
but i still cant use it, although i had the game pad plugged in when i installed the packages...is that the problem? oh and how do i "tell it to load at boot."?

Thanks in advance:)

---

### Post by kamitsukai on 2008-05-15
Ok ive opened joystick calibration from the menu and i can press butons on my gamepad and they will move the buttons on the calibration but i cant use it with a game...oh and it appears ubuntu as mounted it as a media storage device?

---

### Post by kamitsukai on 2008-05-15
wow this is the first time that i havent had reply within 5 min lol :(

---

### Post by tjwoosta on 2008-05-15
what game are you trying to use it with?


you should look into joy2key (in synaptic)

---

### Post by kamitsukai on 2008-05-15
oh cool this might be why it wasnt working...

---

### Post by kamitsukai on 2008-05-15
> **kamitsukai said:**
> oh cool this might be why it wasn't working...

OK i installed it but there seems to be a problem...i tried running it from terminal and i get this...

```
dreamsofubuntu@dreamsofubuntu-desktop:~$ joy2key
joy2key - reads joystick status and dispatches keyboard events
By Peter Amstutz (tetron@interreality.org)
This is free software under the GNU General Public License (GPL v2)
              (see COPYING in the joy2key archive)
You are welcome to use/modify this code, and please e-mail me
if anything cool comes of it!
Version: 1.6.1   Binary built on Oct 30 2007 at 08:10:20

Error opening /dev/js0!
Are you sure you have joystick support in your kernel?

```

Shouldn't it be using "/dev/input/js0" instead of "/dev/js0"

---

### Post by tjwoosta on 2008-05-15
> Shouldn't it be using "/dev/input/js0" instead of "/dev/js0"

yes, it should be /dev/input/js0 

(ive actually never used this program before, i just thought it would help you)

there has to be some way to change the /dev/js0 to dev/input/js0 but i have no idea how

ive been searching for a config file but i cant find one

---

### Post by kamitsukai on 2008-05-15
yer same well hopefully someone can help with this :) thanks for your help so far

---

