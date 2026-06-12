---
title: "Ubuntu 20.04 =&gt; 20.10 upgrade"
date: 2020-10-24
forum: New to Ubuntu
---

### Post by johannes-lichtenberger on 2020-10-24
Hi,

I wanted to upgrade my Ubuntu from 20.04 to 20.10 yesterday. However, it failed and now after rebooting I can't log-in again. The filesystem is mount as read-only.

I tried the following to remount it:

*mount -o remount,rw /dev/mapper/ubuntu--vg-root /*, but I'm getting

*mount: /lib/x86_64-linux-gnu/libmount.so.1: version `MIUNT_2_35` not found (required by mount)*

I'm really lost. Can I somehow get Ubuntu into a bootable state again or do I have to reinstall everything?

kind regards
Johannes

---

### Post by columbarium on 2020-10-24
Sometimes there could be a filesystem corruption... Have you tried checking the integrity of the filesystem?
This seems like a good tutorial: [https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/](https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/)

---

