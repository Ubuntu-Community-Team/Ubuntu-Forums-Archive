---
title: "Windows/Linux and common partition"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by natman on 2008-10-27
I will be doing a fresh install on laptop of Kubuntu8.10 at the moment its partitioned as NTFS ( win ) swap / and /home, but i would like to have another space for file that i need to access in windows also. Instead of using a program in windows to export ext3 stuff to to ntfs drive and ending up with duplications.
So do i just ask for a new partition but formatted as ntfs - will Kubuntu be able to read and write to it? what do i call the new partition /opt?/home2/usr?

Thanks

---

### Post by nhasian on 2008-10-27
yes you can read/write to NTFS paritions.  you can mount it anyplace you like.  i put mine in /media/home2 :)

---

### Post by natman on 2008-10-27
Cool thanks, but when i am doing the install and pick manual partition how do i go about making the extra one, is it logical/primary? and the mount point?

---

### Post by Paqman on 2008-10-27
You can only have up to four primary partitions. If you already have Win, Ubuntu /, /home and swap then you've already hit the max. You're going to have to create an extended partition to put any further partitions into. Unfortunately the extended counts as one of the four, so one of your current partitions will have to go into the extended partition as well. 

Since it's a fresh install that's not too much of a biggy. Presumably you're not touching /home during the install, so your options are to put / or swap into the new extended partition with your new NTFS partition.

As for mount points, you can choose anything you like. Anything you mount to a /media folder will show up on the desktop automatically. If you don't want that to happen mount it somewhere else, like /mnt.

---

