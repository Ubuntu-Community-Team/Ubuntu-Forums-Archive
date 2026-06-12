---
title: "PLEASE HELP! Ubuntu doesn't start!"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by sober on 2008-06-24
Hi, i'm in great trouble and i hope someone can help me.

Today i uninstalled all of the ALSA drivers from my laptop (HP Pavillion dv6000 AMD Turion 64x2, 1ghz ram, Ubuntu 8.04) with synaptics, checking everything ALSA in there. Then i reinstalled all that and proceeded to reboot but i couldn't start ubuntu! 

The system goes to load as usual, but instead of the splash screen where i have to write my username and password, the system doesn't start ubuntu and instead it continues running on the terminal. It says:
> 
Loading, please wait...
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
kinit: name_to_dev_t (/dev/disk/by-uuid/7c04b86f-811a43b0-abd6-d8476082ce11) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/7c04b86f-811a43b0-abd6-d8476082ce11
kinit: No resume image, doing normal boot...

Ubuntu 8.04 (user) tty1

(user) login:

So i type my username and password and i get the last login date, and some disclaimers (the programs are free software... )
Aand then "1 failure since last login.
Last was Tue 24 Jun 2008 09:26:48 AM CDT on tty1

then i have the command prompt, and if i type ls i see all my folders and documents. But all this stills on the terminal.

How can i start normally ubuntu? What's the problem? 
And if i have to restore or reinstall ubuntu, will i lose all my files? i only have ubuntu in my laptop, not windows at all. Is there some way to burn files from the terminal? I don't have USB ports, and this happened when i was getting ready to backup everything....

Hope someone can help!!!! :confused::(:confused::(

---

### Post by Canis familiaris on 2008-06-24
Try this command and see whether the GUI loads
```
sudo gdm
```

---

### Post by AOZ on 2008-06-24
this may be completly wrong but when you boot i think ur in your tty1 instead of tty7. so when your in the blank screen terminal thing press ctrl+alt+F7

---

### Post by niyonk on 2008-06-24
> **Anurag_panda said:**
> Try this command and see whether the GUI loads
```
sudo gdm
```

what do you think of sudo apt-get -f install? :-D

or CTRL-ALT-F7?

---

### Post by Canis familiaris on 2008-06-24
> **niyonk said:**
> what do you think of sudo apt-get -f install? :-D

or CTRL-ALT-F7?
CTRL-ALT-F7 will switch to the GUI only if X is loaded. Maybe it will help.
Yeah if the packages are broken sudo apt-get -f install will work well.

---

### Post by sober on 2008-06-24
Thanks for the quick answer! I've always said that what makes ubuntu what it is today are the users :) 

Well i've tried everything posterd here, i ran sudo apt-get and seemed to install everything, but nothing happens when i press ctrl+alt+f7 (or F anything)... when i use gdm it says command not found.... 
Do i have to be in a specific directory? bash says it's in my home folder. Or is there any moment in specific during turn-on that i have to do all this¿

Thanks in advance!

---

### Post by sober on 2008-06-24
BTW when i run sudo apt get f install i get:

> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
debhelper libbeagle1 po-debconf libggzmod4 libtimedate-perl int1tool-debian gettext fceu libggz2 dpkg-dev debconf-utils html12text libggzcore9 python-gdata patch fxload xulrunner-1.9-gnome-support
Use apt-get autoremove to remove them
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded


Still can't use CTRL+ALT+F7 :(

---

### Post by jpeddicord on 2008-06-24
If you're using 8.04, try running:```
sudo dexconf
```
That will reset your X configuration (restart) and hopefully make the display start on next boot.

---

### Post by sober on 2008-06-25
> **jacobmp92 said:**
> If you're using 8.04, try running:```
sudo dexconf
```
That will reset your X configuration (restart) and hopefully make the display start on next boot.


Thanks, but i tried and it didn't work :( nothing happened when i rebooted..

Any more ideas about fixing this? Thanks..

---

### Post by sober on 2008-06-29
Well so far nothing worked, i've been running the GUI with "startx" altough i need to logout and go back to the terminal... hope someone has any possible solution... thanks

---

