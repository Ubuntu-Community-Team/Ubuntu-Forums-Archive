---
title: "Mounting"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Aoshi99 on 2008-09-06
The following error occurs when I'm trying to mount an ISO file (sudo mount -o loop -t iso9660 /home/aoshi/windows/civ3.iso /media/iso/):

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Any ideas?

---

### Post by orpheus07 on 2008-09-06
try doing this:

**```
dmesg | tail
```**

to find out what the log says...

---

### Post by Bölvaður on 2008-09-06
Do you use normal mount for mounting ISO files?

I thought mount was used for hardware and some programs for ISO images.

---

### Post by Aoshi99 on 2008-09-06
> 
try doing this:

Code:

dmesg | tail



to find out what the log says... 


bash: dmseg: command not found


> 
Do you use normal mount for mounting ISO files?

I thought mount was used for hardware and some programs for ISO images. 


I think it doesn't matter if it's hardware or software...

---

### Post by malathion on 2008-09-06
> **Aoshi99 said:**
> bash: dmseg: command not found

Check your spelling :)

---

### Post by Aoshi99 on 2008-09-06
dmesg | tail
[   47.507719] NET: Registered protocol family 10
[   47.508099] lo: Disabled Privacy Extensions
[   47.605340] eth0: no IPv6 routers present
[   85.276315] loop: module loaded
[   85.414552] ISOFS: Unable to identify CD-ROM format.
[  155.641365] ISOFS: Unable to identify CD-ROM format.
[  418.984969] UDF-fs: No VRS found
[ 1828.739952] ISOFS: Unable to identify CD-ROM format.
[ 3317.686382] ISOFS: Unable to identify CD-ROM format.
[ 7345.692424] ISOFS: Unable to identify CD-ROM format.

---

