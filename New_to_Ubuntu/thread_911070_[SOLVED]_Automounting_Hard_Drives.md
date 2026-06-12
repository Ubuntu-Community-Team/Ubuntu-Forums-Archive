---
title: "[SOLVED] Automounting Hard Drives"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by SpongeBob SquarePants on 2008-09-05
Afternoon chaps,

I'm interested in my NTFS drives mounting automatically. Currently my fstab file looks like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2426e977-1002-46f4-9839-d0007ba663b3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=fe581416-8c20-47d4-ac6d-523649c850a2 /home           ext3    relatime        0       2
# /dev/sda6
UUID=2294b177-9d7f-4a68-a32a-ff3b8adcbefa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

What I'd like however is /dev/sdb1 to automount at start up. I'm reasonably familiar with messing around with fstab. But I'm not used to working with UUID numbers. It's normally just a case of changing "noauto" to "auto". So what do I need to do?

Cheers.

---

### Post by drs305 on 2008-09-05
Get the UUID of /dev/sdb1:
```
sudo blkid | grep sdb1
```
Make sure you have a mountpoint (example sdb1). Ownwership of the /mountpoint/files is set at mounting.
```

sudo mkdir /media/sdb1

```
Backup and edit fstab:
```

cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab

```
Add this line - insert UUID and change /media/sda1 to whatever your mountpoint is. GID 100 is group *users*,  46=*plugdev*, 1000 is normally *your* group:
```

UUID=enterUUIDnumberhere /media/sdb1 ntfs-3g uid=1000,gid=100,umask=022 0 0

```
Remount /dev/sdb1:
```

sudo umount /dev/sdb1
sudo mount /dev/sdb1

```

If you would like to use a gui fstab editor and for more information on mounting, refer to the link in my signature line for SDM.

---

### Post by alienexplorers on 2008-09-05
Please Read this;
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by SpongeBob SquarePants on 2008-09-05
Worked a treat drs. Thanks a lot :)

---

### Post by SpongeBob SquarePants on 2008-09-05
> **alienexplorers said:**
> Please Read this;
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

Hi there,

Thanks for the link, but I wanted something more specific to working with UUID's. It's all sorted now though, but thanks anyway.

---

