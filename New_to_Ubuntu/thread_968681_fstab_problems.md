---
title: "fstab problems"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by jerlinux on 2008-11-02
I should not have been messing with my fstab.  Since I have messed with it, none of my dvd drives will mount.  Gives me the next line can't have a g or some such thing.

I hoped that upgrading to 8.1 would bring in a new fstab but it did not.  

I will attach a copy of the current fstab.  Can anybody tell me what I can change to get the dvds back?  Does 8.1 even use fstab or does it find some other way to mount the drives?

Thanks

---

### Post by alienexplorers on 2008-11-04
My fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=182c66b4-ed87-4eec-9bd9-afebae097ee3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb7
UUID=74d55a7f-49eb-4a65-b1b8-12db46dc75c5 /home           ext3    relatime        0       2
# /dev/sdb5
UUID=2eac46be-ff76-48e4-bbd2-9e8e14c97699 none            swap    sw              0       0
# /dev/sdb1
UUID=11e5a808-45f5-41fb-8b43-5f2a8af9016d /media/disk     ext3    relatime        0       2
# /dev/sdb2
UUID=9f76cfa0-091f-4940-8be3-fc46fe85e283 /media/disk-1   ext3    relatime        0       2
# /dev/sda1
UUID=4CA7-E543                            /media/windows  vfat    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8  0       0
```

---

