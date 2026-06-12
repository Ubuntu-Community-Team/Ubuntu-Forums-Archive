---
title: "[SOLVED] Multiple xorg boot menu"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by C.S.Cameron on 2008-09-09
I am running Xubuntu from thumbdrive.
This works ok on all my computers (that will boot from TD).
As long as I do not install Restricted drivers.
I would prefer to be able to select between xorg configurations at boot to choose between generic Intel, Nvidia or ATI, depending on which computer I plug it into.
Is there a simple way to do this?

Solved, (sort of)

I set up switchconf, it lets me choose between multiple xorg.conf at grub.
I can choose a xorg.conf with or without Nvidia drivers. 
I can choose a xorg.conf with or without ATI drivers.
But when I install the Nvidia drivers they delete the ATI drivers and vice versa.
A switchconf how to is at:
[http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/](http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/)

---

