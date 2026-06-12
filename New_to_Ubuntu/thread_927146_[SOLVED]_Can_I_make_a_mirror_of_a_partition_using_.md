---
title: "[SOLVED] Can I make a mirror of a partition using the LiveCD and other partitioning q"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by hito1 on 2008-09-22
I'm about to set up a computer with 2 hard drives, one 500gb sata and another 120gb pata. 

I want to partition the 500gb like this: 50gb vista/ 50gb ubuntu / 1gb linux swap/ 399gb storage. I'd like to use the 120gb disk to keep backup images of Vista and Ubuntu installations.

I have a few questions:

1. Do I really need a swap partition with 4gb of RAM?

2. Is 50gb enough for Vista and Ubuntu? Is it too much? My use is minimal, basically firefox + open office + games, and I intend to install my games at the 'storage' partition.

3. What is the best way to backup/mirror my install partitions? Can I do it with the LiveCD (gparted or something else)?

4. Do my backup partitions have to have the same size as the install partitions? I ask this because, despite setting aside 50gb for vista and ubuntu installs, the actual content of the backup will be smaller than 50gb (vista and ubuntu clean installs).

5. Am I forgetting something? Is this plan doable?

Thanks a lot.

---

### Post by louieb on 2008-09-22
[LIST=1]
[*]Will need swap only if you plan to hibernate then you will need a little more than the amount of ram you have.  a gig of swap is a good amount otherwise.
[*]Since your keeping your data in a separate partition 10GB should be plenty for Ubuntu.
[*]See this thread on **partimage** [Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522") (works great for Ubuntu).
[*]See #3 I use the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") I have a backup folder on my data drive - that way don't worry about size.
[*]Might want to goggle search partitions. In particular lean the difference between primary logical and extended partitions. By using  extended and logical partitions you can have more that 4 partitions on a hard drive 
 I find it handy to have a testing install partition. After all Ubuntu and some of the other major Linux distros put out a new version every 6 months or so. For ease of use I make mine the same size as the working install partition.
[/LIST]

Seem like a a good plan. Some will tell you to create a separate /home partition too. I create a 5GB partition for /home and use most of my hard drive space for my data partition. Others think the separate /home is overkill.  Check out the psychocats link in signature for lost of good Ubuntu ideas. 

Good Luck.

---

### Post by Yannick Le Saint kyncani on 2008-09-22
Hi hito1,

> 1. Do I really need a swap partition with 4gb of RAM?

You do need a swap partition for hibernate. And I would keep a 4G swap. 

> 2. Is 50gb enough for Vista and Ubuntu? Is it too much? My use is minimal, basically firefox + open office + games, and I intend to install my games at the 'storage' partition.

Considering you have a separate partition for storage, 50G is very confortable. You will be able to keep a large amount of linux-only data with 50G. 30G would still be confortable too.
 
> 3. What is the best way to backup/mirror my install partitions? Can I do it with the LiveCD (gparted or something else)?

The easiest way would be to use rsync onto an ext3 partition, manuals and howtos available on the web.

That's what I think anyway.

>  4. Do my backup partitions have to have the same size as the install partitions? I ask this because, despite setting aside 50gb for vista and ubuntu installs, the actual content of the backup will be smaller than 50gb (vista and ubuntu clean installs).

If you plan to use rsync, the backup partition has to be at least the same size than the source, as the backup is an exact copy of the source. You also need a filesystem that can mirror the files attributes, so that means two separate backup partitions, one ext3 for linux and one ntfs for windows.


Just my .02$

---

### Post by hito1 on 2008-09-23
Thank you, guys!

---

