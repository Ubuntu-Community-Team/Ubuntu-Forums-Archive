---
title: "Laptop Touchpad"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by diego898 on 2008-08-16
I have an Dell Inspiron E1505. The touchpad doesnt really work that well. Its as if I touch it, let go, and touch it again to do something else it doesnt really register that well. Sometimes my workspace switches without warning!! Is there some kind of driver for it?

---

### Post by bhadotia on 2008-08-16
If your touchpad is synaptics I think the driver is called 'x11-xorg-synaptics'. You can customize the touchpad in System>Preferences>Mouse. Also, You can install gsynaptics for further tweaking of the touchpad. You will need to edit the /etc/X11/xorg.conf file after installing gsynaptics. If you need help eith the edition post back.

---

### Post by nicedude on 2008-08-16
Also there is a command line program called tpconfig that if you figured out settings for could be added to startup script.

---

### Post by diego898 on 2008-08-16
> **bhadotia said:**
> If your touchpad is synaptics I think the driver is called 'x11-xorg-synaptics'. You can customize the touchpad in System>Preferences>Mouse. Also, You can install gsynaptics for further tweaking of the touchpad. You will need to edit the /etc/X11/xorg.conf file after installing gsynaptics. If you need help eith the edition post back.

How do I get that?

---

### Post by nicedude on 2008-08-16
The best way I know of to find programs to do certain things or that you know the name of is to use synaptic package manager. Heres the command line command to luanch it

sudo synaptic

or go to System -> Administration -> Synaptic package manager

Then search by name or by name & description and you can see what is available to do what.

Hope this helps

---

### Post by diego898 on 2008-08-16
what do I edit and what do I put inside of it?

---

### Post by nicedude on 2008-08-16
OK diego you probably have either a synaptic or alps touchpad there are several programs to control these listed in synaptic package manager ( it is like add/remove programs for ubuntu in a gui window ) try searching there and also try different settings in System -> Preferences -> Mouse -> touchpad tab and see if you can control it that way.

Goodluck

---

### Post by bhadotia on 2008-08-16
> **diego898 said:**
> what do I edit and what do I put inside of it?
Do this in the terminal
> sudo gedit /etc/X11/xorg.conf

Then in the file that opens up look for this
> Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection
Here put a option "SHMConfig" "true" before the EndSection to make it look like this:
> Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
        Option          "SHMConfig"             "true"
EndSection
Log out and log back in. 
Now try tweaking your toucjpad with System>Preferences>Touchpad and see if it works.
Good Luck.

---

