---
title: "Help Mounting Windows Partition"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Amit Gillen on 2008-06-09
Hi,' I've recently switched over to Ubuntu due to the fact that my windows has managed to lose some of it's system32 files to a virus. I have since come to love Ubuntu and plan to keep it as my primary OS. However, I would still like to get my rather large music library and writing collection over to my Ubuntu partition. I have followed several guides that I found online to mount my windows partition, but I'm afraid I just don't know enough about Lunux to make it work. 

Here is a link to the guide that I used
[https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

and this is the spot that I cannot figure out how to get past.

mount: special device /dev/hda1 does not exist

From what I can tell I have simply misnamed my Windows partition, but I have no idea how to find the real name. Any help would be greatly appreciated.

---

### Post by unutbu on 2008-06-09
Post

```
sudo fdisk -l
```

This will show us what hard drives and partitions you have and their device names.

---

### Post by lisati on 2008-06-09
(deleted:L unubtu beat me to it)

---

### Post by Amit Gillen on 2008-06-09
/dev/sda1   *           1       29759   239039136   83  Linux
/dev/sda2           29760       30515     6072570    5  Extended
/dev/sda5           29760       29820      489951   82  Linux swap / Solaris
/dev/sda6           29821       30515     5582556   83  Linux

These are the results I got from that command...does this mean that I somehow deleted my Windows partition?

---

### Post by unutbu on 2008-06-09
If your windows data partition was on your primary hard drive, then it looks like the windows partition is gone. However, there is a *chance* that you may be able to recover your old partition by using Test Disk
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Amit Gillen on 2008-06-09
I'm just going to go ahead and give up here, this is all getting to be too confusing for someone who's lived his whole life wrapped up in windows. I'm too used to things going wrong and having no way to fix it myself I guess.. Thanks for the help though, I can tell this is a community that I'm going to like being a part of.

---

