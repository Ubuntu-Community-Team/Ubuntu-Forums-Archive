---
title: "upgraded from 7.10 to 8.04/dual boot grub error"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Mr Pockets151 on 2008-05-21
Well I started with the 7.10 Live CD.  Installed it on my IDE 250GB entire disk.  My XP partition is on the SATA 160GB drive.  Everything went smoothly.  Ubuntu detected the partition and added it to GRUB.  It rebooted tested the XP choice and it worked fine. 

I continued to update 7.10 with missing updates.  Rebooted and XP choice still worked fine.  

After updating I decided to "upgrade" to 8.04.  Now when I boot my PC, before reaching GRUB I get a "cd disk error...press any key to continue...."  When I press the key it goes to GRUB menu.  My ubuntu choice works, but now it doesn't want to boot to XP.  What happen?

---

### Post by logos34 on 2008-05-21
Post your /boot/grub/menu.lst and the output of

sudo fdisk -l

---

### Post by TeoBigusGeekus on 2008-05-21
Post us the output of 
```
sudo fdisk -l
```
(-L)
and the contents of your menu.lst file
```
gksudo gedit /boot/grub/menu.lst
```
(.LST)

---

### Post by Mr Pockets151 on 2008-05-21
Sorry, I'm a "dork!":lolflag:  I didn't notice that I had a USB stick in the damn machine.  So it was looking for something on an empty drive.  DUH!!!!  Everything works fine now.  THANKS FOR THE RESPONSES!!!!

---

