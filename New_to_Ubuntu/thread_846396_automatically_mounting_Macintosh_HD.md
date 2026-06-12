---
title: "automatically mounting Macintosh HD"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Ravinon on 2008-07-01
Hi, 

I am trying to automatically mount Macintosh HD. I tried the advice of another thread and now my fstab looks like this: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=ef059b93-18cc-4c21-91f3-4043106b19a7 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda2       /media/Macintosh hfs+ auto,user,exec,rw	0	0
# /dev/sda6
UUID=346fcf46-6792-44d4-bdbf-b82bcd77060b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Where /dev/sda2 is my hfs+ Macintosh HD, which is named Macintosh. Now, whenever I try to mount Macintosh, I get the error message "The volume 'Macintosh' uses the  file system which is not supported by your system."

This is strange, because I can manually mount the Macintosh HD if I just comment this line. 

I also tried creating the Macintosh folder in /media. This did not work either.

Help, please?

---

### Post by Ravinon on 2008-07-01
I have also tried installing hfsplus and hfsutils, this did not help.

---

