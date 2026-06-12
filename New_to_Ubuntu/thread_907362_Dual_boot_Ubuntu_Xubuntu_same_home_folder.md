---
title: "Dual boot Ubuntu Xubuntu same home folder"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by C.S.Cameron on 2008-09-01
I am dual booting Ubuntu and Xubuntu and would like to use the same home folder for both on its own partition.
Is there simple method?

---

### Post by jamesrfla on 2008-09-01
xubuntu and ubuntu are the same except Ubuntu uses the gnome desktop and xubuntu uses xfce desktop. To get the xfce desktop run ```
sudo apt-get install xubuntu-desktop
``` Let me know if it doesn't work.

---

### Post by in-dust-rial on 2008-09-01
yeah, he is right! 
if you have installed several desktop-environment (KDE,GNOME,XFCE) or window-manager (simular but smaller then desktop-environments)

you can choose "SESSION TYPE" in the login screen ( the SESSION MANAGER )

#############
if you would like to have two STAND ALONE installations of ubuntu (and gentoo, suse, whatever, maybe even windows) you can use the 
```
/etc/fstab
```
and **_*mount*_** there any partition you want into ur /home/

---

### Post by clinto on 2008-09-01
Yeah, simply put, ubuntu, xubuntu, kubuntu, etc. are all the same, they just use different desktop environments(DE).  You can set up your Ubuntu install to include multiple DEs and choose which one you wish to use at the login screen.

As far as sharing a /home, you'll need to have a separate partition set up just for /home.  If you wish to share the same config files for multiple distros, you'd have to use the same login name(or move your home directory to the one that the other distro is using after you install).  While you *may* be able to get away with this in some cases, different distros and DEs or window managers and apps may use the same files different and could possibly cause conflicts.

I tried this once for a short period of time and didn't seem to have any problems.  However, I decided against it and just started using different home directories within the home partition for the different distro installs.

---

### Post by in-dust-rial on 2008-09-01
if you change home, some environmental variable can be set wrong!
- i dont remember what i did, but after moveing /home/ to somewhere, bash scripts always returned, that ```
#/bin/bash
``` could not be found... i just remember it was easy to solve the problem, after i realized what is wrong

---

### Post by kansasnoob on 2008-09-01
Look at this section:

> Playing Around
Enable Desktop Effects
KDE/Gnome Comparison
Install Gnome
Install KDE
Install XFCE
Install IceWM
Install XPDE
Pure Gnome
Pure KDE
Pure XFCE
A faster KDE
Replacing Nautilus 

In this tutorial:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Also it's much better to use aptitude than apt-get to install a different desktop:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

As far as sharing a true /home partition between different distros, I'd think it would be a mess. Xubuntu uses Thunar whereas Ubuntu uses Nautilus. I'd think it would be a mess!

---

