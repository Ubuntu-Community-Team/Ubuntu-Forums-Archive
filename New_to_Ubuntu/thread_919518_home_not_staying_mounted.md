---
title: "/home not staying mounted"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by G14N14RI12 on 2008-09-14
Hello, I'm fresh to Linux and (after a few days figuring out what to do) have installed Ubuntu for the first time. 

The problem I'm having is that every time I try to log in after booting the computer Ubuntu says that /home could not be found and cannot log in normally. So to fix this I log into a failsafe terminal and mount the /home partition, after which I can log in normally. I assume this has something to do with fstab, but I don't know what could be wrong here:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/pdc_fgadfgae1
UUID=8dccf345-7b92-42ef-b797-8d1a11110e50 /               ext3    relatime,errors=remount-ro 0       1
# /dev/mapper/pdc_fgadfgae6
UUID=76d663b7-526f-43ab-b1b6-6712add82c9c /home           xfs     relatime        0       2
# /dev/mapper/pdc_fgadfgae5
UUID=88361f24-90cb-4a4f-b4dc-e991383bb171 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

```

:~$ sudo blkid
/dev/mapper/pdc_fgadfgae1: UUID="8dccf345-7b92-42ef-b797-8d1a11110e50" TYPE="ext3" 
/dev/mapper/pdc_fgadfgae6: UUID="76d663b7-526f-43ab-b1b6-6712add82c9c" TYPE="xfs" 
/dev/mapper/pdc_fgadfgae5: TYPE="swap" UUID="88361f24-90cb-4a4f-b4dc-e991383bb171" 
/dev/mapper/pdc_fgadfgae3: TYPE="swap" UUID="46e9338e-7e6c-43ed-a4ef-ce01717262a4" 
/dev/sda1: UUID="8dccf345-7b92-42ef-b797-8d1a11110e50" TYPE="ext3" 

```

---

### Post by cmnorton on 2008-09-18
This sounds like /home got mounted on a separate partition, though I did not know if the Ubuntu install let you do something like that by default. Probably you need to put an entry into fstab 

sudo vi /etc/fstab
or 
gksudo <your favorite X-win editor> /etc/fstab

Here's an entry I have on a Fedora system

/dev/sdb1         /mnt/sdb1         ext3     defaults,errors=remount-ro 0 1

---

### Post by karlr42 on 2008-09-18
I take it sda1 is home? If it's not in fstab, it won't be mounted at boot. Try adding something like:
```
/dev/sda1	 /home     ext3	     defaults,errors=remount-ro 	0 	1
```
those are tabs

---

### Post by philinux on 2008-09-18
> **G14N14RI12 said:**
> Hello, I'm fresh to Linux and (after a few days figuring out what to do) have installed Ubuntu for the first time. 

The problem I'm having is that every time I try to log in after booting the computer Ubuntu says that /home could not be found and cannot log in normally. So to fix this I log into a failsafe terminal and mount the /home partition, after which I can log in normally. I assume this has something to do with fstab, but I don't know what could be wrong here:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/pdc_fgadfgae1
UUID=8dccf345-7b92-42ef-b797-8d1a11110e50 /               ext3    relatime,errors=remount-ro 0       1
# /dev/mapper/pdc_fgadfgae6
UUID=76d663b7-526f-43ab-b1b6-6712add82c9c /home           xfs     relatime        0       2
# /dev/mapper/pdc_fgadfgae5
UUID=88361f24-90cb-4a4f-b4dc-e991383bb171 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

``````

:~$ sudo blkid
/dev/mapper/pdc_fgadfgae1: UUID="8dccf345-7b92-42ef-b797-8d1a11110e50" TYPE="ext3" 
/dev/mapper/pdc_fgadfgae6: UUID="76d663b7-526f-43ab-b1b6-6712add82c9c" TYPE="xfs" 
/dev/mapper/pdc_fgadfgae5: TYPE="swap" UUID="88361f24-90cb-4a4f-b4dc-e991383bb171" 
/dev/mapper/pdc_fgadfgae3: TYPE="swap" UUID="46e9338e-7e6c-43ed-a4ef-ce01717262a4" 
/dev/sda1: UUID="8dccf345-7b92-42ef-b797-8d1a11110e50" TYPE="ext3" 

```

Your fstab looks ok to me. What exactly are the errors when you login?
Here's mine, I've a separate home.
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9d1cb08e-4895-4fdf-986e-8426ce01b211 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=39759482-7d7a-4398-b338-2cdf7ed2e99d /home           ext3    relatime        0       2
# /dev/sda2
UUID=41d5d5ba-4485-462c-bb71-309d7d42359b none            swap    sw              0       0
# /dev/sdb2
UUID=ab1f8f9f-6596-4625-9e5c-a60a17af1901 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by egalvan on 2008-09-18
> **cmnorton said:**
> This sounds like /home got mounted on a separate partition, though I did not know if the Ubuntu install let you do something like that by default.

A separate /home partition is VERY common in Linux.
(keeps your settings separate)

I, for one, have ALWAYS had a separate /home...

under:
Ubuntu, Kubuntu, Xubuntu, Mandrake, PCLinuxOS, and a few others...

(well, except for a couple of 'quicke' fresh installs to try something out, but these did not last long, usually a few hours. Just experimental.)

My home file server has a separate /home DRIVE

and i never had to do anything to get and keep /home mounted....



So there are problems here, but I'm too new to see the solution...

---

### Post by egalvan on 2008-09-18
This should NOT be a problem, I'm just pointing it out:

you have /home using the 'xfs' file system.


Any of you Linux wizards see problems with xfs?

---

### Post by timcredible on 2008-09-18
if this is a fresh install, i would recommend re-installing, and leaving the filesystem as ext3 for /home.

---

