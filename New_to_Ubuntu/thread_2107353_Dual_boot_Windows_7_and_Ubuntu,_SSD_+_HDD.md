---
title: "Dual boot Windows 7 and Ubuntu, SSD + HDD"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by treystaff on 2013-01-21
Hello, 

I am new to linux and Ubuntu and wish to create a system that can boot both Windows 7 (for windows specific applications) and Ubuntu (I wish to become familiar with linux and Ubuntu for work). I have already read through a lot of material, but found nothing for quite what I am looking to do, and I am not sure how or where I should start. 

I have a 120GB solid state drive on which I want to locate the windows and linux OS, as well as other applications that would benefit from the SSD. 
I additionally have a 1TB hard drive that I want to use for data/storage. 

From what I have read, I understand that I will need to partition the drive(s) or use Logical Volume Management to set up the dual boot environment that I envision. I hope to share the data stored on the 1TB hard drive between the two operating systems, but if this is not feasible then splitting the 1TB hard drive into two or more smaller partitions would be fine. 

I have previously installed windows to the SSD and 'migrated' the User's folder to my 1TB data drive (without manually setting up a partition or anything). This worked fine for a while, but the system proved unstable and no longer works, except in 'safe mode'. I have all of my data backed up, so I intend on "starting over" and re-installing windows along with ubuntu. I don't want to keep anything that is currently on the ssd or hdd. 

In short: 
--I have a 120 GB solid state drive I want to put Windows 7 and Ubuntu on. 
--I have a 1TB hard disk drive that I want to use as data storage for the two operating systems. 
--What is the best way of going about this? I want the system to be as stable as possible while maximizing the benefits of using an SSD to boot from/run applications. 
    + Any advice or information would be appreciated!


Thanks!

---

### Post by oldfred on 2013-01-21
Welcome to the forums.

I am sure there are several ways to accomplish what you want. And even my own "optimal" configuration a year or two later is not so good. :) 

I am not a fan of LVM, unless you really need a lot of flexibility on repartitioning.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)

    
I do like small system partitions and larger data partitions. I also prefer to have operating systems on every drive that can boot without the other drive. So when one fails I can still boot. 
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

    
I would allocate most of SSD to Windows since it is large & works best with lots of free space (30% free). I normally install Ubuntu to 25GB / (root) partitions including my /home but then have all data in two data partitions. My /home is about 2GB which is mostly .wine. But I am aggressive about moving data including some hidden folders like Firefox & Thunderbird profiles, so I can use them from all my installs. Those profiles are in my Shared NTFS partition, but I also have most new data now in my Linux formatted data partition as I stopped booting XP.

I currently have two Ubuntu installs in my 62GB SSD and only use about 9GB. So you can allocate 25GB or so to Ubuntu and the rest to Windows. Then on 1TB drive make a large NTFS data partition. I am not sure I want just one large NTFS partition as even chkdsk on a very large drive can take awhile. Also how are you planning to back up 1TB of data?

---

### Post by audiomick on 2013-01-21
I am a bit less rigorous than oldfred. I leave a fair bit of room for my /home. However, I don't got into the 'net with windows if I can avoid it, so when I get files in e-mails that I need for work, I always save them to the ntfs Data partition that can be accessed from both installs on my Win Vista / Ubuntu daul boot laptop.

In short, think a little bit about how your habits are, and structure your data partitions accordingly.

Give windows space. I have read that 30GB is good. More if you can afford it. As oldfred has mentioned, windows needs some elbow room. An Ubuntu install doesn't need much space, about 5GB I think, until you start installing extra stuff. I have about 15GB on my desktop. I set up a separate /home and make it big so I don't have to worry about how much space stuff needs that is only relevant to the Linux install. I don't bother with LVM, or with syslinks to various files, which is another way to keep your /home small.

---

