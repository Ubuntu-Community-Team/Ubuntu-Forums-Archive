---
title: "Unable to mount ntfs drive"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by mwsisme on 2014-04-06
Hi!

Ealier on this evening, one of my wd external drives failed. Suspecting it was a power issue rather than the disk itself, I have removed it from its case and wired it up via SATA instead of usb. I can see it now in gparted and disks, but I can't for the life of me get it to mount so that I can retrieve the data from it. I have tried to add it to fstab but I am unable to find its uuid label. Additionally, gparted tells me that the disc is unallocated even though its single ntfs partition is nearly full.

Please can anybody advise what steps to take to solve this problem? Thank you.


ps. running lubuntu 13.10

---

### Post by Double.J on 2014-04-06
Hi there, Welcome to the forums!

Really sorry to hear about your situation. I would actually advise against mounting. If the drive has become damaged, every read/write attempt risks damaging data. I would advise using clonezilla to clone the drive and then attempt data recovery from the cloned drive. you can also use the dd command and may see many guides on this. I cannot stress enough that you should only use dd if you are very certain what you are doing - never copy and paste from a guide.

also when cloning disks, always boot from a live cd/usb and ensure that ONLY the disk you are cloning from and to are connected to the computer - any other hard drives or memory cards should be removed so there is no way to accidentally confuse them. Also check at least three times that you are sure which drive is being read and which is being written. 

Best of luck! Keep us upto date with the progress

Jj

---

### Post by Mark Phelps on 2014-04-06
>  its single ntfs partition is nearly full. That the disk was formatted in NTFS is important ... read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

### Post by mwsisme on 2014-04-06
Hmm ok....thanks for the advise both of you. Since my original post, I have been surfing this board looking for clues and I tried running sudo fdisk -l which produced the following output:

> Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x79d368c4

Disk /dev/sdf doesn't contain a valid partition table

This lead me to the following tutorial: [http://ubuntuforums.org/showthread.php?t=370121](http://ubuntuforums.org/showthread.php?t=370121)  . Is this likely to be of any help or am I barking up the wrong newbie-tree here?

---

### Post by squakie on 2014-04-07
You mentioned you couldn't find the UUID.  What happens when you do the following in a terminal window:

sudo blkid

I always have to use sudo in order for the blkid command to show all of the UUID's.

Also, is the ntfs file system being mounted under /media/<yourusername> ?

---

