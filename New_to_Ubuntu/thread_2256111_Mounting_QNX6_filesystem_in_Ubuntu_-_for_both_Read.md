---
title: "Mounting QNX6 filesystem in Ubuntu - for both Read ad Write"
date: 2014-12-09
forum: New to Ubuntu
---

### Post by sheran2 on 2014-12-09
Hi,

I'm trying to mount a QNX6 filesystem in Ubuntu 14.4. It only gets mounted  as Read Only.

I tried below

sudo mount -o rw -t qnx6 /dev/xyz /mnt/cf

Any Help reagrding this?
Does Ubuntu not support writing to QNX6 filesystem?

Regards
Sheran

---

### Post by sandyd on 2014-12-10
> **sheran2 said:**
> Hi,

I'm trying to mount a QNX6 filesystem in Ubuntu 14.4. It only gets mounted  as Read Only.

I tried below

sudo mount -o rw -t qnx6 /dev/xyz /mnt/cf

Any Help reagrding this?
Does Ubuntu not support writing to QNX6 filesystem?

Regards
Sheran
The kernel driver [seems to only support read-only mounting]("http://cateee.net/lkddb/web-lkddb/QNX6FS_FS.html")

---

