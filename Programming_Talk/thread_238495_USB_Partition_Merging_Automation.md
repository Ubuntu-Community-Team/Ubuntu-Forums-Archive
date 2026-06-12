---
title: "USB Partition Merging Automation"
date: 2006-08-17
forum: Programming Talk
---

### Post by nroussi on 2006-08-17
Hi all,
I am trying to develop an automated way to repartition and format USB drives using FAT for all USB drives that I insert into my machine. Ok, this is how the process goes:
I insert multiple drives into a USB hub, then using df I read all the mounted devices on the computer. Then, I dump the output and using awk I get the device names and save them into a list. Using a shell loop I specify what files I need copied and it copies them all on the devices. Now there is a problem since some USB drives come with 2 partitions, one being formated in CDFS and the other in FAT. Is there a way to erase the whole USB flash drive, and repartition it as FAT? I tried fdisk but it tells me that the device is busy. Also, fdisk needs some user input and I need it to be automated.
As always, any help is very much appreciated.
Thanks.

---

### Post by jeffnt on 2006-08-18
If the partation is CDFS, you can not erase it through fdisk because CDFS is read-only. there are some special configuration if the disk is multi-partition. you should get vendor support to do it.

---

### Post by mikimiki on 2008-04-23
Sorry for my english. 

The fact is I´ve achieved merging both partitions (public & CDFS) into one single partition, but... on Win Xp, I´m afraid. 

UDFUtility.exe (RapidShare, aeg.) allows you to configure your USB´s autoboot, really detects both partitions and -most important- REALLY merges them into a single volume -a public one, I mean. No matter what kind of autobootable USB you plug in (U3, USBest, etc).

It works!

I hope this can be useful -though it ain´t much ubuntunian...

Salud!

---

