---
title: "How to change the GRUB OS Order"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by meadhikari on 2011-10-19
I have 9.10 in one partition and 11.10 in another
GRUB shows 9.10 as the primary(at the first and also has (recovery mode)) while ubuntu 11.10 is shown at the last after mem86+ like
Ubuntu 11.10(/dev/sda1)

I can not find the menu.lst as most tutorial talk about and believe it has been depreciated in GRUB2 and the automatic no manual editing grub.cfg is to be used.

I tried to update-grub from my 11.10 but also it is still the last one in the menu.

Thanks for your time.

---

### Post by computerandu on 2011-10-19
This might be helpful for you:

[http://www.computerandyou.net/2011/08/19/how-to-change-the-default-boot-order-in-grub-2-in-ubuntu-10-04-10-10-and-11-04/](http://www.computerandyou.net/2011/08/19/how-to-change-the-default-boot-order-in-grub-2-in-ubuntu-10-04-10-10-and-11-04/)

---

### Post by oldfred on 2011-10-19
If 9.10 is first you are booting with 9.10's grub2 boot loader in the MBR. Do you have more than one drive? If so you 11.10 grub may have just installed to sda. You can just install your new grub to the MBR with this:

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Grub legacy with 9.04 and before used the menu.lst. Some who upgrade may still have grub legacy & a few still boot with it.

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
/etc/default/grub

---

### Post by meadhikari on 2011-10-19
Thanks It helped.

---

