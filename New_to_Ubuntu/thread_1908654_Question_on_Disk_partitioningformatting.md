---
title: "Question on Disk partitioning/formatting"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by jrbrooks on 2012-01-13
I now have a duel boot system with 3 physical hard drives. 
Two (80GB and 500GB)came with the original PC with a Windows operating system. The Windows OS was loaded on the 80GB disk as the C: drive. The other disk has two NTFS partitions.
Later I installed a 1TB hard disk. I _cannot_ remember whether I had already converted to duel-boot Ubuntu before I installed the new hard disk.
However my problem is that the 1TB hard disk is partitioned in a strange way viz
1. /dev/sdc1 NTFS 500 GB
2. /dev/sdc2 Extended Partion 500 GB.  This is subdivided into:
3. /dev/sdc5/ EXT4 490 GB
4. /dev/sdc6/ Linux Swap Space 9.6 GB

My problem is that I have lost 490 GB of useable disk space! All this disk space seems to have been grabbed by Ubuntu along with the 9.6 GB that it actually needs. I want to format the 490 GB (item 3 above) to NTFS.
How do I do this? The Disk Utility would not allow me to do it.

---

### Post by nipunshakya on 2012-01-14
Give a shot from the Disk management tool in windows. Even though u don't see any label of your partitions, u can pretty much format the 490gb u want(if u wish to throw any data from it.)

Regards,WinuxUser

---

### Post by kc1di on 2012-01-14
> **jrbrooks said:**
> I now have a duel boot system with 3 physical hard drives. 
Two (80GB and 500GB)came with the original PC with a Windows operating system. The Windows OS was loaded on the 80GB disk as the C: drive. The other disk has two NTFS partitions.
Later I installed a 1TB hard disk. I _cannot_ remember whether I had already converted to duel-boot Ubuntu before I installed the new hard disk.
However my problem is that the 1TB hard disk is partitioned in a strange way viz
1. /dev/sdc1 NTFS 500 GB
2. /dev/sdc2 Extended Partion 500 GB.  This is subdivided into:
3. /dev/sdc5/ EXT4 490 GB
4. /dev/sdc6/ Linux Swap Space 9.6 GB

My problem is that I have lost 490 GB of useable disk space! All this disk space seems to have been grabbed by Ubuntu along with the 9.6 GB that it actually needs. I want to format the 490 GB (item 3 above) to NTFS.
How do I do this? The Disk Utility would not allow me to do it.

You haven't lost the space -Windows simply will not see EXT4 file systems or any file system formatted to a linux partition. There are programs that will make it possible for windows to see and even write to ext filesystems. (you can do a google search for that if interested)
As far as repartitioning your H.D. I would go to distrowatch look for a distro called gparted or parted magic either one will do download it and burn the iso to a cd or usb stick. boot into gparted.  you are going to loose Ubuntu when you do this and will have to reinstall later.**[COLOR="Red"](SO MAKE SURE YOU BACK UP ANY FILES YOU WANT!)[/COLOR]**

Now you can repartition that drive any way you want. But if you want Ubuntu install I would make the follow linux partions  10 GB for / (Root Partition) 2 GB  for linux swap  and say at least 100gb for a /home partition  then partition the rest to NTFS if you like. 

now when you reinstall Ubuntu it's important that when the installer come to the partition screen you select Something else and manually select the partions for / and /home.
Good Luck BE CAREFUL you can easily erase your windows install with this if your not careful!

---

### Post by insane_alien on 2012-01-14
by right clicking on 'My Computer' and selecting manage there should be a disk utility in the 'storage' section that will allow you to remove the linux partitions (this will wipe all data within those partitions) and you can then expand the ntfs partition (or create a new one if you want) to fill the now empty space.

Windows does not currently have an ext4 driver and so can't read ext4 filesystems. one could be made but it hasn't happened yet.

Linux can use ntfs though.

sorry to see you leave linux.

---

### Post by nipunshakya on 2012-01-14
> **kc1di said:**
> You haven't lost the space -Windows simply will not see EXT4 file systems or any file system formatted to a linux partition. There are programs that will make it possible for windows to see and even write to ext filesystems. (you can do a google search for that if interested)
As far as repartitioning your H.D. I would go to distrowatch look for a distro called gparted or parted magic either one will do download it and burn the iso to a cd or usb stick. boot into gparted.  you are going to loose Ubuntu when you do this and will have to reinstall later.**[COLOR=Red](SO MAKE SURE YOU BACK UP ANY FILES YOU WANT!)[/COLOR]**

Why do such a big pain when the OP has clearly said that he wants to remove the 490gb and format it as NTFS ?> **jrbrooks said:**
>  I want to format the 490 GB (item 3 above) to NTFS.
How do I do this? 

> **kc1di said:**
> Now you can repartition that drive any way you want. But if you want Ubuntu install I would make the follow linux partions  10 GB for / (Root Partition) 2 GB  for linux swap  and say at least 100gb for a /home partition  then partition the rest to NTFS if you like. 

now when you reinstall Ubuntu it's important that when the installer come to the partition screen you select Something else and manually select the partions for / and /home.
Good Luck BE CAREFUL you can easily erase your windows install with this if your not careful!


I'd very much like to add a question here for myself. For instance, one has to run the following on an ubuntu pc:
visual studio similar (maybe mono) , mysql, some 3d graphics editor, and few other stuffs like that. Then, will 10 gb be enough for / partition? 

Thanks, WinuxUser

---

### Post by kc1di on 2012-01-14
> **WinuxUser said:**
> 




I'd very much like to add a question here for myself. For instance, one has to run the following on an ubuntu pc:
visual studio similar (maybe mono) , mysql, some 3d graphics editor, and few other stuffs like that. Then, will 10 gb be enough for / partition? 

