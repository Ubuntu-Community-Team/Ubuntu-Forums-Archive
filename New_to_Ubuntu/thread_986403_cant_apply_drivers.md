---
title: "cant apply drivers"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by metallicamike on 2008-11-18
i got two updates that turned out to be the drivers i needed for my crappy integrated intel card, but now i want to apply them, but i cant seem to figure out how. i have looked in hardware drivers, but it says 'no proprietary drivers installed'. also fyi, im running intrepid

---

### Post by metallicamike on 2008-11-18
anyone?

---

### Post by nakama85 on 2008-11-18
drivers for what? (sound,video)

---

### Post by halitech on 2008-12-01
> **metallicamike said:**
> i got two updates that turned out to be the drivers i needed for my crappy integrated intel card, but now i want to apply them, but i cant seem to figure out how. i have looked in hardware drivers, but it says 'no proprietary drivers installed'. also fyi, im running intrepid

The reason it says no proprietary drivers installed is because Intel drivers are open as opposed to drivers by ATI and Nvidia which are closed source. If you installed the updates then they are already in place, unless you told the updates to download them only.

---

### Post by metallicamike on 2008-12-01
ok, in another thread, i posted the output of a command in terminal, and the other guy said that i have mesa drivers in place.

---

### Post by metallicamike on 2008-12-01
> **nakama85 said:**
> drivers for what? (sound,video)

video

---

### Post by halitech on 2008-12-01
do you have the link for that thread?

---

### Post by metallicamike on 2008-12-01
[http://ubuntuforums.org/showthread.php?t=980381](http://ubuntuforums.org/showthread.php?t=980381)

it says solved, i thought that the random everything was what was causing the issue, turns out it wasnt.

---

### Post by halitech on 2008-12-01
ok, open a terminal and run this```
sudo dpkg-reconfigure xserver-xorg
```

select Intel I810 for the driver and reboot. It should work better.

---

### Post by metallicamike on 2008-12-01
all that that does is a bunch of crap for my keyboard........?

---

### Post by halitech on 2008-12-01
do this first:
open a terminal and type```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_old
``` so we have a working backup

ok, try this first```
gksudo displayconfig-gtk
```
and if that doesn't work, we'll need to manually replace mesa with intel i810 in Xorg.conf
```
gksu gedit /etc/X11/xorg.conf
```

---

### Post by metallicamike on 2008-12-01
ok, the first one (not the backup) didnt work, and so i need to know how to manually replace it.

---

### Post by halitech on 2008-12-01
run the second command, it will open the Xorg.conf file in a text editor. Then look for the section that has Mesa and replace it with intel i810

---

### Post by metallicamike on 2008-12-01
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection
```

mesa doesnt seem to be in there....

---

### Post by halitech on 2008-12-01
forgot, you are using interpid which has everything being auto-configured. Not sure at this point other then alot of people have problems with configuring things themselves. Do a search on intel i810 in the forums and see if it turns anything up.

---

### Post by metallicamike on 2008-12-22
bump

---

### Post by metallicamike on 2008-12-22
bump

---

