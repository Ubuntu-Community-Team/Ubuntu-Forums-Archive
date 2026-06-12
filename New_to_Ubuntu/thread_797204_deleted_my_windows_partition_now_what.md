---
title: "deleted my windows partition now what?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-05-17
i want to increase my hard disk space but i cant get gparted to increase the size of my ubuntu partition any way i can do that  without having to wipe my entire disk

---

### Post by plucky on 2008-05-17
> deleted my windows partition now what?

Assuming your windows partition was at the beginning of the disk,Gparted can only extend a partition from the rear end of the partition.

It can however move the start of the partition,so you can move the start of your Ubuntu partition to fill the empty space when you deleted the windows partition.**(Moving the start of a partition can take a very long time if the partition is large and has a lot of data)**.

After the partition has moved,you can now extend it to take up the space that the move created at the backend of the partition.

Also deleting and moving partitions will change UUID's and partition numbers,which can cause problems with booting and mounting,so I hope you have made backups of your important data.

Hope this helps

Good Luck

---

### Post by HotShotDJ on 2008-05-17
> **PatrickMoore said:**
> i want to increase my hard disk space but i cant get gparted to increase the size of my ubuntu partition any way i can do that  without having to wipe my entire diskYou cannot make changes to a partition that is mounted.  So, if you tried to expand your Ubuntu partion into the free space while running Ubuntu from your hard drive, it will fail.  You'll need to boot to a LiveCD (your installation CD should do nicely).  Be prepared, it takes HOURS & HOURS to grow a partition.  If you have a USB hard drive that you can use to backup your important files, you might be better off just doing a reinstall using the entire harddrive.

---

### Post by PatrickMoore on 2008-05-17
oh my ubuntu partition is at the front of the disk and my swap file is at the end. so  i have about 25gb of unallocated space in the middle any suggestions of a backup disc creator?

---

### Post by Xiong Chiamiov on 2008-05-17
Personally, I use [partimage]("http://www.partimage.org/Main_Page"), since it allows me to back up my entire partition across the network, then easily put it back after rearranging things.  I'd make sure you have a copy of [SuperGrubDisk]("http://supergrubdisk.org") on hand, as well as the Ubuntu disk, just in case you need it.

---

### Post by forestpixie on 2008-05-17
> Be prepared, it takes HOURS & HOURS to grow a partitionIt can in fact take days, which can be a bit worrying, dpepnds on size of partitions.

It might also are trying to add space from a primary to an logical partition - it has to be in the extended before you can add it to the logical.

Might I ask what you want to do with the space - is there a pressing reason to add it to your install - it's easy enough to change type - ntfs to ext3 and add the partition to fstab so it mounts as storage space.

---

### Post by Crossroads on 2008-05-17
Could you just create a new ext3 partition of 25 GB then assign a mount point to it? You'll need to boot from a LiveCD.

That way you end up with three paritions / (root), (swap) and one other.

{as forestpixie said in his last sentence}

---

### Post by forestpixie on 2008-05-17
If it's not mounted and doesn't exist you can do that within ubuntu

---

### Post by mixtri on 2008-05-17
Hi Guys I have a similar problem. I have two hard-disks daisy chained. Disk 1 has ubuntu and disk 2 had windowsx xp which i dual booted.
I deleted the windows OS off disk 2 as Today is the day I decided to purge my machine of Microsoft windows.

I used to be able to access the ntfs partition of windows from within ubuntu.

Since removing windows, creating a new partition and reformatting disk 2 to the ext3 filessystem, I have been unable to mount the disk even though ubuntu recognises it. I have tried mounting with root privileges i get the following console message - 

albert@albert-desktop:~$ sudo mount /dev/sdb1
[sudo] password for albert: 
mount: mount point /media/Windows does not exist

I want to use this disk for backup purposes and need to transfer some files before a fresh install of ubuntu.
Thanks

---

