---
title: "[SOLVED] new harddrive, editing FSTAB help"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by rabidninjawombat on 2008-06-13
Heh.. i should be be an expert at this by now. :) 

I installed a new 500 gigabyte SATA drive in my system, (currently unallocated and unformatted. I still have my two current on the IDE channel. For reference here is my fstab file. 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=f52792a5-0355-4ae2-b53c-0cc12d7d3a77 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=604144a8-65b7-44e2-9150-43c209f1f493 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /mnt/multimedia  ext3  user,rw,exec,auto  0  0

```

now here is where my quest lies, it appears when i installed the new hard drive, that my devices were reallocated,  The file system now appears to be on sdc1,  my multimedia partition appears to be on sdb1, and the new drive appears on sda1.   

Now i should mention that the file system is working just fine and i can boot into ubuntu no problem. (typing this from it now)  despite the fstab file appear to be wrong. So im kinda scared to edit the:

```
# /dev/sdb1
UUID=f52792a5-0355-4ae2-b53c-0cc12d7d3a77 /               ext3    relatime,errors=remount-ro 0       1
```

line to reflect the new location... also i would need to edit the 

```
/dev/sda1       /mnt/multimedia  ext3  user,rw,exec,auto  0  0

```

line to get it to mount correctly. 

Any harm in me doing this or am i just being paranoid?

---

### Post by rabidninjawombat on 2008-06-13
Hah ok all figured out myself.. im a bit slow :)

Just realized that the 

```
# /dev/sdb1
```

line is commented out so it doesnt matter whats put there :) 

but i did correct the assignment of my Multimedia drive.. and works fine now.

---

