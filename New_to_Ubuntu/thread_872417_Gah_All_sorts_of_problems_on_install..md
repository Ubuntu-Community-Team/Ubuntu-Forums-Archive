---
title: "Gah All sorts of problems on install."
date: 2008-07-28
forum: New to Ubuntu
---

### Post by DasLegionnaire on 2008-07-28
Ok, Ill tell the whole story...

I got a virus in windows, the explorer.exe kept messing up but my pc/files were still usable.

Whenever I would run a virus checker for one reason or another it couldnt delete the files.

I decided to install ubuntu, I had used ubuntu for about 6 months but I am working on a music demo and need to use windows. Everything went fine until I got to the partitioning screen. I think I just changed the filetype, I know i never told it to format my windows partition nor did i ever even install anything.

Well there was some sort of error and I ended up rebooting, windows would not boot up, and when I put in my windows xp disk and went to recover and put in dir to the command prompt it spat out some corrupt disk error. 

So now all of the music I having been working on for well over FOUR YEARS in on a corrupted disk, I know I should back-up but I figure this is the lesson we all have to learn. But I do NOT want to lose this data!


So as of now I am using 8.04 livedisk, which works with my wireless adapter out of the box (woohoo!) I tried to install teskdisk but can not figure out how to install it, and I cant even remember how to mount a disk...

please, I am in desperate need of help.

---

### Post by DGortze380 on 2008-07-28
The first thing you need to do is STOP mounting that disk!

Use the dd command to image the drive. So you can work from the image, not the drive.

Take a look at this link: [http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

You're on a live CD. post the output of:

```

df -l

```

---

### Post by dietkinnie on 2008-07-28
1. you should have backed up all the files if you were uncertain about creating partitions.

2. sudo apt-get install testdisk

3. search google with "mount partitions linux"

---

### Post by DGortze380 on 2008-07-28
> **dietkinnie said:**
> 1. you should have backed up all the files if you were uncertain about creating partitions.

2. sudo apt-get install testdisk

3. search google with "mount partitions linux"

If that's the only copy of your data, do not perform any operations on that disk until you have a byte for byte copy of the entire disk.

you'll probably want something along the lines of 

```

dd if=/dev/sda1 of=/dev/sdb1

```

where sda1 is the drive with your ntfs partition, and sdb1 is an external usb hard drive.  I'll need the output of df -l (thats a lowercase L) to know exactly what command you need.

---

### Post by falcon61102 on 2008-07-28
Have you tried using the snyaptic package manager under Settings>Administration to install testdisk.  

You may be able to mount the partitions in question by going to Places>Computer and selecting them if they are available.

Otherwise you are going to have to use the terminal, the code should look something like:
```
sudo mkdir /media/winxp
sudo mount -t ntfs-3g -o /dev/sda1 /media/winxp 
```

The first command creates a mount folder.
This is for an NTFS file system.  The /dev/sda1 is the partition and /media/winxp is the mount point.

Use:
```
sudo fdisk -l
```
To determine the exact partition name.

---

### Post by DGortze380 on 2008-07-28
> **falcon61102 said:**
> Have you tried using the snyaptic package manager under Settings>Administration to install testdisk.  

You may be able to mount the partitions in question by going to Places>Computer and selecting them if they are available.

Otherwise you are going to have to use the terminal, the code should look something like:
```
sudo mkdir /media/winxp
sudo mount -t ntfs-3g -o /dev/sda1 /media/winxp 
```

The first command creates a mount folder.
This is for an NTFS file system.  The /dev/sda1 is the partition and /media/winxp is the mount point.

Use:
```
sudo fdisk -l
```
To determine the exact partition name.

Again, if this is the only copy of the data on that disk, DO NOT mount anything until you have a copy. If you did reformat by mistake, or deleted the partition table, then simply mounting the partition can make the data significantly more difficult if not impossible to recover. 

Make an iso of the drive and mount the iso. Then try to recover the data.

---

### Post by falcon61102 on 2008-07-28
Yeah, that's a good point, and I hope after three posts he gets it :).  I was merely answering his original question since you provided the rest of the info...

---

### Post by DasLegionnaire on 2008-07-28
Ok, so i feel like a just got hit with a lot here,

how do I create an iso of the drive? That would mean I need a drive at least as big as that drive to create it on?

Do I need to run testdisk before I create an Iso?

I havent been able to access the drive at all so that sounds good.


Maybe a step by step?

---

### Post by DasLegionnaire on 2008-07-28
please guys a bit more instructions.

---

### Post by DGortze380 on 2008-07-28
Start By opening a terminal (Accessories>Terminal) and typing

```

df -l

```

that's a lowercase L

post the output here.

---

### Post by DasLegionnaire on 2008-07-28
ubuntu@ubuntu:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                  1037300     16512   1020788   2% /lib/modules/2.6.24-19-generic/volatile
tmpfs                  1037300     16512   1020788   2% /lib/modules/2.6.24-19-generic/volatile
varrun                 1037300       100   1037200   1% /var/run
varlock                1037300         0   1037300   0% /var/lock
udev                   1037300        52   1037248   1% /dev
devshm                 1037300        12   1037288   1% /dev/shm
tmpfs                  1037300      1632   1035668   1% /tmp
gvfs-fuse-daemon       1037300    153852    883448  15% /home/ubuntu/.gvfs
/dev/sdb1             58613120  23373136  35239984  40% /media/disk

---

### Post by DasLegionnaire on 2008-07-29
bumpity bump

---

### Post by DGortze380 on 2008-07-29
Take a look at this link, or use the dd command I posted early, to get a copy of the drive.

[http://ubuntuforums.org/archive/index.php/t-6509.html](http://ubuntuforums.org/archive/index.php/t-6509.html)

---

### Post by DasLegionnaire on 2008-07-29
why did i have to paste that stuff?


And it will be a few days until I can get a bigger hard drive.

---

### Post by DGortze380 on 2008-07-29
> **DasLegionnaire said:**
> why did i have to paste that stuff?


And it will be a few days until I can get a bigger hard drive.

I was trying to see what device your filesystem was on. looks like it'll be something like sda1. But there isn't much we can do until you have a place for a backup anyways.

---

