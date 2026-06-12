---
title: "Ubuntu Dual Boot"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by Sleepy333 on 2012-10-05
Hello,

I've looked around on the forums first and searched if any other topics had anything I could use, but didn't find much which could serve it's purpose. So I'll just ask here.

To give a little insight, I'm currently a high school student who studies computer sciences. Now for certain classes we need to use Microsoft software (e.g. Visual Studio). So I can't just switch to only Ubuntu and I know that Windows can take quite a bit of hard disk space already.

Now I'm a bit struggling with the issue on how much space I need to reserve for Ubuntu. I know that giving a precise number will be hard, but I can live with an estimate.
Basically, I will use it for the following things:
1. Coding in HTML, Java & Python
2. Learning how to use Ubuntu (e.g. bash scripts)
3. Learning about Ubuntu itself as in how it is coded, developed, maintained, etc.

Currently I have a laptop with 500GB hard drive, so I certainly got some space to work with.


Regards,
Sleepy333

---

### Post by DeezyFaReal on 2012-10-05
You need at least 5 GB for Ubuntu.
It's better to go ahead and give it 10 or 15.
You should have no problem doing that ; )

---

### Post by oldfred on 2012-10-05
I prefer smaller system partitions for both Windows & Linux. Then you can create a shared NTFS data partition for any data you may want in both systems. Best to set Windows system partition as read-only as it does not like too many writes into its system partition. Also the Linux NTFS driver exposes all the normally hidden files & folders in Windows, so accidents can happen if not just read only.

I use 25GB for my Ubuntu system partitions, but have all data in both an older NTFS shared data from when I still booted XP and now all new data goes into a Linux formated data partition. Windows will not see Linux partitions.

Of my 25GB / (root) partition, I use about 9GB with lots of programs installed. Over 1GB is for .wine with Windows version of Picasa. Videos, music, and what few games are currently in Linux are the ones that may consume lots of space.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

