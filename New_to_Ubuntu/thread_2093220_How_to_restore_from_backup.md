---
title: "How to restore from backup"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by crashdogy on 2012-12-10
Ok i login to root do ls and i have a backup.tar.gz file but cant get it to run and restore system and there is also a fullsystem backup directory  ?    Runing ubuntu 11.10 server

---

### Post by mlentink on 2012-12-10
A compressed tar-file is not executable. Use the tar-command to extract the archive.
See:
```
man tar
```

---

### Post by crashdogy on 2012-12-10
Thank you for fast reply

I'm a noob so what is the command 

man tar backup.tar.gz. ?

Then once is extracted how do i excut it?

---

### Post by steeldriver on 2012-12-10
STOP

Seriously

Unless you know EXACTLY how the backup was created, you are almost certainly going to hose your system

A .tar.gz file is a compressed (with gzip) tar archive - basically like a winzip archive. If you extract it as root without knowing what path it was created relative to, you are VERY likely to hose files all over your system and make it unbootable.

At the very least you should list the archive contents first so you can decide how to proceed

```
tar -ztf backup.tar.gz
```You DO NOT need to be root to do that

---

### Post by crashdogy on 2012-12-10
Ok  put the backup.tar.gz on a usb extracted it is there a whey to do a restore from the usb drive it was a full backup of the whole drive   ?

---

### Post by crashdogy on 2012-12-10
Ok put the backup.tar.gz on a usb extracted it.  is there a whey to do a restore from the usb drive it was a full backup of the whole drive or can i do a mass copy?

---

