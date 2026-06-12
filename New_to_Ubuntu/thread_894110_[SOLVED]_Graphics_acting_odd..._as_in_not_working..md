---
title: "[SOLVED] Graphics acting odd... as in not working...."
date: 2008-08-18
forum: New to Ubuntu
---

### Post by pelle@xburk on 2008-08-18
Dear Ubuntonians,

I've just re-installed Ubuntu again, cause Windows ****** (excuse the french) my harddrive over again when I tried to dual-boot.  I'm just so damn sick of it right now so I thought, "Hey!  Why not go 100% Linux instead?", so I went for it and here I am.  Expecting everything to be a little tricky at first as usual, I managed not to screw up all the config files, so that's all good.  What sucks though is that XGL doesn't seem to work, so I can't launch Compiz, so I can't launch AWN, which makes my desktop look like utter (not really) crap.  My BIOS have been weird since Windows was all weird (sorry for the not-so-in-detail description), so in the POST it says that my system is in Safemode.  Could that be why XGL doesn't work?

I'm running Ubuntu 8.04 Hardy Heron for an AMD64.

Specs:

AMD Athlon X2 64-bit 3800+
2GB RAM
nForce 4+ Ultra MB
nVidia GeForce 7900 GT 256MB

That's all I can remember.

Also:
[URL="http://paste.ubuntu.com/38687/"]
http://paste.ubuntu.com/38687/[/URL]

---

### Post by epidemiks on 2008-08-18
Have you enabled the restricted driver for your card?
EnvyNG may help get the best drivers for you

---

### Post by nicedude on 2008-08-19
Disable the restricted driver for your graphics and instead use envyng here is the command to install it

COMMAND TO INSTALL
sudo apt-get install envyng-gtk

COMMAND TO LAUNCH
sudo envyng-gtk

once you let it download and install the best driver then right click on desktop and select "change desktop background" then tab "visual effects" then select "extra" after enabling that compiz fusion can work. So install compiz manager

sudo apt-get install compizconfig-settings-manager

THEN LOOK UNDER -> System -> Prefferences -> Advanced Desktop Effects Settings 

This will let you manage the 3D compiz fusion pluggins :-)

Goodluck

---

### Post by Separ on 2008-08-19
Although many people say to use EnvyNG, it has risks attatched to it and you could end up hosing your system. I would recommend that to be the last thing that you try if all else fails.

To check for/enable the driver from the Restricted Drivers Manager:
go to System > Administration > Hardware Drivers and check the box.

**_OR_**

To install the Nvidia binary driver from their website:
1. Download the Linux-Source package by typing
```
sudo apt-get install linux-source
```
2. Download the Nvidia binary driver.
3. Hit ctrl+alt+f1 to get to tty1
4. type ```
sudo /etc/init.d/gdm/stop
```
5. "cd" to the directory that you downloaded the driver
6. Type ```
sudo sh NVIDIA-x86-installer
``` or whatever the driver is called.
7. Type ```
sudo /etc/init.d/gdm start
```
8. Follow the prompts and make sure that under the "devices" section of your /etc/X11/xorg.conf file is set to "nvidia" and not "nv".

**_OR_**

To install Envy:
Do as posted above.

---

### Post by pelle@xburk on 2008-08-19
Envy did the trick!  Thank you guys so much!  :)

---

