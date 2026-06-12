---
title: "[SOLVED] Is this safe to do?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-09-09
I was wanting to optimize Ubuntu for my laptop. One of the things I wanted to do is to change my fstab. My current fstab looks like ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/Barnaby-root
UUID=1e82593f-7158-47cc-a02d-b6bb7d3cecde /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=addb0a65-9a4c-4bbf-a596-4022750e9253 /boot           ext3    relatime        0       2
# /dev/mapper/Barnaby-swap_1
UUID=2a2b8e0c-55c1-43e5-9823-bc6ba1190ca7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
But I want to change it to ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/Barnaby-root
UUID=1e82593f-7158-47cc-a02d-b6bb7d3cecde /               ext3    defaults,data=writeback,noatime,errors=remount-ro 0       1
# /dev/sda1
UUID=addb0a65-9a4c-4bbf-a596-4022750e9253 /boot           ext3    relatime        0       2
# /dev/mapper/Barnaby-swap_1
UUID=2a2b8e0c-55c1-43e5-9823-bc6ba1190ca7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
I would also like to know what all of the options mean, if you can.

---

### Post by caljohnsmith on 2008-09-09
I think you will find this link helpful:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by oldos2er on 2008-09-09
Just make a backup copy of your current fstab.

---

### Post by hyper_ch on 2008-09-09
in the terminal, run

```

man fstab

```

---

### Post by slughappy1 on 2008-09-18
NOT AT ALL SAFE!!! Completely broke my system.

---

