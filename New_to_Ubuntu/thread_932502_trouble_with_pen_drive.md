---
title: "trouble with pen drive"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by nnjond on 2008-09-28
There's a padlock on my .trash folder and Ubuntu now claims my pen drive is read only?

---

### Post by Pro-reason on 2008-09-28
The .trash folder on the pen drive?

With the pen drive inserted, post the output of:

```

sudo blkid
cat /etc/fstab
mount

```

(That's three separate commands.  I need all of them.)

---

### Post by nnjond on 2008-09-29
Thanks for your interest.

nick@nick-desktop:~$ sudo blkid
[sudo] password for nick: 
/dev/sda1: UUID="d2cde2b7-321f-4db5-888a-eaf52aa5f66d" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="892c3006-824a-9fa7-1a23-63503cd3b37d" 
/dev/sdb1: UUID="4842-C799" TYPE="vfat" 
/dev/sda3: UUID="addc5919-5aff-48af-b534-0c4e43f914c7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: SEC_TYPE="msdos" UUID="48B1-AE88" TYPE="vfat" 
nick@nick-desktop:~$

---

