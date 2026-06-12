---
title: "Is my SiS760 Mirage graphics chip supported by Gutsy?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by aimpau on 2008-04-22
The graphic settings say:

SiS Real256. I've searched for a suitable Linux driver but to no avail.

I can:
Change my desktop resolution
View movies

I'm just wondering.

Thanks!

---

### Post by Ub1476 on 2008-04-22
If you can change and use highest screen resolution with the best refresh rate, it should be fine. If the driver is open, it's probably included in the Linux kernel.

Also if screensaver, Google Earth etc work, it's good.

---

### Post by aimpau on 2008-04-22
Hi there,

Anyways, I have a CD installer of the chip (it's not a vidcard but an onboard VGA chip). However, the installer is for windows. I know something is wrong since whenever I boot up to xubuntu, it says there in the monitor Sync. Out of Range but when I boot up in WinXp, it doesn't say that.

I'm using 1024x768 60Hz refresh rate.

---

### Post by propwashz on 2008-04-22
your splash screen resolution needs to be changed to 1024 x 768 --I found the terminal commands to do it in these forums a couple of days ago--just do a search...I would give you the link,but I can´t find it right now...

---

### Post by propwashz on 2008-04-22
Found it--
try this--I think it will fix your out of range error,as well as your splash-screenage..

[http://ubuntuforums.org/showthread.php?t=756668&highlight=fix+splash+screen](http://ubuntuforums.org/showthread.php?t=756668&highlight=fix+splash+screen)

---

### Post by Ub1476 on 2008-04-22
Well, if it's a problem with the bootup sequence (do you see the bootimage?), you can install StartupManager, and change the resolution and depth of the boot to something more appropiate than what is already set (I would suggest not to use a very high value, because you won't be able to boot then).

Say, you can set res to 1024x768 (or lower) and depth to 16 (maybe 24).

The thing is, every integrated VGA I know has drivers included in Ubuntu (the Linux kernel to be exact). If there is an integrated VGA which do not have the proper res and Hz, it should be in the repos (like the i810 for intel). ATI and nVidia VGA drivers can be found in the Restricted Driver Manager.

However, not every VGA manufacture is so good to support with drivers furher than correct res and Hz rate, like direct rendering, which (if working) enables you to use 3d stuff such as Compiz (I know some VGAs from VIA for instance can't do this).

So, it's probably not a driver which is the problem you encounter, just what I would call some "safe settings", which is working, but not perfect (here's where StartupManager comes in).

---

### Post by aimpau on 2008-04-22
Thanks Ubl476 and propwashz! :)

Solving this kinds of problem is a real learning experience for me and I try as much as possible not to "integrate" my XP diagnostic troubleshooting with my learning.

Thanks!

---

