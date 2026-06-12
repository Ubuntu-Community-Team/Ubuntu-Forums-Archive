---
title: "No Display Ubuntu 12.04"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by julio8a00 on 2012-04-28
After installing Ubuntu 12.04 (via wubi) there is no display!
the login sound plays but there is nothing visual. I have dual monitors and have one on HDMI and another on DVI, I also tried connecting it on VGA but nothing...
I previously had ubuntu 11.10 installed (via wubi) and everything worked fine then.

here are some of my system specs: 
Intel i7-2600 CPU @ 3.40GHZ
ASUS MAXIMUS IV GENE-z/GEN3 
NVIDIA GeForce GTX 550 Ti

I would appreciate some help, thanks!

---

### Post by ltburch2000 on 2012-04-30
I am having the same issue, I can tell it has booted from the sounds I get when hitting the keyboard but I have no display.

There is a display during the booting process.

I have tried booting off CD and off USB key.

Any guidance would be appreciated.

---

### Post by bcbc on 2012-04-30
Some graphics cards need workarounds to boot. So first thing is to identify your graphics card, second is to search for workarounds or post the spec if you can't find anything.

For setting boot options see this: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by anewguy on 2012-04-30
Since it's an nVidia card, you're going to need to add nomodeset to the boot line.

If you need help doing that, please post back.

In the mean time, hold down ctrl/alt and press F1 - you should see a login screen.  If so, it's definitely that you need nomodeset until you can get the GUI - once you have the GUI you will need to go to Additional Drivers, let it search, then install the nVidia driver.

Dave ;)

---

### Post by ltburch2000 on 2012-05-01
I have an nVidea card and this did the trick, adding nomodeset got me to the GUI.  There is a long delay after you start the boot after specifying nomodeset however given a few minutes it did start with the GUI.

> **anewguy said:**
> Since it's an nVidia card, you're going to need to add nomodeset to the boot line.

If you need help doing that, please post back.

In the mean time, hold down ctrl/alt and press F1 - you should see a login screen.  If so, it's definitely that you need nomodeset until you can get the GUI - once you have the GUI you will need to go to Additional Drivers, let it search, then install the nVidia driver.

Dave ;)

---

### Post by robbietea on 2012-05-01
What do I do for an ati card?

---

### Post by bodhi.zazen on 2012-05-01
> **robbietea said:**
> What do I do for an ati card?

Start your own thread, hijacking another is impolite. Be sure to identify your hardware.

---

### Post by julio8a00 on 2012-05-08
> **anewguy said:**
> Since it's an nVidia card, you're going to need to add nomodeset to the boot line.

If you need help doing that, please post back.

In the mean time, hold down ctrl/alt and press F1 - you should see a login screen.  If so, it's definitely that you need nomodeset until you can get the GUI - once you have the GUI you will need to go to Additional Drivers, let it search, then install the nVidia driver.

Dave ;)

Thanks! I will definitely give this a try! going to need some help with the nomodeset addidtion o the bootline. (a link/tutorial will suffice)

If I have any other issues or  concerns I will make sure to report them here, The help is greatly  appreciated.

---

### Post by julio8a00 on 2012-05-08
> **anewguy said:**
> Since it's an nVidia card, you're going to need to add nomodeset to the boot line.

If you need help doing that, please post back.

In the mean time, hold down ctrl/alt and press F1 - you should see a login screen.  If so, it's definitely that you need nomodeset until you can get the GUI - once you have the GUI you will need to go to Additional Drivers, let it search, then install the nVidia driver.

Dave ;)

I tried holding down ctrl/alt and pressing F1, but nothing helps, any suggestions?

---

### Post by julio8a00 on 2012-05-09
HA! figured it out! thanks for the help.

I used the "How to set NOMODESET" from this post: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

on post #8 it states how to fix on wubi, but It didn't work for me.
I tried editing \ubuntu\install\wubildr-disk.cfg  (adding nomodeset at the end of quiet splash) as stated but nothing.

with ubuntu versions 11.10 and 12.04 there is no visible grub when you boot (using wubi) all I did was select ubuntu from the windows boot menu then I hold SHIFT that loads grub

then I pressed "e" on the keyboard, from there I was able to add nomodeset after quiet splash and it worked !   =)

---