Thanks, WinuxUser

I might up that to 12 GB in that case with a separate /home partition most of those files can be store there only the actual file and libs for the program will reside in the / partition

---

### Post by nipunshakya on 2012-01-14
Thanks..

---

### Post by varunendra on 2012-01-15
> **jrbrooks said:**
> I want to format the 490 GB (item 3 above) to NTFS.
How do I do this? The Disk Utility would not allow me to do it.
If you have the installation CD that you used to install ubuntu from (or any ubuntu live cd for that matter, it will already have gparted on it. Boot from it, open gparted and do whatever you want to do with the partition(s) (shrink, move, delete, format,...etc.). The current Disk utility or even gparted running on the installed ubuntu won't let you do this because they will require you to 'unmount' the partition first (which you can't while running Ubuntu from the same partition!).

**BE CAUTIOUS!:**
If you want to completely remove ubuntu and make your system Windows-only, you may have to restore windows MBR on your boot partition. Because it must have surely been overwritten with Grub during Ubuntu installation. As such, You WON't BE ABLE TO BOOT WINDOWS after removing Ubuntu!

**_Options_:**
Option 1: Either make sure you have the installation CD/DVD for your Windows installation which you'll be using to restore MBR after removing Ubuntu,

or

Option 2 (recommended): Just use gparted from the live cd to shrink the Ubuntu partition, and create a new ntfs partition in the obtained space. With so much space, it won't hurt to leave 20-40 GB for Ubuntu. On the contrary, it may actually be very useful in case some day Windows gets corrupt or infected by some virus.

Also, if you decide to keep Ubuntu and are not going to use its 'Hibernation' feature, then 2 GB swap space would be more than enough.

If you have any more questions, just ask and we're eager to help!

---

### Post by mcduck on 2012-01-15
> **jrbrooks said:**
> I now have a duel boot system with 3 physical hard drives. 
Two (80GB and 500GB)came with the original PC with a Windows operating system. The Windows OS was loaded on the 80GB disk as the C: drive. The other disk has two NTFS partitions.
Later I installed a 1TB hard disk. I _cannot_ remember whether I had already converted to duel-boot Ubuntu before I installed the new hard disk.
However my problem is that the 1TB hard disk is partitioned in a strange way viz
1. /dev/sdc1 NTFS 500 GB
2. /dev/sdc2 Extended Partion 500 GB.  This is subdivided into:
3. /dev/sdc5/ EXT4 490 GB
4. /dev/sdc6/ Linux Swap Space 9.6 GB

My problem is that I have lost 490 GB of useable disk space! All this disk space seems to have been grabbed by Ubuntu along with the 9.6 GB that it actually needs. I want to format the 490 GB (item 3 above) to NTFS.
How do I do this? The Disk Utility would not allow me to do it.
Your disc is actually partioned in perfectly normal way. You have a 500GB Windows partition, and a 490GB partition for your Ubuntu system.

I just wanted to confirm, do you actually want to keep it as a dual-boot system with Windows and Ubuntu, or do you want to get rid of Ubuntu and only use Windows (as that's what formatting your 490GB Linux partition to NTFS would mean)?

Or do you mean that you'd want a dual-boot, but with less space available for Ubuntu and more for Windows than what you currently have? In that case you should be able to shrink the sdc5 partition a bit and create a new NTFS partition to the empty space. (You *can* also add the space back to sdc1, but since it's outside of the extended partition you'd first need to shrink and move sdc5 and then shrink sdc2 to get the free space next to sdc1...)

THe 9,6GB partition is a swap partition, similar concept to paging file in Windows. It's not where your Ubuntu system is installed, it's just used to allow the Linux to handle larger amounts of data than what would fit in your computer's RAM, and to store the data from RAM when you hibernate the computer.

And the 500GB extended partition of course doesn't use any space on the disc, it's just a container for sdc5 and sdc6 partitions.

---

### Post by jrbrooks on 2012-01-15
I down-loaded GPARTED , burnt it to a CD and booted from the GPARTED disk. I could easily achieve what I wanted. I realised that Ubuntu was hosted on the 1TB disk and it had grabbed 500 GB of space. Apart from the 10 GB of swap space Ubuntu was using 29 GB of the available space
I resized the space to 50 GB which released the remaining 400+GB. This procedure took about 3 hours.
On re-starting, Ubuntu I formatted the the new space to NTFS.
Windows seemed to complain a bit, requiring a couple of re-starts.

btw I am using NTFS for all my data files as Windows "likes" it. To date I have had no problems reading and writing to the same files from either Windows or Ubuntu.
Should I be using/doing something else? 
I find I have to use Windows for things like printing, ITunes and, at the moment, I cannot get the TP-Link USB Wireless to work in Ubuntu 

Thanks for the helpful suggestions.

---

### Post by varunendra on 2012-01-15
Great job!

> **jrbrooks said:**
> btw I am using NTFS for all my data files as Windows "likes" it. To date I have had no problems reading and writing to the same files from either Windows or Ubuntu.
Should I be using/doing something else?
No, you are doing exactly what is needed to be done. For the other problems regarding iTunes/wireless/.... please start separate threads with relevant topics, and mark this one as [solved] as it is.


**_PS_:**
As a side note, it is the best practice to simply move as much data as possible 'out of the partition' which you are going to resize/move, preferably on a different physical media (another hdd for example). It not only serves as a backup, but also dramatically reduces the time required to move/resize the partition.

As gparted must have already cautioned you - ALL partition manipulation operations have the potential to completely destroy the data on the subject partition/drive (regardless of what tool you are using).

---

