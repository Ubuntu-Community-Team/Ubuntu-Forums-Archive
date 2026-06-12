---
title: "upgrading my distro HELP!!"
date: 2008-03-06
forum: Philippine Team
---

### Post by Kulaspiro on 2008-03-06
greetings.....

i gave up reconfiguring my xorg/X11...no matter what i do, i cant seem to restore my working And Reliable feisty... ryt now, ala akong GUI, i tried 2 do all threads/how to's on X11 but nothing is working for me. ..finally, i have decided to just move on and run GUTSY...my worries are...with so much messing w/ my xorg/ ati drivers( i have installed/uninstalled envy too.)...reconfigure,renaming  etc/X11/...
IS it possible to have a clean upgrade to gutsy from a messed up feisty? if so... how? i dont have a GUI,...can u give me a terminal like how to:?

THANK you all!

hp nx6125 notebook
ati radeon xpress 200M
amd mobile sempron 1.8Ghz

---

### Post by ragadanga63 on 2008-03-06
That happened to me once.  With no access to the internet, what I did was replace my installed xorg.conf with that of the Live CD.  At least I had a GUI to rebuild my system.

---

### Post by februarius on 2008-03-10
might help this thing 

sudo dpkg-reconfigure -phigh xserver-xorg

or 

sudo nano /etc/X11/xorg.conf

find Section "Device" then look for driver under then try put vesa then ctrl+o for save then hit enter

then 

sudo /etc/init.d/gdm stop then /etc/init.d/gdm stop 
or /etc/init.d/gdm restart

---

