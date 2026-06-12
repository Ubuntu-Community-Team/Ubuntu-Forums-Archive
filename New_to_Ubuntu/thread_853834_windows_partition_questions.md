---
title: "windows partition questions"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by jclu on 2008-07-08
Hi, I currently have a WinXP installation, and I want to dual-boot with (most likely) Ubuntu. I've had dual-boot setups running in the past, but they were years ago, so I wanted to get some help on a few questions I had in regard to how to setup a dual-boot system.

1) How do I resize an existing FAT32 partition and not lose any data? Here's my comp setup:
hda - 160GB
 hda1 - 20.1GB FAT32 - "C:" - ~3GB free
 hda2 (logical partition) - 132.5GB FAT32 - "D:" - ~75GB free
hdb - 30GB
 hdb1 - 27GB FAT32 - "E:" - ~14GB free

*D and E are data partitions; the 160GB is a newer drive, hence it contains my C and the bigger data partition; the numbers actually add up, I just rounded up for the hd sizes and used the exact sizes for the partitions

Now, I have software to resize a fat32 partition, but I'm not sure if I can just go ahead and shrink the fat32 partition. The software I have is Ranish Partition Manager, which doesn't work from within Windows but straight at the sectors level. Because of this, if I just shrink the partition(s) I want to shrink, I'm afraid of losing sectors that have data on them. From what I remember I think I need to make sure all the data is at the beginning of the partition. Is that correct? If so, how do I do that? Will defragmenting do the job?

2) What is the current status with Linux and NTFS partitions? I have these three as FAT32 because when I had a dual-boot before, NTFS support in Linux wasn't 100% yet, so I stuck with FAT32. I know that if I wanted to convert my FAT32 partitions to NTFS, I would have to back up the data because it will overwrite it, but I could do that fairly easily. I want to know if Linux has 100% NTFS support, in which case, I'd probably convert at least my C over to NTFS and maybe D and E.


Thanks for any help you can provide. If anything is unclear, ask, and I'll try to answer as best as I can.

---

### Post by ChameleonDave on 2008-07-08
To resize partitions, use GParted.  It will handle everything.  If there is a lot of data on the partition, or if it is in a bothersome location, then it will take hours, but it will do it.

Linux support for NTFS has progressed greatly, and some people use NTFS on Linux all the time.  However, support can never be 100% whilst NTFS remains a Microsoft trade secret.  I always advise against it.  I use an Ext3 partition as a data partition for Linux and XP.  There are drivers available for XP to recognise it.

---

### Post by mcduck on 2008-07-09
Just run a defrag to the partition you want to resize. I suggest doing it in safe mode. After that Ubuntu's installer is able to do the resizing for you. :)

---

### Post by indytim on 2008-07-09
Another thing to consider as you work your way through partition-related activities.... might want to consider going the ext3 route on future data partitions.  There is a driver for the windows side that readily recognizes (and mounts) ext3 partitions in Windows.  I personally use it to mount 3 different ext3 partitions when I'm forced to work in a Windows environment (multi-media apps with no equivalent in Lx-Land).  Here's the link if you're interested:
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

A word of caution : If you convert an existing FAT32 formatted partition to ext3, YOU WILL LOOSE ALL OF YOUR FAT32 DATA.

IndyTim

---

### Post by DezSP on 2008-07-09
> **ChameleonDave said:**
> Linux support for NTFS has progressed greatly, and some people use NTFS on Linux all the time.  However, support can never be 100% whilst NTFS remains a Microsoft trade secret.  I always advise against it.  I use an Ext3 partition as a data partition for Linux and XP.  There are drivers available for XP to recognise it.

I wouldn't say NTFS support in Linux is any worse than EXT3 support in Windows nowadays. They're both very stable.

---

### Post by rogier.de.groot on 2008-07-09
AFAIK there's ext2 support for Windows, not ext3, but it's forwards-compatible so you can use ext3 partitions with the ext2 IFS driver. It'll just not use the journaling stuff that's in ext3 - maybe Ubuntu will complain about that from time to time.
I use NTFS partitions for data; Ubuntu support for it rocks nowadays.
The partitioner (gparted) on the live cd does indeed resize NTFS (and presumably FAT32 as well) partitions just fine, in my experience anyway.

---

### Post by ChameleonDave on 2008-07-09
> **DezSP said:**
> I wouldn't say NTFS support in Linux is any worse than EXT3 support in Windows nowadays. They're both very stable.

Indeed.  I'm working on the assumption that the first priority is that it must work on Linux, and the second priority is that it work when Windows is used for the occasional legacy app.

---

### Post by jclu on 2008-07-09
I guess I have a few options then (ie, use NTFS, ext3, etc)! I guess the next step is to figure out how many ext3 partitions I want, and how big they should be. From what I remember, a minimum of 2 ext3 partitions, and 1 swap should be fine? The 2 ext3 partitions would be / and /home.

Slightly OT, but related to my dual-boot plans: has anyone here installed UbuntuStudio? If so, what sort of partition structure should I try - perhaps the same as above? And what partition sizes should I be looking at?

Thanks again.

---

