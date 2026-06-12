---
title: "partitions"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by mannpann on 2012-04-28
So, I'm trying to create a new partition to run win 7 on it. I have found posts on the topic but they are not exactly what I need and too complicated for me, and since I know little about computers, especially ubuntu, I would appreciate if someone could help me with a step by step guide.

The first problem that I encountered was that when trying to create a partition, you need to have disks unmounted, how on earth do I unmount my hard drive in order to do that, or what do I do? 

[http://s1079.photobucket.com/albums/w504/mannpann/?action=view&current=sss.png](http://s1079.photobucket.com/albums/w504/mannpann/?action=view&current=sss.png)
this is what it looks like. 

Secondly, I really don't have a clue how to create a partition that would actually recognize/accept windows. 

Thank you in advance, I've had Ubuntu for some time now and trying to come up with solutions is killing me (I have literally punched my computer).

---

### Post by Zukaro on 2012-04-28
You can't unmount the partition Ubuntu is running on.  What you'll have to do is boot up a LiveCD/LiveUSB, go into Gparted, and then shrink the partition.

You don't need to make any special partitions for Windows, just leave it as unformatted and format it in Windows.  If you really want to format it before booting into Windows format it as NTFS.

Just make sure you know which partition to format (if you leave it as blank space it will say "Free Space" in Windows (or something similar), if you format it as NTFS it will say NTFS).

---

