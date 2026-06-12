---
title: "Failed boot. log file"
date: 2015-01-23
forum: New to Ubuntu
---

### Post by john350 on 2015-01-23
Hey Y'all,
I messed up my install by playing with partitions. (ill just get a new hhd next time) Anyway I downloaded the boot-repair and applied it in live. Heres the link they suggested I post if it didnt work. Any help would be appreciated.
[http://paste.ubuntu.com/9836984/](http://paste.ubuntu.com/9836984/)

---

### Post by Derrick_Katula on 2015-01-23
can u access the GRUB2 boot loader . to check boot whilst holding the Shift key . if you see a menu with a  list of operating systems appear, you&#8217;ve accessed the GRUB boot loader.

 If you don&#8217;t see a menu with a list of boot options appear, the GRUB  boot loader may have been overwritten, preventing Ubuntu from booting.  This can happen if you install Windows on a drive after installing  Ubuntu or another Linux distribution on it. 

use the Ubuntu installation to repair the GRUB2 boot loader

---

### Post by LostFarmer on 2015-01-23
> Any help would be appreciated. Telling us just what the problem is might help.

---

### Post by john350 on 2015-01-23
OK. I had a 500 gb disk with Vista 32 - problem one. I installed ununtu 14.5 on a separate partition to slowly pull the files over then realised my partition might be too small. So, I used Gparted to try to change the partition size and messed everything up. No boot period. So after using the boot repair tool, I can now see the boot menu: *ubuntu, special ubuntu blah blah, Vista. Any time i try to boot i get the flashing cursor of death forever.. UNLESS I hit control alt delete. Then i see my ubuntu sign in momentarily before the system restarts. Here i am. I have no problem allowing remote assistance if thats possible.

---

### Post by john350 on 2015-01-23
I have a vista /norton 360 backup from sunday.. I could always wipe the disk, ceate new equal partitions, and start fresh. Vista problems is what started this in the first place. It would just be nice to have 64 bit access to those files.. Much faster.

---

### Post by oldfred on 2015-01-24
If you get grub menu, then it is installed.
Boot after that is often video issue or other boot parameters.
You do show you already have installed the radeon video driver.

Can you boot recovery mode from grub menu? Should be second line in menu.

---

