---
title: "[SOLVED] Drive names (e.g. /dev/sda1) are changing at reboot"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by radiocognition on 2008-06-19
Hey everyone:

I have noticed some peculiar behavior on my system.  The drive names are *changing* every time I reboot the machine.  For instance, my home directory is located on /dev/sda2, but the previous time I booted my machine, the system called it /dev/sdb2.  Its not that the order of the partitions are swapping (like a partition called /dev/sda2 switching to /dev/sda4), but the actual drive letters are switching.

This is a big hassle for me because I have my own /home partition.  Everytime I boot, Ubuntu cannot find my home directory, and I am forced to boot into a failsafe terminal and manually edit my /etc/fstab file to correct the problem.

What the heck is going on, I thought that drive names were supposed to remain static.  Is there anyway that I can force the system to call a piece of hardware by a certain drive name.

Thanks in advance for your help,

---

### Post by Gannon8 on 2008-06-19
The numbers are read from the partitions, so they shouldn't change... Something might be seriously wrong on your computer.

---

### Post by sisco311 on 2008-06-19
Mount your partitions by uuid.
uuid is an unique identifier of the partition and will not change after a reboot.

To get the uuid of the partitions:
```
sudo blkid
```fstab example:
> /dev/sda4 /home           ext3    relatime,defaults        0       2--->

> UUID=d4cd72376-733c-4469-9255-e378cd1abff0 /home           ext3    relatime,defaults        0       2

---

### Post by sisco311 on 2008-06-19
> **Gannon8 said:**
> The numbers are read from the partitions, so they shouldn't change... Something might be seriously wrong on your computer.

You're right the numbers should not change, but the device name (sd**a**, sd**b**, sd**c**) can alter after a reboot.

---

### Post by radiocognition on 2008-06-19
I will try that UUID trick.  I've just been an Ubuntu user for two years now and I never have had this issue in the past.  Didnt we just have a kernal update?  I am just trying to think of rational reasons why suddenly this starts happening.

---

### Post by sisco311 on 2008-06-19
> **radiocognition said:**
> I will try that UUID trick.  I've just been an Ubuntu user for two years now and I never have had this issue in the past.  Didnt we just have a kernal update?  I am just trying to think of rational reasons why suddenly this starts happening.

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by radiocognition on 2008-06-19
Using the UUID worked so far (two reboots).  I am marking this thread solved and posting the contents of my current /etc/fstab file.  I wish I knew why my old method (mounting by device name) suddenly stopped working.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=7cda7d37-df05-4f60-8f8e-efce5f5ddc43 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=01f131f4-317e-47f5-a208-af37b93a68c7 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

UUID=7e2b8213-488a-441f-88c3-98001b5c1ad7 /media/Music	ext3	defaults	0	0
UUID=0926c0f6-6bb1-4710-805e-323889e8218e /media/Share	ext3	defaults	0	0
UUID=567c1ee3-42af-4fb6-88ad-3bfa00dbadd6 /home		ext3	defaults	0	0
```

---

