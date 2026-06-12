---
title: "Not enough disk space"
date: 2013-08-11
forum: New to Ubuntu
---

### Post by rajivt on 2013-08-11
I have installed Ubuntu 12.04.2 LTS on a 8GB USB stick. Tried to install software upgrades, but got a message saying "unable to install upgrades due to insufficient disk space". Properties shows that I have used less than 1GB, therefore should have 7GB left. Can some one please help. Thanks.

---

### Post by The-Server-4dmin on 2013-08-11
Do a ```
df -h
``` on the command line and let us see it please.

---

### Post by rajivt on 2013-08-11
ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            1.9G   71M  1.8G   4% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           766M  944K  765M   1% /run
/dev/sdb1       7.4G  1.4G  6.0G  19% /cdrom
/dev/loop0      663M  663M     0 100% /rofs
tmpfs           1.9G   44K  1.9G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  148K  1.9G   1% /run/shm
ubuntu@ubuntu:~$

---

### Post by ibjsb4 on 2013-08-11
> Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        36G  3.4G   31G  10% /
udev            995M  4.0K  995M   1% /dev
tmpfs           401M  744K  400M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M  148K 1002M   1% /run/shm
none           1002M   38M  964M   4% /tmp/guest-LSm2dW


Thats what mine looks like; yours is strange.  Is this a wubi install?

---

### Post by Bucky Ball on 2013-08-11
> **ibjsb4 said:**
> Is this a wubi install?

Indeed, because a full Ubuntu install is going to use more than 1Gb.

---

