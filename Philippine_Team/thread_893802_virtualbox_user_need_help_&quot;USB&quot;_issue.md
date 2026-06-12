---
title: "virtualbox user need help &quot;USB&quot; issue"
date: 2008-08-18
forum: Philippine Team
---

### Post by killer_d76 on 2008-08-18
i have the 1.6.4 version of virtualbox, i've been using and playing with it for quite sometime now (to test OS's)and everything is working propely, but the "usb thumbdrive" is not showing up?, ubuntu, the host OS works properly and recognize the usb thumbdrive, but not on Windows XP in Virtualbox, need help here guys.

---

### Post by leepesjee on 2008-08-18
USB is not supported in the open source versions of VirtualBox. See their website for more information. [http://www.virtualbox.org/](http://www.virtualbox.org/)

Leo.

---

### Post by killer_d76 on 2008-08-18
have a look at this link [http://www.virtualbox.org/wiki/Changelog]("http://www.virtualbox.org/wiki/Changelog") this is from the Virtualbox site as well, and you can see from there that they have fixed the usb issue.. :confused:

---

### Post by loell on 2008-08-18
does this happen to all of your usb devices?

---

### Post by killer_d76 on 2008-08-18
> **loell said:**
> does this happen to all of your usb devices?

usb mouse works okey, but if i go to the usb settings, all the usb devices that is plugged-in is recognised, but they are all grayed out! :confused:

note: built in camera of my laptop is showing as one of the usb devices, though i was not able to make it work even on ubuntu.

---

### Post by loell on 2008-08-18
give this workaround a try

[http://forums.fedoraforum.org/showthread.php?p=1048386#post1048386]("http://forums.fedoraforum.org/showthread.php?p=1048386#post1048386")

---

### Post by Nhatz on 2008-08-18
killer_d76 dude follow mo lang tong link na to [http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html](http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html) para sa installation ng Virtualbox na may USB support for Ubuntu.... hehehehe :)

ASTIG! :guitar:

---

### Post by the yawner on 2008-08-18
> **Nhatz said:**
> killer_d76 dude follow mo lang tong link na to [http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html](http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html) para sa installation ng Virtualbox na may USB support for Ubuntu.... hehehehe :)

ASTIG! :guitar:

I got my Virtualbox to work using this guide. If you followed the same guide, especially yung sa *Enable USB Support in Virtualbox* then there shouldn't be any problem. Pero note that you may not use the USB device simultaneously on the host and guess OS. Try to unmount the USB in Ubuntu then check again sa Virtualbox.

On a sidenote, hindi ko rin mapagana yung built-in camera ko.

---

### Post by pendletone on 2008-08-19
i had the same problem before...and the yawner's right. what i did was ***not*** to mount the usb thumbdrive first on the host os, but rather wait for WinXP to boot inside VirtualBox and mount it there. Or simply unmount and re-mount the thumbdrive once inside VirtualBox.

...and yup i also followed *that* guide. :)

---

### Post by killer_d76 on 2008-08-19
thanks for all the help guys! ;) i tried to follow the guide last night, but i havent tried mounting the usb drive after the os on Vbox boots up.. cause i still can't seem to mount usb on virtualbox.. i'll post the error i'm getting later ;)

---

### Post by wersdaluv on 2008-08-19
I managed to make usb work by using the non-ose version from [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI) .

When you have that installed, go the the settings of your Virtual OS. In the USB part, tick the check boxes. :D

---

### Post by killer_d76 on 2008-08-20
thanks for all your help guys!.. i just found out what seems to be the problem..the code on the links have 124 ID, but mine was 125!.. i just replaced all the 124 with 125, restart computer and voila!.. usb is working on my VBox now!.. i was able to make the camera to connect.. but all i get is a black screen.. but its okey for now ;).. thanks guys.

---

### Post by killer_d76 on 2008-08-23
di din makatiis hehehe.. get those braincells working again guys.. need help here!..

i was able to make Virtual Box 1.6.4 with Windows XP on it to recognize all usb devices that i plug-in and it even detected the built-in camera of my laptop (specs at the bottom) though this camera haven't worked on ubuntu 7.10 and even on 8.04 that i have right now, but this camera works perfectly on XP (i have a dualboot system)!  now i when i enabled the built-in camera using XP on VBox all i get is a black screen?! tulong naman po mga brader and sisters! ;) thanks in advance

---

### Post by loell on 2008-08-23
have you installed the xp driver for that webcam?

---

### Post by killer_d76 on 2008-08-23
yes i did and i can see the camera icon on the screen, but when i activated it, all i get on the screen where you normally see your image showing, now its all black!, normally on windows xp, when the camera is activated i see consistent yellow color on the tip of the camera icon (lens part), but on VBox i noticed that the yellow part flickers :confused:

---

### Post by loell on 2008-08-23
apparently its a known problem, but has no clear solution

try editing the **ubfs** 

look at **Setup USB:**

[http://www.uluga.ubuntuforums.org/showthread.php?t=770745]("http://www.uluga.ubuntuforums.org/showthread.php?t=770745")

---

