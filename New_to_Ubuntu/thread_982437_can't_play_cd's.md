---
title: "can't play cd's"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by davarse on 2008-11-14
hey all, i've been running ubuntu from 7.10 on my laptop acer aspire 5920
i had a problem on hardy that i my computer can't recognize or play cd's,, it's bit weird because it plays dvds and data cd...
after i upgraded to ibex the problem is still there..
does anyone have any suggestion whats happen here? could it be fix? or maybe is there any audio file that went missing? i dont really know about computer much...
much appreciate to your help
davarse

---

### Post by MasterSander on 2008-11-14
can you post the output of 
```
 cat /etc/fstab 
```

It could be that your cdrom isn't mounted at startup

---

### Post by davarse on 2008-11-14
> **MasterSander said:**
> can you post the output of 
```
 cat /etc/fstab 
```

It could be that your cdrom isn't mounted at startup
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ca3d0417-8bec-460a-a041-2aa47fde4f77 /               ext3    noatime,nodiratime,errors=remount-ro,data=writeback,relatime 0       1
# /dev/sda5
UUID=c4b61b77-23ad-4e92-a876-ab20e47e2397 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by davarse on 2008-11-15
is that possible anything to do with the hardware?

---

