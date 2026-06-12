---
title: "Problem installing Ubuntu 13.04"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2013-04-26
Hi friends,

I am trying to install ubuntu 13.04. I already have Windows 8 + Pear Linux 7 Dual boot and now I wish to install Ubuntu 13.10 alongside these two. I have prepared Live USB with help of multisystem. When I run Installer it shows that some partition is mounted at /isodevice and ask for permission to unmount. I click continue. I proceed with "Something Else" option and try to create partition manually. In next installer shows error and tells me that partion is mounted at /isodevice. I run Disks program and try unmounting partition manually but program display error "Not Authorised". If I ask installer to continue it reaches next steps but stuck at "Detecting File Systems" steps. That step never ends. Can anyone please help. Sorry for wromg heading. I meant Ubuntu 13.04

Sujit

---

### Post by oldfred on 2013-04-26
I not not used Multisystem, but have suggested it for some that want to multi-boot ISO. But, I just use grub2 and copy ISO to a flash drive and manually maintain grub.cfg.

I always partition in advance with gparted either from liveCd (ISO) of Ubuntu or Parted Magic or gparted ISOs. I now have them on hard drive to boot as that is even faster than flash drive. 
What boot loader does Pear use? If grub2, it is not difficult to create a /iso folder in Pear and use grub to boot ISO from that. But it should not be in mounted partition or if logical the extended will also be mounted.
       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

When I installed 13.04 from ISO, it did have a lockup on partitioning. I was in live mode, and clicked on install from that.  I have lots of partitions so it normally takes a while, but it was too long. I was able to back out and reran it not expecting it to work but it did and was fairly quick at finding my partitions.

---

