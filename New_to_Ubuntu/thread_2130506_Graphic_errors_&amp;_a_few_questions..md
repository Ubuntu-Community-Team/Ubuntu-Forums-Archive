---
title: "Graphic errors &amp; a few questions."
date: 2013-03-29
forum: New to Ubuntu
---

### Post by kikcer2 on 2013-03-29
Hello,

I am a newer ubuntu user and I am having some issues with Ubuntu 12.10

the main reason I am posting here is Whenever I hit the dash home button, the screen turns black and white (kinda like channels will do in a rain storm when you have dish), then the screen goes to the correct skin but its all distorted sometimes completely scrambling words and turning the upper taskbar yellow and scrambling all my icons.

I have tried a few of the drivers available in the software sources and I always get the same issue.
the GPU on this computer is 

Nvidia c51g [geforce 6100] rev. A2

now I have also been recommended simply switching to the KDE GUI,

computer specs

MOBO - Asus k8n-vm
CPU - Amd Sempron 3000+
and 686mb of ram

on another graphic issue, right now i cannot seem to adjust my display dimensions off of 600x400 which ends up making my icons and windows HUGE on my screen.

Quick little edit: with my screen showing in the 600x400 i am not having any of the dash home issues.


My last issue that isn't really a big deal, im having issues getting Firefox to show certain webpages correctly. I do believe I have the correct Java and Flash players install. webpages like Youtube load and work perfectly, but for example if i go to Facebook the page is nothing but the links similar to web 2.0 mobile version.

Thank you very much for any all help.

---

### Post by MythicManiac on 2013-03-29
This most likely is a graphics device driver issue, I had the same problem but installing the official linux driver for my graphics card fixed this

---

### Post by MythicManiac on 2013-03-29
Tiny bit of googling gave me these:

[http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)

and

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/nvidia")

The first one seems easier to install. I'm not sure whether they'll work though, as I don't have a GeForce card

---

### Post by kuifje09 on 2013-03-29
I discovered such a same problem. 
Installed a system with a dvd version 12.04  and the kernel version 3.5.0-23 ? ( not quite sure - other system )
The system was fine, graphics and resolution ok, right display detected.

After the suggested update, all went wrong , kernel version 3.5.0.26 ?  
But also the xorg version differ !.

Then I had multicolor background ( like you are havely drugged ) wrong resolution wrong display ....
Thet kicked out some hardware so it seems.

Luckily I now know the same for G 6200,  I almost bought such card to overcome those problems.

See this post : [http://ubuntuforums.org/showthread.php?t=2127332](http://ubuntuforums.org/showthread.php?t=2127332)

---

### Post by kikcer2 on 2013-03-30
> **MythicManiac said:**
> Tiny bit of googling gave me these:

[http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)

and

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/nvidia")

The first one seems easier to install. I'm not sure whether they'll work though, as I don't have a GeForce card


Thank you for the links. I did try those and im still having issues with the the forced screen sizing.


edit; after a reboot today the force screen size issue has been corrected.  im thinking it may stem from the ppa based update.

---

