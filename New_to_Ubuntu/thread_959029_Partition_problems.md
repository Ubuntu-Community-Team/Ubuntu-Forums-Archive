---
title: "Partition problems"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by technosinner on 2008-10-26
Hi.

I have partition/HDD two-fold question: When I mount a partition and try to get it to mount at boot, why won't my system accept to mount by Partition ID? The reason I want this - second part to the quesiton - is because I've noticed my three drives don't always have the same identifier (sda1, 2, 3).  Why is that?

We're talking about a mix of ext3 and NTFS partitions.

Thanks
ts

---

### Post by em4r1z on 2008-10-26
You might want to use labels or UUID for the partitions/hard drives and edit your filesystem table. Read this:
[http://bbs.archlinux.org/viewtopic.php?pid=440069](http://bbs.archlinux.org/viewtopic.php?pid=440069)

---

