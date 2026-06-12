---
title: "Error 17!!!"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by zeroxorxdiexskater on 2008-07-06
ok well i had ubuntu and vista for a while (dual booting) and i decided to get rid of ubuntu. and went into vista and viewed my partitions and there were two extra partitions (one containing ubuntu) so i deleted the bigger one. when i restarted my comeputer the GRUB boot thing got an error 17 and it wont do anything else. i cant get onto vista or anything. i am using the ubuntu live cd right now. please help!

---

### Post by drsaamah on 2008-07-06
i would use the live cd to backup anything you need from the vista partition and then just do a clean install of vista.  the issue is most likely that you were using GRUB as your bootloader and then took out ubuntu which had some process essential for GRUB to operate properly.

---

### Post by zeroxorxdiexskater on 2008-07-06
well i was thinking this
i could make a new partition witht his cd and then just install ubuntu again and then uninstall ubuntu (properly)

---

### Post by Nikitas350 on 2008-07-06
Try to repair vista with vista installation disk...

---

### Post by zeroxorxdiexskater on 2008-07-06
> **Nikitas350 said:**
> Try to repair vista with vista installation disk...

first of all i dont have the installation disk because i got this computer with vista on it. and also i would lose all my stuff

---

### Post by Xerp on 2008-07-06
No, with a repair install of Vista you wouldn't lose any of your personal data.

---

### Post by unutbu on 2008-07-06
When you installed Ubuntu, you must have overwritten the MBR (Vista's bootloader) with GRUB. GRUB reads /boot/grub/menu.lst on your Ubuntu partition to boot your OSs. Now that Ubuntu has been deleted, GRUB is left hanging, because it can not find /boot/grub/menu.lst.

The cure for this is to re-install the Vista bootloader on the MBR. You are going to need some kind of rescue CD to do this. If your Ubuntu LiveCD allows you automatic internet access, then you could use it to download the SuperGRUB disk:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

which can restore your Windows MBR. This is the easiest way. 

As a second option, you can also download a Vista Recovery Disk. The instructions are here:
[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

You will also find much helpful information here:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by zeroxorxdiexskater on 2008-07-06
> **unutbu said:**
> When you installed Ubuntu, you must have overwritten the MBR (Vista's bootloader) with GRUB. GRUB reads /boot/grub/menu.lst on your Ubuntu partition to boot your OSs. Now that Ubuntu has been deleted, GRUB is left hanging, because it can not find /boot/grub/menu.lst.

The cure for this is to re-install the Vista bootloader on the MBR. You are going to need some kind of rescue CD to do this. If your Ubuntu LiveCD allows you automatic internet access, then you could use it to download the SuperGRUB disk:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

which can restore your Windows MBR. This is the easiest way. 

As a second option, you can also download a Vista Recovery Disk. The instructions are here:
[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

You will also find much helpful information here:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

ok how do i use super grub. i want to know sum info before i try it

---

### Post by bumanie on 2008-07-06
It is a simple graphical program that will have a menu such as 'fix boot of windows' or some such (can't remember the exact wording). It is very easy to follow.

---

### Post by zeroxorxdiexskater on 2008-07-06
ok well i burnt super grub on a cd and everytime i put it in it loads to the grub. even when i forcibly boot it to the cd rom drive it boots to the grub.

EDIT

please i would really like to know how to fix my grub. ive burnt multiple copies and it still boots to the grub and i get the error

---

### Post by zeroxorxdiexskater on 2008-07-06
BUMP
? its getting very late where i am and i would like to finish this before morning

---

### Post by cariboo on 2008-07-06
Using this:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

might be a lot easier for you.

Jim

---

### Post by zeroxorxdiexskater on 2008-07-06
i know how to do it...i just cant...
i know the problem
i have to burn the image at 8x speed or lower. but im using roxio to burn the image and i dont know how to burn an image on roxio. the closest thing is a data disc and i dont think that works. can someone tell me how to burn an image on roxio creator basic 9

---

### Post by zeroxorxdiexskater on 2008-07-07
does anyone know of a free cd burner that burns images and can burn at a speed of 8x or slower?

---

