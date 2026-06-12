---
title: "Something went wrong with my partitions"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by chris137 on 2013-11-15
Hey,
I think I kinda ****ed up my partitions.
I tried to copy 30GB earlier and failed because I do not have enough space.
I checked and saw, I only had 7GB free space in my user directory.
Then I opened gparted and got even more confused.
Not only there is no partition with that amount of free space - the space I need is at the wrong place.
I am not sure what I did wrong in the first place and have no idea how to fix this.
Simply copying those files to the host directory does not seem too clever.
So here's a screenshot.
I hope you can help.

Thanks

---

### Post by Impavidus on 2013-11-15
You have a wubi installation. This is no true dual boot, but Linux living in a virtual partition on the Windows partition (the one mounted at /host). Wubi installations cannot be larger than 30GB. I think you created two partitions for Ubuntu using windows tools (one a swap partition) and then used the wubi installer instead of the live disk installer. I think your intention was to create a true dual boot. Right now you only have a tiny amount of storage space.

---

### Post by chris137 on 2013-11-15
Well.. I followed a guide. So either I made a mistake or that guide is crap.
Will I be able to fix this?

---

### Post by oldfred on 2013-11-15
I would delete your last two partitions and start over. You want the entire last part of your drive as the extended partition so you can have many logical partitions inside it.
Then you also can have  a shared NTFS data partition as Windows will not read Linux formatted partitions, but Linux has a NTFS driver. Still best not to write a lot into Windows system partition so set it as read only and use shared data partition as read/write.

If you have made a lot of changes you can back up /home and then restore that.
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

If you use auto install it only creates the / & swap partitions.
      
 The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by chris137 on 2013-11-18
Okay, so I made a backup of home and killed all partitions.
I started over, restored home and am lucky now.
Thanks for your answers :)

---

