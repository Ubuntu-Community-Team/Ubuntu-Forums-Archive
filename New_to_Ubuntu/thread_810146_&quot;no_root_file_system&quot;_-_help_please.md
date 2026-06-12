---
title: "&quot;no root file system&quot; - help please"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Ryan_Z/28 on 2008-05-28
Hi guys.

I am an absolute noob to linux and am currently trying to dual-boot Ubuntu (i also have XP).

I have created an 80GB Ext2 partition (is Ext3 better?) and when i try to install it comes up with the error message:
"no root file system"

Anyone know what to do?

Thanks

---

### Post by drkameleon on 2008-05-28
For Linux, you have to specify at least 2 partitions. One main partition used for the filesystem and one minor (~1-2GB) used as swap.

When you create that main partition, you must then mount it to "root" (Edit partition -> Mount point = "/") so that Linux starts building the filesystem tree starting from there... So just edit it, when partitioning and that SHOULD work. You could also (for upgradeability...) create another partition to use as /home (where a normal Linux user stores his own data). So...

1st Partition : 20 GB - ext3 - Mount Point = / (root)
2nd Partition : 58 GB - ext3 - Mount Point = /home
3rd Partition : 2 GB  - Linux swap

P.S. I think ext3 is better...

---

