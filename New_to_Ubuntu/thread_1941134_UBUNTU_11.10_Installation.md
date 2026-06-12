---
title: "UBUNTU 11.10 Installation"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by AnupamMitra on 2012-03-15
My OS is WINDOWS XP SP 3. I installed UBUNTU 11.10 from a CD which was prepared through ISO Image. Incidentally, I am having two Hard Disks – “C” Drive is in the old Hard Disk, but the WINDOWS is in “J” Drive located in New Hard Disk. Now, UBUNTU 11.10 was installed in “J” Drive. Proper installation was done. Thereafter I was asked to reboot the system. That was also done but after rebooting I’m not getting any option to open UBUNTU. Straightway WINDOWS is opening. Please help.

---

### Post by sp-1070 on 2012-03-15
Hey

So the best option would be to start from a live disc or usb and install the grub loader because windows does not like to share -at all-

---

### Post by raja.genupula on 2012-03-15
yes reinstall grub (Grub recovery in my signature) .

if that wont help then please post the output of bootinfoscript by booting with a LIVE CD  . 

Thank you :)

---

### Post by JC Cheloven on 2012-03-15
You probably accepted (which I think is) the default, and installed the grub2 bootloader in the second disk, the one in which ubuntu was installed as well. This is not suitable for you, as your bios looks for booting from your 1st disk, and finds there everything it needs (the windows bootloader and the windows system). The grub2 boot loader should have been placed in that first disk.

To fix the problem, please refer to [this guide]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2"). Your disks will probably be /dev/sda1 (your xp disk), and /dev/sdb1 (your new disk with ubuntu), but we can't be sure without more information. Pease check yourserf by runing at a terminal ```
sudo fdisk -l
``` from the live session (eventually post here the output if you need help at this)
Your goal should be to install grub in your first (windows) disk.

Alternatively, you may set up your bios to boot from the second drive (I think it should work straight away, but not 100% sure; you loose little by trying anyway).

Hope that helps
JC

---

### Post by AnupamMitra on 2012-04-14
Thanks to all. Problem is solved with the help of all of you.

---

