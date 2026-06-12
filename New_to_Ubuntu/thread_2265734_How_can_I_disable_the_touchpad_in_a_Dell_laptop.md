---
title: "How can I disable the touchpad in a Dell laptop?"
date: 2015-02-17
forum: New to Ubuntu
---

### Post by berkbw on 2015-02-17
How do I disable the touchpad on a Dell laptop?  I have had a recurring problem, not just with Ubuntu nor this computer: My hand passing over the touchpad, seems to cause unpredictable input.  It reminds me of when static discharge used to be a problem.  This has caused a **LOT** of lost data entry, as programs get killed, new ones opened, etc.

Thanks for any help in this,
b-

---

### Post by sudodus on 2015-02-17
See these links to recent threads about the same or a similar subject:

[http://ubuntuforums.org/showthread.php?t=2250916](http://ubuntuforums.org/showthread.php?t=2250916)

[http://ubuntuforums.org/showthread.p...2#post13164172]("http://ubuntuforums.org/showthread.php?t=2252169&p=13164172#post13164172")

[URL="http://ubuntuforums.org/showthread.php?t=2263662"]http://ubuntuforums.org/showthread.php?t=2263662
[/URL]

---

### Post by JeQhdMD on 2015-02-17
Many (but not all) laptops have a combo key that toggles the touchpad (on/off).   Check the top row of keys for a touchpad graphic-symbol - usually you tap the "Fn" key then the assigned key.   On my Acer Timeline, it's Fn+F7, on my System76 Galago, it's Fn+F1.    IF the key isn't apparent . . . check your user manual for your model and check the index for touchpad . . . so, most of the time there is a solution.    

This is actually very important . . . I had a Compaq laptop that was almost worthless because of that issue (so, check for this functionality as one of your "must-haves" for any future laptop purchase (along with a matte-nonglare screen of course))!!  ;)

ALSO . . . did you check if using the checkbox (disable while typing) via "System Settings" > "Mouse & Touchpad" works?  (worth a try it seems).??

ALSO+1 . . . . see the tables at bottom of web link:   [http://www.dell.com/support/article/us/en/19/SLN114937/EN](http://www.dell.com/support/article/us/en/19/SLN114937/EN)

---

### Post by Dragonbite on 2015-02-17
I am going to have to read through those threads. I'm wondering if I can have the trackpad turned off when a USB mouse is plugged in, and turned back on if it gets unplugged.  

My wife has this setup on her Dell running Windows, but I have only started thinking about it on my Compaq running Linux.

---

### Post by sudodus on 2015-02-17
I find it easy to use 'touchpad-toggle' from a terminal window.

But if you want something that looks better and is a little bit more  advanced, for example can have the trackpad turned off when a USB mouse  is plugged in, and turned back on if it gets unplugged, you can try ***touchpad-indicator***, which works well in some versions of Ubuntu but might be hard to install in other versions.

[https://launchpad.net/touchpad-indicator](https://launchpad.net/touchpad-indicator)

[URL="http://www.webupd8.org/2011/02/touchpad-indicator-now-automatically.html"]http://www.webupd8.org/2011/02/touchpad-indicator-now-automatically.html
[/URL]
[HR][/HR]
*Edit*: See also this link, in Spanish, but it indicates that the touchpad-indicator is updated/upgraded for 14.04 LTS, and the command lines for installation are there.

[http://www.atareao.es/ubuntu/gestion-del-touchpad-con-touchpad-indicator-en-ubuntu-trusty-tahr/#more-9057](http://www.atareao.es/ubuntu/gestion-del-touchpad-con-touchpad-indicator-en-ubuntu-trusty-tahr/#more-9057)

---

### Post by mc4man on 2015-02-17
The touchpad indicator seems to be good here, 14.04
Because it's running it can  resolve the issues with log outs, restarts & coming out of suspend when using a usb mouse on a laptop
So here i'll think I use over an autostart script that used gsettings to turn off (the script worked fine with everything but suspend

---

