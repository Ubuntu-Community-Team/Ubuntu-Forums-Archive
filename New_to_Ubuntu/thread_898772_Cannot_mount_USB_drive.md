---
title: "Cannot mount USB drive"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by RicherL on 2008-08-23
I recently installed Ubuntu via USB drive. I am now unable to mount any USB drives on the laptop.
I have tried 4 different USB sticks, and they all give the same error.

my /etc/fstab file reads

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1e8c3d02-a0a9-4201-8526-6577d43b2dc1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4e86e240-7ce1-4f46-b7b2-da239d8a7e45 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Because the install believes its coming in from a CD, it looks like its declared USB drives as cd drives.

Kind of new to all this... what can I do to fix this?
The laptop doesn't have a cd or dvd rom, so I really need USB support!


Thanks,

L Richer

---

### Post by RicherL on 2008-08-23
Just wondering here... could I simply comment out the 

> /dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0 line?

I won't have access to the notebook again until tomorrow morning, but I'll try that and update here if it does work.

Any suggestions until then are welcome!

---

