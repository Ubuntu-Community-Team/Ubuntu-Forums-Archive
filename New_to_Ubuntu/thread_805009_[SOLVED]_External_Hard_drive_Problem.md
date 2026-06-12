---
title: "[SOLVED] External Hard drive Problem"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Sheneron on 2008-05-23
I am trying to get some files off an external hard drive I have, but I am getting an error message. It says Unable to mount the volume.  I have used a different hard drive and it worked fine.  Can anyone tell me how to fix this?

---

### Post by bumanie on 2008-05-23
It has probably been incorrectly removed form a windows machine. Plug it back into windows and go through the correct shutdown procedure. This is the usual cause of external devices not mounting.

---

### Post by anystupidname on 2008-05-23
-in a terminal type
```
tail -f /var/log/messages
```
-plug the drive in and you'll see something like
```
...scsi9 : SCSI emulation for USB Mass Storage devices...
sd 9:0:0:0: [sdd] 505856 512-byte hardware sectors
sd 9:0:0:0: [sdd] Write Protect is off
 sdd: sdd1
sd 9:0:0:0: [sdd] Attached SCSI removable disk
sd 9:0:0:0: Attached scsi generic sg3 type 0
```
-take note of the "sdd: sdd1" (yours might be sdb: sdb1 hdc2 or whatever...)
-create a folder (ctrl-c to exit previous tail follow command)
```
mkdir /mnt/external
``` (for example)
-mount the partition from your drive to it (I'm assuming there is only one)
```
mount /dev/sdb1 /mnt/external
``` (if you get some weird response from the mount command it may be that the external drive's partition is in an unrecognizable format or broken or mount just needs some parameters) (try "man mount")
-your drive contents is now available at /mnt/external/*

---

### Post by Sheneron on 2008-05-23
thank ye

---

