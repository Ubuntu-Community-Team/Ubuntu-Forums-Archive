---
title: "kmymoney backup"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by unibroker on 2012-05-01
I'm dual boot ubuntu 12.04 & WinXP.  I use kmymoney which I backup to the same external drive as I have MS Money archives on.  When I tried to backup the dialogue box in kmymoney asked if the external drive was to be mounted first.  I selected it and the procedure failed (I assume because it was never partitioned and therefore is all fat32).  I deselected it and the backup was successful.

I booted into XP, defraged the external drive and found I have loads of free space.  I have downloaded gparted into Ubuntu and was thinking of recapturing a portion of this free space like I did to my hard drive to enable the dual booting of Ubuntu.  If this is advisable should I designate the file system of this new partition ext3?

---

### Post by bodhi.zazen on 2012-05-01
If you are going to use the hard drive for Linux only, I would use ext3 or ext4.

If you are going to share it with windows, NTFS.

---

### Post by unibroker on 2012-05-01
> **bodhi.zazen said:**
> If you are going to use the hard drive for Linux only, I would use ext3 or ext4.

If you are going to share it with windows, NTFS.

Thanks for the response!  I am sharing the external drive with Microsoft Money (double-entry for awhile).  

When I partitioned my hard drive to dual boot Ubuntu, the NTFS partition was occupied by XP.  If I remember correctly the new partition for Ubuntu was ext3.  Since kmymoney is for use on a linux platform is NTFS the file system I want for this new partition area?

---

### Post by bodhi.zazen on 2012-05-02
> **unibroker said:**
> Thanks for the response!  I am sharing the external drive with Microsoft Money (double-entry for awhile).  

When I partitioned my hard drive to dual boot Ubuntu, the NTFS partition was occupied by XP.  If I remember correctly the new partition for Ubuntu was ext3.  Since kmymoney is for use on a linux platform is NTFS the file system I want for this new partition area?

I would use ext4 for your ubuntu partitions.

---

### Post by unibroker on 2012-05-02
> **bodhi.zazen said:**
> I would use ext4 for your ubuntu partitions.

Thanks for your input.

---

