---
title: "finding hard drive details"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by vinceUUUU on 2008-05-23
Hello

can anybody tell me what terminal command i can use to show the condition of my hard drive?

i know the drive has 3 partitions on it...but i am not sure which partition is the spare empty partition for installing winXP...

my other two partitions are a swap and the main Linux partition for my distro

i know this is a very simple Linux question but i was looking for a quick answer here

Vince.

---

### Post by kilroy423 on 2008-05-23
Show smart info:
```
sudo apt-get install smartmontools
smartctl -a /dev/DEVICE

```

Show connected drives with some info:
```
sudo fdisk -l
```

Test read and write speeds
```
hdparm -tT /dev/DEVICE
```

replace DEVICE with your hdd, probably hda or sda

Kilroy

---

### Post by vinceUUUU on 2008-05-23
Hello

Thanks for that.

so there is a small tool to download.

will try it.

thanks

Vince.

---

### Post by kilroy423 on 2008-05-23
yes...the smartmontools package is great.

If you are looking for alot of information smartctl with fulfill that wish.  It might seem daunting at first, one of the things to look for though is reallocated sectors.


Kilroy

---

### Post by philinux on 2008-05-23
It sounded in the original post that he just wanted to know how the drives where partitioned etc.

System>Admin>System Monitor File system tab can do that. As long as all drives are mounted.

---

### Post by vinceUUUU on 2008-05-23
Hello Kilroy,

the  command

fdsik -l

revealed
  
/dev/sda1  BOOT size is  10241437   83  Linux
/dev/sda2/               1028160   Linux swap / solaris
/dev/sda3/               18032962  linux

so this means to me that the 18 gig partition is the spare...it's never been formatted with fat32.....so i suposse it would default to Linux format file type

right

thanks

Vince.

---

### Post by kilroy423 on 2008-05-24
you lost me....can you post all the of the fdisk output?

Kilroy

---

### Post by SparKot on 2011-09-22
If you're inclined towards GUI tools; "Disk Utility" is another way of getting that information

---

