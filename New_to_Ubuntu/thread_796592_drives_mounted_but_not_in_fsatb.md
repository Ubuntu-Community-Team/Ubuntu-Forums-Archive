---
title: "drives mounted but not in fsatb???"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by buntu_noob on 2008-05-16
Here is a copy of my fstab

# /etc/fstab: static file system information.
> #
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=acd94fe1-af02-4605-bbe8-b08f9b40b23a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=5c1d7474-54a2-45ca-ba40-e21d95b0095e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


the problem is that I have three hard drives, this seems to only be showing the one. The other two drives however are appearing on the desktop and seem to be working fine. However, my write privileges are not defined, and I am therefore not able to share folder on this drive using samba. 
So, in short how can these drives not be in my fstab but still be usable, (for the most part)? I want o make these drive privileges and set the write previlages so that they can be shared, any thoughts?

---

### Post by buntu_noob on 2008-05-16
problem solved, just manually mounted in fstab, works fine

---

