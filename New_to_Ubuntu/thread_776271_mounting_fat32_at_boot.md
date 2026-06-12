---
title: "mounting fat32 at boot"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by boeding on 2008-04-30
I was wondering if you can add a hdd to mount at boot with out editing the fstab file. If not I have this and was wondering what to edit.
I have one hdd that is partitioned into XP Pro, Ubuntu 8.04, and then a data partition.

boeding@boeding-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=182efffe-fd4d-4a55-a1a5-77f6b562bfa6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=73c223ef-ab57-4562-bead-37d2c688c0ca none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Any help would be great.

P.S. I'm really new to terminal so in depth details would be very helpful.

Boeding

---

### Post by bobplano on 2008-04-30
If you don't want to edit your fstab, you can add a startup session with a mount command. it is under System>preferences>sessions, and click the add button under startup programs. then fill in a name and comment and the command
```
sudo mount /dev/(the partition you want to mount) [where you want to mount it to]
```

---

### Post by jken146 on 2008-04-30
[http://www.psychocats.net/ubuntu/mountwindows#fat32](http://www.psychocats.net/ubuntu/mountwindows#fat32)

---

### Post by boeding on 2008-04-30
Alright I have the hdd mounting at boot, but I am unable to write to the disc, I can only read to it. The line I added to the fstab file is:

/dev/sda5 /media/DATA vfat defaults 0 0

as I understand it that should grant the owner (me) read write capability, but I have read only access. What should I do now?

Boeding

---

