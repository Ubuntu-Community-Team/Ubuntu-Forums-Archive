---
title: "Can't get access to hard drives."
date: 2008-07-06
forum: New to Ubuntu
---

### Post by darien_ward on 2008-07-06
I'm very new to Ubuntu and to this forum, so I'm sorry in advance for any stupid questions :)

So... I've got Ubuntu 8.04 which I load from USB flash, and I've got two FAT32/NTFS hard drives.
The problem is: whenever I try to open any of them via Places --> Computer, I get the same error:
[B]Unable to mount the volume.
Cannot create /media/.hal-mtab~[/B]

If I try to mount them manually, I get this:
```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
```
or this:
```
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sdb1 /media/disk1
mount: according to mtab, /dev/sdb1 is already mounted on /media/disk1
```

How can I fix this?
I hope someone can help me here. Thanks in advance!

---

### Post by ibutho on 2008-07-06
The output of the second command says that the disk is alreay mounted at /media/disk1, so go to /media/disk1 and see if you can access the contents.

---

### Post by Troll_the_Great on 2008-07-06
If your hard drives are NTFS you should install ntfs-config and they will be mounted automatically at start-up.Open a terminal and type:
```
sudo apt-get install ntfs-config
```
Have a look at this links:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
Cheers!

---

### Post by darien_ward on 2008-07-06
**ibutho**
In /media/disk1 there is one empty folder named '500_1' (it's the label of the hard drive I try to mount). Also there are several folders marked as unreadable with names like '500_1_', 500_1__' etc. (probably from previous tries?), and I can't open them at all.

**Troll_the_Great**
Thanks, I tried it too, but still no result.

---

