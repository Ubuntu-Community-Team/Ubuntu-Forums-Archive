---
title: "mount problems"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by blairm on 2008-07-20
Hi,

Wanting to backup some stuff to an external hard drive but I'm unable to do so - getting the following error message:

hal-storage-removable-mount-all-options refused uid 1000

The external drive is ntfs - could that be the problem? Do have ntfs-3g installed.
I'm trying to do the backup from Gutsy kubuntu

Cheers,

Blair

---

### Post by blairm on 2008-07-20
Okay, googled some more and found a solution - for those who are having the same problem:

1) go to dolphin and click on storage media
2) right-click on the external drive you're having problems with and go to properties
3) click on the mounting tab and untick mount as user.

That has let me open and write to the disk.

Cheers,

Blair

---

