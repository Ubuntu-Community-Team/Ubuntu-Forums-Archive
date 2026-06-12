---
title: "Problems with Partitions"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by !ndy on 2008-08-10
hi there,

i have been fighting with hardy for 3 days already...
probably i have the most unfortunate HP laptop (its series g6000) for linux... you know, vista preinstalled i threw it away in 2 days)

i've fixed this until now and i didnt want to bother you with things i was able to google--->
 - broadcom wireless, oh yeah... blacklisting and ndiswrapper. to get it working, i had to use actual winxp bcmwl.inf & .sys files, linux tarred drivers some guys mentioned just did not work
 - geforce go 6100 drivers problem (drivers provided with hardy 8.04.1 were no good and i finally got it working (freezes every 20 minutes, etc., weird horizontal lines at logout, weird green-blue graphics at some splashup screen)

but still, i am having those problems with hard drive:
 - Partition table entries are not in disk order
 - sometimes HDD just freezes, when i am watching movies from /media/disk (my dual-boot winXP)

okay, to the core...
possibly, it can be a matter from the installation. when i was installing ubuntu for the first time, i just got some I/O error at 61% and that was it --- my laptop has restarted and and had to boot to winXP to download it again. 
(the image got corrupted during the download (md5sums did not agree) - i checked it later)
so i was trying to install it again, but i could not use the partitioning guide again --- because it offered me to cut another gigabytes from windows NTFS partition. and i already had these 15 GB missing from old NTFS partition.
so i tried manual partitioning, i just remeber, that i just marked the old ubuntu partition (the one from corrupted installation) for formatting, put / for root and kept the swap file and installed ubuntu

now, i was looking at the hard drive issues, because it's not so great, when my SATA HDD is just rotating in some weird way (computer is frozen forever and harddrive is just moving constantly and it's making sounds like if it was hurt - really ;-))  

so i read about this:
cat /etc/fstab
sudo fdisk -l

and i have seen some errors "relatime,errors something" and this error with partitions not in correct order.
you know, i hate playing with partitions and editing GRUB or what should i do, so, please, tell me what is safe to do. 

here is the ouput;
1.
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=f79b1513-6347-41b3-96b5-314e1275b08f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=37037930-4f98-4c81-a61f-1a2c26a71eda none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

2.
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe29e4c96
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8120    65223868+   7  HPFS/NTFS
/dev/sda2            8121        9729    12924292+   5  Extended
/dev/sda5            9656        9729      594373+  82  Linux swap / Solaris
/dev/sda6            8121        9655    12329824+  83  Linux
Partition table entries are not in disk order


what do you thing?
there is something wrong... isnt it? :-)
and what do you thing about the SATA drivers - can there be also something wrong - i mean, when i use NTFS windows drive under ubuntu, it is somtimes doing troubles.

you know, i like ubuntu and the opensource and community spirit, but i am getting tired :-(
fortunately, wlan and gpu is working :-)

one last thing that came on my mind:
is there any powerful PC HW Diagnostic Tool, such as Sandra or Everest in Win? 

sorry for such exhausting post.
thanks in advance!

---

### Post by Pro-reason on 2008-08-10
I found that post a little hard to understand.  I'm not sure whether you successfully installed Ubuntu or not.  What is that fstab file from, the live CD or a successfully installed system?

This guide might be helpful in terms of understanding the different ways in which fstab can refer to devices: [https://help.ubuntu.com/community/MountDevicesTroubleshooting](https://help.ubuntu.com/community/MountDevicesTroubleshooting)

---

### Post by nicedude on 2008-08-11
If I were you I would live boot either an Ubuntu CD or a Gparted live CD and delete all the partitions but your XP and then resize the 65GB XP partition to something like 15-25GB ( Depends on how much stuff you have there ) and then apply it all and wait as will take awhile to resixe the NTFS XP partition. Now reboot the PC to your Ubuntu install disk so that the disk partition tables are properly updated and at this point you will only have /dev/sda1 15-25GB NTFS. Now install Ubuntu and when you get to partitioning choose manual again and add 1 or 2GB ( supposed to be twice the RAM you have but I use 1X my RAM and it works fine ) partition formated as SWAP ( this will be your Linux swap file space ), next do a partition of 15-25GB for Ubuntu formated as EXT3 with a mount point of / , Finally you can format the remainder of your disk space as a data storage container for you to store all your video, audio & other documents etc. this can be formatted as FAT32 or NTFS so both XP & Ubuntu can access it easily. When your done with the install you will be able to boot either OS and still have a large data storage area accessible easily from both.


You would end up with a device list like this, which is much cleaner in my opinion.

/dev/sda1 - XP
/dev/sda2 - Linux swap
/dev/sda3 - Linux System
/dev/sda4 - Data Storage

Hope this helps you out on what to do and how to do it.

nicedude

---

### Post by !ndy on 2008-08-11
**one more question at the bottom of my post**

thanks guys...

anyway, i have decided that i want to do a format and that's it...
since i was a windows power user for a looong time (since win 3.11) I know, that there are some problems, when it's better to format than look for errors and spend hours and hours :-)

so, now it's working.
like this:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8120    65223868+   7  HPFS/NTFS
/dev/sda2            8121        9667    12426277+  83  Linux
/dev/sda3            9668        9729      498015   82  Linux swap / Solaris


i regret, that i did not read your recommendations.
no i have swap 512mB and it is sda3, not sda2 as you said it should be... but it's luckily working fine. 
i will see, if the disk gets frozen under heavy acctivity. i will put him under a small test :-)
and i also did not understand, whether swap should be primary or logical?
about the data storage partition, it should be logical, no? but swap?
i have it primary.

thank you so much for trying to help me. 
i appreciate your work, since i saw a lot of activity on the beginners forum and i would not have nerves to read all that sometimes;-)

---

