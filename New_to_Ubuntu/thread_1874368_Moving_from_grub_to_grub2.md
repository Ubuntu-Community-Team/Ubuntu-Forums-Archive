---
title: "Moving from grub to grub2"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by rng on 2011-11-02
I use grub legacy and want to change to grub2. How can I do the following: 

My hard disk has 3 partitions: sda1 (having windows7) and 2 empty partitions which are sda2 and sda5 (both ext4). I boot with ubuntu livecd. How do I install grub2 on mbr with grub2 files on sda5 in folder /boot/grub? Also can I also install grub2 on partition boot sector of sda5?

Thanks for your help.

---

### Post by oldfred on 2011-11-03
Normally you install grub2 as part of an Ubuntu install. One of the best parts of new grub2 with an install is the os-prober. On a sudo update-grub it finds just about everything, where old grub even had issues finding Windows.

But grub2 can be used stand alone but requires you to manually build grub.cfg which is similar to editing grub legacies menu.lst but format is different. 

Grub2 does not like to be installed to a partition. It is larger than grub legacy and has to use block lists which are hard coded addresses for the rest of grub to load. If those files get moved on an update then you have to reinstall grub to the PBR.

What are you planning on booting besides Windows?

Herman has info on both grub & grub2 partitions
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition")
Chainbooting grub2, install to partition & Make CD or floppy - saikee
[http://www.justlinux.com/forum/showthread.php?threadid=152790](http://www.justlinux.com/forum/showthread.php?threadid=152790)
Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub2 partition discussion:
[http://ubuntuforums.org/showthread.php?t=1465772](http://ubuntuforums.org/showthread.php?t=1465772)

I boot my USB flash drives with grub2, so I do install it directly to the flash drive whether FAT32, NTFS or any Linux format. But I then create the grub.cfg to boot ISOs, my hard drives installs (as backup way to boot) or even Windows.

grub2-------------------------------------------------------
General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by rng on 2011-11-03
Thanks Oldfred. Could you please tell me stepwise how to install grub2 to usb flashdrive as you have done. What are the exact commands?

---

### Post by oldfred on 2011-11-03
See Herman's guide above and these links. I think you have to be running Ubuntu or use LiveCD.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

sudo grub-install --root-directory=/media/grub2 /dev/sdX # where X is drive that is the USB drive. Double check that it is the correct drive.

Then create a grub.cfg file with a grub2 boot stanza.
[http://ubuntuforums.org/showthread.php?t=1757395](http://ubuntuforums.org/showthread.php?t=1757395)

A full install with a distribution has this:

 GRUB 2 - GRand Unified Bootloader has three main parts plus a boot loader installed to the MBR:
   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

A grub only partition will just have th /boot/grub files and usually is missing the grub.cfg since the scripts are not there to create it.

---

### Post by rng on 2011-11-03
How important are /etc/default/grub file and /etc/grub.d/ folder, because I want to have on usb flash drive only grub and iso files. Is it possible?

---

### Post by oldfred on 2011-11-03
If you install to a grub only partition like the flash drive, then you do not get the scripts, and configuration file. That is why you have to manually create the grub.cfg. Once you understand the grub.cfg which is somewhat different than the old menu.lst it is not difficult. 

The links above show many examples but some ISOs do not boot directly from grub, the ISO has to be designed to be bootable. For Puppy I had to extract the boot files and in effect just run Puppy as an install from the flash drive. It is so tiny that still works. The Ubuntu distributions all boot from grub2 as an ISO. Startup is a bit different as it just loads the liveCD. I think additional parameters on the grub.cfg may give the 'normal' CD boot menu.

I find it even quicker to have another primary partition with the ISO on a hard drive and install from that. When installing from one drive to another that way the install is very quick.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by rng on 2011-11-03
> I find it even quicker to have another primary partition with the ISO on  a hard drive and install from that. When installing from one drive to  another that way the install is very quick.Can you please explain briefly how I can install from iso without burning it to a cd ?

---

### Post by oldfred on 2011-11-03
You must not have gone to drs305's detailed instructions posted above. That explains everything.

---

### Post by rng on 2011-11-03
So I boot from iso file placed on hard disk with grub2 and then install it. Thanks oldfred.

---

### Post by rng on 2011-11-12
I have gone through various links of grub2 installation. I am trying to install grub2 on a usb flash pendrive (one partition only: sdb1, ext2 format). I have made a folder /boot/grub/ on flash drive and copied to it files from /boot/grub/ folder of ubuntu installed on hard disk. Now from command line, I want to install grub2 to sdb (flashdrive). Which of following commands (suggested in different links) should I use from terminal (flash drive is mounted on /media/sdb1): 

$ sudo grub-install --root-directory=/media/sdb1  /dev/sdb

$ sudo grub-install --boot-directory=/media/sdb1/boot/  /dev/sdb     #note boot, not root

$ sudo grub-setup -d /media/sdb1/boot/grub /dev/sdb

Or will all of them work?

---

### Post by oldfred on 2011-11-12
I used the first, but that was before version 1.99.  With version 1.99 they changed to boot from root and modified the commands slightly. Supposedly the old command still works, but I have not tried installing 1.99 to a flash drive yet.

With commands like that, I would just try and see if it gets installed. And then copy a basic grub.cfg to /boot/grub and see if it boots to a grub menu. Takes about 5 minutes to test.

---

### Post by rng on 2011-11-13
Thanks oldfred, for being around and helping us.  I will try as you suggested.  

One more question: If I boot from ubuntu livecd with usb flash drive inserted, press 'c' at grub menu to go to commandline, can I install grub2 to flash drive (which already has files in /boot/grub/ folder) from grub commandline prompt? What will be the command?

---

### Post by oldfred on 2011-11-13
Grub has very little command line capability. I do not think from the grub boot menu you can do much other than manually boot a system.

---

### Post by rng on 2011-11-13
One last question on this topic. What will be a basic grub.cfg for grub2?

---

### Post by oldfred on 2011-11-13
It depends on what you want to boot. Often you can start by copying a boot stanza from a grub.cfg that the os-prober created. Or find similar boot stanzas on various sites. 

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

Attached is one of mine, but it has to be named grub.cfg. 
Edit - noticed a typo or two. Several comments are missing # and I know one or more of my gparted stanzas do not work as I was try alternatives.

---

### Post by rng on 2011-11-14
Thanks.

---

