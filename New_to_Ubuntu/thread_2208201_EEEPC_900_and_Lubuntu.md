---
title: "EEEPC 900 and Lubuntu"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by Adrian_Kniel on 2014-02-26
I installed Lubuntu 13.1 with no problems in my eeepc900 which has two disks ( 4gB and 16gB). I would like to use the 16gB hard disk as home and have read the following post
[http://ubuntuforums.org/showthread.php?t=1762241&highlight=asus+eeepc900](http://ubuntuforums.org/showthread.php?t=1762241&highlight=asus+eeepc900)
that explains how to do this. However being new to lubuntu I have no idea what this means.
Could someone please walk me through the proper steps one at a time.
Thank you in advance

---

### Post by David_Wright on 2014-02-27
There is a very detailed walk through here:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Hope this helps.

---

### Post by coldraven on 2014-02-27
I installed Xubuntu 13.10 on my eeePC 900 and it worked fine but soon ran out of space on the 4GB drive.
The reason was that when it downloads updates it need space in /tmp to uncompress them before installing them. So I ended up with about 400 updates waiting to be installed.
The easiest solution was to completely re-install Xununtu but use the partitioning tool to make some changes.
I made two 1GB partitions on the 16GB drive 
When installing select the 4GB as / (root)
One of the 1GB partitions for /tmp
The other 1GB partitions for /var
The remainder (14GB) as /home

I decided that the loss of space could easily be made up by leaving an SD card in the slot.

---

