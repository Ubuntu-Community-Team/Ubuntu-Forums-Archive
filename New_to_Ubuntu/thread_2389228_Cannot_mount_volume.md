---
title: "Cannot mount volume"
date: 2018-04-13
forum: New to Ubuntu
---

### Post by balliekeith on 2018-04-13
Hi,

I get a 'cannot mount volume' message when inserting a cd/dvd

Invalid mount option when attempting to mount the volume 'UDF volume'.

What do i do to fix this>?

---

### Post by TheFu on 2018-04-13
Welcome to the forums.

Which file system does the cd/dvd have since it doesn't appear to be using UDF?
Many CDs and/or DVDs are using a data format that is iso9660.  Try mounting using that as the file system option.
Music CDs may use a different file system and I'm not certain what video DVDs use, but I think it is ISO9660 just with a specific directory structure and encryption for commercial discs.

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768) has info on a bug in 16.04 which a tiny group of people have reported. Might not be relevant to you.  I haven't had issues mounting DVD discs on 14.04 or 16.04 systems myself.

[https://help.ubuntu.com/stable/ubuntu-help/video-dvd.html](https://help.ubuntu.com/stable/ubuntu-help/video-dvd.html) helps with video DVDs.
[https://help.ubuntu.com/stable/ubuntu-help/disk-partitions.html](https://help.ubuntu.com/stable/ubuntu-help/disk-partitions.html) is general information about disks and partitions, including optical discs.

To get better help, the exact format for the discs needs to be provided.

---

