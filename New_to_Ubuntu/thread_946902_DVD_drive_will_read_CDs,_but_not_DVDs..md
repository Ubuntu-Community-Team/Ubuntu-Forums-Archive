---
title: "DVD drive will read CDs, but not DVDs."
date: 2008-10-13
forum: New to Ubuntu
---

### Post by TheHanna on 2008-10-13
Just installed Ubuntu 8.04 this morning, absolute beginner, so please be patient with me :)

I have 2 optical drives on my machine, a DVD-R drive and a CD-RW drive. They will both read CDs fine, but the DVD-R drive will not read DVDs.

When I put a DVD in the DVD drive, I get the error message Cannot Mount Volume. Invalid Mount Option When Attempting To Mount The Volume 20081012_0543.

Here is my fstab contents:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4ab32424-d694-4df5-83f2-44b5c28d5479 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=637126ab-6d3a-4a5e-abcf-da741e3c6fa2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


My (un)educated guess is that the DVD drive is mounted as a CD drive, and therefore will not read DVDs. If so, how do I fix that?

---

### Post by philinux on 2008-10-13
My single dvd writer shows up in fstab as this.

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```Works fine.

Not sure why yours is not working.

---

### Post by TheHanna on 2008-10-13
Found the problem. Windows decided to flip me off one last time before I gave up on it. None of the backup DVDs I burned are reading at all. Just tried my copy of Independence Day, and it read perfectly. I just lost 40gb of DRM-free music, among other things.

---

