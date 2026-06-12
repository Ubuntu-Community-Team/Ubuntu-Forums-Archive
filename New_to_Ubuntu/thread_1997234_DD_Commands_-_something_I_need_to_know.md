---
title: "DD Commands - something I need to know"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by Jack Nitro on 2012-06-04
I need to format one of my drives in order to reinstall Windows 7 on it. The installation is corrupted and won't boot. First, however, I want to preserve the contents of the drive, and the best way I figure to do that is using the dd command. I've been referencing [this thread](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/), but first I need to know - 

```
dd if=/dev/sda2 of=/dev/sdb1 bs=4096 conv=notrunc,noerror
```

If I run this, will Linux erase all of the data on partition /dev/sdb1 and replace it with the data from /dev/sda2 or will it just use the free space? I need to know because there *is* data on /dev/sdb1

p.s. don't know if this really belongs in absolute beginners - if not...sorry.

---

### Post by cariboo on 2012-06-04
dd will overwrite anything that is on the partition/disk

---

### Post by idoitprone on 2012-06-04
> **Jack Nitro said:**
> I need to format one of my drives in order to reinstall Windows 7 on it. The installation is corrupted and won't boot. First, however, I want to preserve the contents of the drive, and the best way I figure to do that is using the dd command. I've been referencing [this thread]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/"), but first I need to know - 

```
dd if=/dev/sda2 of=/dev/sdb1 bs=4096 conv=notrunc,noerror
```If I run this, will Linux erase all of the data on partition /dev/sdb1 and replace it with the data from /dev/sda2 or will it just use the free space? I need to know because there *is* data on /dev/sdb1

p.s. don't know if this really belongs in absolute beginners - if not...sorry.

use gparted. it is so much easier to use

---

