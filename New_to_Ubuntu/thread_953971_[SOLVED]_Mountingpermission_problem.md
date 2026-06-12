---
title: "[SOLVED] Mounting/permission problem"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Zorgoth on 2008-10-20
Hello.  I have the problem that I mounted a partition (containing a lot of data) in a folder (/shared), but it's contents can only be modified by root.  How do I give myself permission to edit this folder and its contents?  It is FAT32.

---

### Post by perlluver on 2008-10-20
Sounds like it is mounted through Fstab, if so use this code ```
sudo chown username /shared
``` obviously use your username there.

---

### Post by bodhi.zazen on 2008-10-20
> **perlluver said:**
> Sounds like it is mounted through Fstab, if so use this code ```
sudo chown username /shared
``` obviously use your username there.

LOL

Nope, that will not work. Fro FAT partitions you set ownership and permissions at the time of mounting.

See:

_Windows:_ [Psychocats Mount windows ]("http://www.psychocats.net/ubuntu/mountwindows")
For read-write: 
[LIST=1]
[*]vfat (FAT) use dmask=027,fmask=137[INDENT]more permissive permissions : dmask=000,fmask=111[/INDENT]
[*]ntfs use [ntfs-3g]("http://ubuntuforums.org/showthread.php?t=217009") and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)[INDENT][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/INDENT]
[/LIST]
[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Zorgoth on 2008-10-21
Thanks!  The second one worked (I think it was dmask=000, fmask=111).  The first one, however, did not...  It didn't give me read or write permissions.  However, with the second I'm fine.  Thanks.  I did something horrible to firefox just a moment ago, but I'll report that in another thread...

---

