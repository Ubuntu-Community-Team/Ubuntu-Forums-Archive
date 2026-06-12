---
title: "updated to heron, now no grub entry for windows?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by snuffy on 2008-05-29
i updated to hardy heron from the previous release. now when i boot, there's no windows boot option in the grub menu.

please help.

---

### Post by UnWarierMage224 on 2008-05-29
As a possible step in the right direction...

When upgrading, was there an option to install the boot loader? If so, was it selected?

-'Mage

---

### Post by philinux on 2008-05-29
Get into terminal and post the result of

cat /boot/grub/menu.lst

---

### Post by snuffy on 2008-05-29
sorry, please read my initial post again, i wasn't quite accurate. i have the grub menu, but no windows entry.

---

### Post by philinux on 2008-05-29
ok

sudo fdisk -l
thats a lower case L

---

### Post by snuffy on 2008-05-29
the windows partition is still there if that's what you're asking? i checked.


> **philinux said:**
> ok

sudo fdisk -l
thats a lower case L

---

### Post by philinux on 2008-05-29
Ok then I'd re-install grub from the live cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by snuffy on 2008-05-29
cheers. i'll try reinstalling grub. looks tricky for a beginner ??

thanks.


> **philinux said:**
> Ok then I'd re-install grub from the live cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by philinux on 2008-05-29
The one disk I Have at the ready is this 

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Dang marvelous

---

### Post by meierfra. on 2008-05-29
Since you can boot into Ubuntu, grub is installed correctly. So you do not need to reinstall grub.  Probably all you need to  do is to add a few lines to the file "/boot/grub/menu.lst". If you would have posted "cat /boot/grub/menu.lst" and "sudo fdisk -l" as requested, it would be much easy for us to figure out what is going on and to help your fix your problem.  
"sudo fdisk -l" does not only tell us that the windows partition is still there, but more importantly what exactly to write in "menu.lst".

You need an entry like this at the very end of "menu.lst"

title Windows 
root (hd0,3)
makeactive
chainloader +1


or 

title Windows 
root (hd2,3)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


Of course the  numbers to use depend on your setup. The map lines are needed if XP is not on (hd0).

To edit "menu.lst" use

> gksudo gedit /boot/grub/menu.lst

---

