---
title: "unable to get usb hard drive listed under fdisk, unable to mount"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by drpalak on 2008-11-27
Hi, I just installed ubuntu 8.10 , just for one reason. I have western digital my book world edition 500 gb hard drive, that failed because of firmware problem. so i removed it from case and attached through SATA to USB cable, and attached to pc via usb. I installed ubuntu since my drive has ext3 file system, and all other means to get it read in win xp ( i tried ext3ifs, ext2ds, linux reader etc. ), failed. so, finally i got some idead from forums that installing ubuntu will help. now, i installed and in places>computer> its showing up as 'usb drive', unmounted, and unknown filesystem..unble to mount by right click.. i used terminal and typed 'sudo fdisk -l' but that drive is not listed in the screen output. that means, ubuntu is still not detecting? how can i fix this problem. I have very important information in the drive, about 150 gb. It is now showing up in system monitor either. I have screenshots taken of all these, attached to the thread. please help. thanks.

---

### Post by cdtech on 2008-11-27
So at one point was the drive ever bootable? What filesystem was it originally?

---

### Post by Bucky Ball on 2008-11-27
Your 'USB Drive Properties' screen shot is correct if this is a fat formatted drive.

---

### Post by drpalak on 2008-11-27
this drive is basically a NAS, i kept attached through ethernet to router, and i was able to access files anywhere in the world through meonet service. basically, what info i have, its a drive with a linux system installed in it, and ext3 file system. I don't remember, if file system was changed ever, so it should have ext3 only.

---

### Post by cdtech on 2008-11-27
Did you make sure the plug is set to master? USB uses only one detection line.

---

### Post by alwayshere on 2008-11-27
have you tried the " Hipo iPod Management Tool " 

look in add/remove

---

### Post by drpalak on 2008-11-27
NO, its ext3 system.. i didn't change it. ( is there any other way to know, which file system is there? ). when i checked with other win xp programs ( ext2ifs, etc. ) it was showing up as ext3 system. and it was not getting mounted,.

---

### Post by drpalak on 2008-11-27
how to check that plug is set to master? ( sorry, for being linux ignorant )

---

### Post by Bucky Ball on 2008-11-27
On the back of the actual drive is a block with about 8 metal pins and a plastic jumper covering two of them. On top of the drive is a diagram showing where to put this jumper to change the drive from 'master' to 'slave' and some have other options. Fingernails or tweezers are good for removing this jumper and changing it over.

If the drive is being picked up in windoze, I doubt this is your problem, though. :)

---

