---
title: "Backup partition with partimage"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by sumpm1 on 2008-07-30
Hey guys, I am total noob to Linux, came from XP. I Have 8.14.1 installed and  want to backup the partition with Ubuntu on it so tha I can restore to this point later. I am trying to use partimage on a Live CD.

I have 3 partitions on my drive: a 20gb drive for linux, a 2 gig swap partition (that ubuntu created itself), and the rest of my 320 Gig hard drive is another partition. All of the partitions are ext3, made in gparted.

sda1:20gig (1.5 gigs used)
sda2:2gig
sda3:rest of space

I want to backup sda1 to a folder on sda3. I am having trouble with the SPECIFIC commands that I should use to create a folder and mount the drive. I thought I had it mounted correctly, but when I ran partimage, after like 500megs of transfer, it says that the "devise is full, please choose another location" or something like that. How exactly should I achieve this? Am I going about it all wrong? Any advice is appreciated, I just want to COMPLETELY backup my Linux drive for later restore. 

Thanks

---

### Post by drs305 on 2008-07-30
From the live CD:

```
sudo mkdir /mnt/temp
sudo mount /dev/sda3 /mnt/temp
```

```
sudo partimage
```
Select the partition to be backed up with the up/down buttons (sda1).
Save File Name: /mnt/temp/pickaname

---

