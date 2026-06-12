---
title: "Problems with Logging-in after Installation"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by chris221 on 2014-05-11
Alright so I installed Ubuntu 14.04 onto my windows 7 computer and Installed it instead of win-7, Installation was sucessful with no problems then after I was prompted to reset it brought me to the log-in screen. When I logged-in successfully and will it was loaded my screen all of the sudden went to this:

[IMG]http://snag.gy/I88Pk.jpg[/IMG]


After I got this problem I went and got a new copy of the ISO and put it on a flash, I selected re-install and tried to log-in again after the re-installation, and got the same result!

My graphics card: **NVIDIA GeForce 7050 **

Does this mean its my computer and not Ubuntu? Can anyone help me?

---

### Post by Bashing-om on 2014-05-12
chris221; Hi ! My Welcome to the forum.

That in all probability is a graphics driver issue.
Try booting with the "nomodeset" boot parameter, and once to the desk top install from the "Additional Drivers" utility the recommended driver.
This link for applying "nomodeset".
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132).

[INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris221 on 2014-05-12
I'm not getting the messed up screen but now Ubuntu is basically zoomed in and I can't use the mouse !?

---

### Post by Bashing-om on 2014-05-12
chris221; Hey.

One size does not fit all, we need to do just a bit of tailoring.

Mouse. keyboard and graphics (as well as others) are all a part of the Xorg layer in the operating system. The proper graphics driver will alleviate this issue.
Please advise what you have done in changing out the graphics driver, then we can discuss what other alternatives there exist.

Let's look at what is presently;
Boot to the grub boot menu, -> advanced options -> recovery mode -> resume normal boot. Degraded graphics at this point is OK, we will try and fix that.
The key combo ctl+alt+t will yield a terminal, post back the outputs - between code tags - of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
To see your graphics card and info.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

