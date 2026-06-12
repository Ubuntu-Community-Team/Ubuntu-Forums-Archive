---
title: "Problems with LCD Monitor resolution"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by peter290935 on 2008-08-05
The monitor I am using is an ACER AL707.  On both boxes I installed ubuntu from an iso taken from the APC magazine DVD. I then upgraded from the internet.  The results on the two boxes are different.

On one box ubuntu boots, and to see a menu I need to press escape. The menu options are: Ubuntu 8.04.1, kernel 2.6.24-19 Generic Ubuntu 8.04.1, kernel 2.6.24-19 Generic - recovery mode Ubuntu 8.04.1, kernel 2.6.24-16 Generic Ubuntu 8.04.1, kernel 2.6.24-16 Generic - recovery mode Ubuntu 8.04.1, Memtest86+

Since I only installed form one Iso I do not understand why I have two versions of the Kernel, but perhaps this was created by the updates.

On the second box the menu is displayed without needing to press escape.



 On the first box the processor is Pentium 4, 2.4g with 480 Mbyte ram.  I suspect this box has an on board video. 
On selecting first menu option the monitor first displays a message saying Input not Valid, eventually id displays the login screen, but the monitor the goes into autoconfig mode. Once logged in the best resolution offered is 960 x 600.

On the second box which has 728 Mbyte ram and a nvidia TN vidieo card with 32 M ram, the menu displays without the need to press esc. After choosing the first menu option the screen is set to 800 x 600


Note that the resolution of the screen on the XP box is 1152 x 864.

All three machines are connected to the same monitor, keyboard and mouse by an electronic switch. Whenecer I select the firsat Linux box the monitor is set into autoconfigure mode

If I boot the machine with the Nvidia card using the 2.6.24-16 kernal then it opens in 800x600 but I can (sometimes)change the resolution using preferences to 1280 x 1024.

On the other machine with mother board video this makes no difference.  I would like to get the higher resolution options on both machines. Can anyone suggest what I need to do?

How do I confirm what video cards etc are on the machines?

Regards


Peter Goggin

---

### Post by ConMan318 on 2008-08-05
The multiple kernels are from the update; your .iso had an older one so it was updated.  You can remove the old one if you'd like, though most people recommend keeping at least one older kernel available.  And I believe the need to press escape to get to the splash menu is a BIOS thing, not  Ubuntu thing.

You need to install or enable the drivers for the cards.  Try going into System > Administration > Hardware Drivers and see if there is a vid-card driver there.  If so, enable it.  Then your res should be able to be set properly.

---

### Post by bobnutfield on 2008-08-05
To find out what graphics card you have on each machine, open a terminal and type:

> lspci | grep VGA

This will reveal the installed graphics card and usually its exact model.  Whether or not you need propriatory graphics depends on the card.  The nVidia card will definitely be improved with a prop. driver.

Many find it much easier to install EnvyNG (available in the Synaptics Package Manager).  Once installed, when you run it, it will determine your graphics card, download and install the correct driver for it, and automatically reconfigure your Xorg.conf file.  You can then set the resolution correctly to your tastes.

---

### Post by peter290935 on 2008-08-14
I tried downloading the nVidia drivers but this did not help.

What I have found is that If I start my XP box first then the Linux systems cannot set the monitor properly. If I start a linux box first and leave the monitor connected via the KVM switch until the completion of the login sequence then the resolution is set properly. I now start the Linux boxes, one at a time and then the XP box and all of the systems set the monitor resolution to 1280 x 1024 which is the full resolution of the monitor

---

