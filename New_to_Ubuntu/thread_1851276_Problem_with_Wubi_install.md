---
title: "Problem with Wubi install"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by rvmedina20 on 2011-09-28
hey ubuntu community, 

I have a problem when i try to install Ubuntu using wubi: 

wubi seems to install properly, assign the partition and everything. After its done and i reboot i get the Dual Boot screen. When I choose Ubuntu I am taken to the Ubuntu setup prompts, BUT the problem is that the display is messed up and i cannot follow the prompts. (i have tried to install it multiple times, both 10.4 and the latest 11. version of ubuntu but i get the same problem) i attached a pic of the promts with the messed up display.  Please help.

current system: OS Windows Vista; RAM 3 GB; AMD-Turion 64 @2GHz

Thanks

---

### Post by anewguy on 2011-09-28
I'm not familiar with actually using Wubi, but it appears to me that you have a video driver problem.  Do you know what video adapter you have?

If possible, at the boot menu edit the string to boot Wubi, and see if it will allow nomodeset on the boot line - you may have to change quiet splash to nosplash nomodeset.  If you can do that edit, just try it once to see if it improves things.  If not, try editing again and change splash to nosplash noapic.

Post back any and all results!

Dave ;)

---

### Post by technosysind on 2011-09-28
I believe this a problem with the display card compatibility. Why don't you let the setup complete the installation and then try to configure the display card.
or
Have you already tried this??

---

