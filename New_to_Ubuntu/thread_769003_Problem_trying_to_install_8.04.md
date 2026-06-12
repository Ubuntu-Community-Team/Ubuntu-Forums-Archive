---
title: "Problem trying to install 8.04"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by carlofono on 2008-04-26
I have tried to install the new release of ubuntu several times, but every time i try, when it comes to step 4, the partitions doesn't appear. I run gparted to check, and no devices detected. Since i have 7.10, I tried doing an upgrade but when ubuntu boot busybox appears. I run ```
sudo fdisk -l /dev/sda
``` and nothing appears. I have no problem installing gutsy. I hope someone can help.

---

### Post by PattonPending on 2008-04-26
Are you trying to set the partitions manually, or are you letting the system partition and format things automatically?

Within the live CD environment (not the installer), are you able to see your hard drive and interact with it?

---

### Post by carlofono on 2008-04-26
It seems that the OS doesn't see my hard drive. Within the installer when it says starting partitioner, it jump to step 4. In this step there's supposed to appear the partition, but nothing. The options to choose between manual,etc, doesn't appear.

---

### Post by PattonPending on 2008-04-26
> **carlofono said:**
> It seems that the OS doesn't see my hard drive. Within the installer when it says starting partitioner, it jump to step 4. In this step there's supposed to appear the partition, but nothing. The options to choose between manual,etc, doesn't appear.

Do you have more than one hard drive in the machine?  Also, when you start the partition manager, you said it detects nothing?

---

### Post by PattonPending on 2008-04-26
You can also try the solution specified in [this thread]("http://ph.ubuntuforums.com/showthread.php?t=726546").  (make sure the hard drive is listed as the primary drive, otherwise it may have issues being automatically detected)

Post the results of the ```
cat /etc/mtab
``` and ```
sudo fdisk -l
``` here as well, if that doesn't seem to be the issue.

---

