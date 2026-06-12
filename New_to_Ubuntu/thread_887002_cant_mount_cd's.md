---
title: "cant mount cd's"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Existance0 on 2008-08-11
```
sudo mount /media/cdrom0/ -o unhide
[sudo] password for arie: 
mount: No medium found

```

---

### Post by alienexplorers on 2008-08-11
Try:
> sudo mount /dev/scd0 /media/cdrom0

---

### Post by Existance0 on 2008-08-11
```
sudo mount /dev/scd0 /media/cdrom0 
[sudo] password for arie: 
mount: special device /dev/scd0 does not exist

```

I think its only dvd's now I put a cd in and it ran fine but dvd's dont.

---

### Post by JohnMac on 2008-08-12
What did you do?
I get the "no media" message and nothing I do can change it!!

---

### Post by bumanie on 2008-08-12
Check /etc/fstab to ensure the device has a mount point. Post output of > cat /etc/fstab

---

### Post by aimpau on 2008-08-12
Is this a laptop wherein you have to connect your CD drive?

---

### Post by Existance0 on 2008-08-12
> **bumanie said:**
> Check /etc/fstab to ensure the device has a mount point. Post output of
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=692c3bc6-d3db-4bc7-a737-c6bf35eebd71 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=6f9f5d76-f8f3-46ac-ae28-fd41e77e47bf none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```
> **aimpau said:**
> Is this a laptop wherein you have to connect your CD drive?

No its a desktop.

---

### Post by bumanie on 2008-08-12
There is a mount point for the cd-rom drive, however it is not /dev/scd0 as you tried mounting it is > /dev/hda        /media/cdrom0 

---

### Post by Existance0 on 2008-08-12
```
sudo mount /dev/hda /media/cdrom0 
mount: No medium found

```

---

### Post by Existance0 on 2008-08-12
:(

---

### Post by bumanie on 2008-08-12
/etc/fstab looks as though the drive is mounted correctly, I can't understand why it doesn't see the media. You say it works with cd's but not dvd's > I think its only dvd's now I put a cd in and it ran fine but dvd's dont.Logically, it would seem that the drive is at fault. It is mounted correctly, it plays cd's OK, but not dvd's - maybe the laser has seen better days. The 'pits' that are read on a dvd are much smaller and spaced closer than on a cd, hence the 6x + extra capacity on a dvd. Lasers do fail sometimes. You could brrow a dvd-rom from from a friend and see if that works - if it does it would virtually prove your drive has seen better days - you would have to make a directory/mount point to mount the borrowed drive to.

---

### Post by JohnMac on 2008-08-17
You make anything of this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=798f91d4-a724-48f4-879d-340f6e5d635c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2e059f74-802c-4490-9d79-18b885b3faa0 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
john@john-desktop:~$

---

