---
title: "[SOLVED] /home partition problems"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by whitethorn on 2008-11-08
Hi,

I set up my /home partition as a primary partition and I can no longer add any partitions.  I was thinking I could backup my /home (it's the last partition on my drive) then change it to extended and then put the data back on the drive.  

I used partimage to create a backup, then gparted, removed the partition and created an extended with the rest of the drive.  I then used partimage to restore the data. Unfortunately it's not working properly.  When I open start ubuntu I can use my home directory but when I check my harddrive instead of being 41 gigs being used, it shows 96 gigs. I'm not really sure what's happening, but when I wasn't able to find the data which is taking up most of the space. The original size of my /home was 98 gigs, and the new one is 150.  Any ideas how to get my data back and working properly?

I think my problem was that I did a backup from the partition and not the files themselves. Not sure what to do about it though.

---

### Post by philinux on 2008-11-08
Post result from

```
[FONT=Trebuchet MS]sudo fdisk -l[/FONT]
```

---

### Post by drs305 on 2008-11-08
Let's try to make some sense out of all this. First, if possible, it would be helpful if you could post a pic of gparted so we can see how your drive partitions ended up.

Second, run the following and post the results:
```

df -Th | grep '/dev/'
sudo fdisk -l

```

If you think there is more data than there should be on a drive, you might check the trash bins to see if there is unemptied trash. This trash takes up partition space even though it's trash. There is a link in my signature block about how to find and remove trash from your system.  If you were checking your disk space with Disk Usage Analyzer (baobab) it often is confusing to new users. Refer to the outputs from the command above to really see how much of a partition is being used (including trash).

---

### Post by whitethorn on 2008-11-08
Hi, so instead of having a huge /home, I made it a bit smaller and then did a tar of my data onto the last drive.  I'm not really sure what happened but it now looks like I have exactly what I had before -> namely 41 gigs on my /home.  Now I'm a little confused.  Here are the the answers to the two posts, but it looks like the problems been solved.

> ~|$df -Th | grep '/dev/'
/dev/sda2     ext3     20G  3.6G   15G  20% /
tmpfs        tmpfs    505M   12K  505M   1% /dev/shm
/dev/sda5     ext3    102G   41G   58G  42% /home
/dev/sdb1     vfat    233G  178G   56G  77% /media/HDDRIVE2GO

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda621ae6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       10199    20482875   83  Linux
/dev/sda3           10200       10467     2152710   82  Linux swap / Solaris
/dev/sda4           10468       30401   160119855    5  Extended
/dev/sda5           10468       23982   108559206   83  Linux
/dev/sda6           23983       30401    51560586   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc61fa308

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32
/dev/sdb2   *           1           1           0    0  Empty
Partition 2 does not end on cylinder boundary.


sdb is an external USB HD.  To check how much of my harddisk was being used, I first used the program system Monitor under System -> Administration.  I had then run df -h. I had also used GParted to compare.  Thanx for the help.

---

