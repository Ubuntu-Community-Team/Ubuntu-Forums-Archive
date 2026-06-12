---
title: "Black screen"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by EliMi on 2008-04-29
Hey, Im a complete newbie at ubuntu.
Ive installed it today to see another OS than windows for a change
I liked it but I cant seem to install a 3d driver for my ATI x800 GTO
i get a popup with message "Restricted driver available" for my card but if i enable the accelerator driver, after the restart, ubuntu loads and then the screen goes black and i cant do anything.  i reinstalled ubuntu like 2-3 times cuz of that.
ive read somewhere that i can boot to a similar configuration as windows safe mode and simply change back the way it was, how do i boot into something on ubuntu?

im using: 
Ubuntu 9.04 (Hardy) on 
Intel 3ghz
1.7Gb ram
Ati Radeon x800 GTO

How can i install a 3d driver for my card?

---

### Post by it290 on 2008-04-30
Yes, hardy seems not to like that card for some reason. I have the same one, and any attempts to use the fglrx driver resulted in a black screen. The 'ati' driver does work and will give you servicable 3d, however.

In order to boot into 'service mode', you can hit escape after the POST screen and tell Ubuntu to boot into recovery mode. From there you can attempt to use the 'fix X' option or drop to a root shell in order to edit your xorg.conf file.

---

