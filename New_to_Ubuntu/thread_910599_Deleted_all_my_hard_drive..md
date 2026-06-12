---
title: "Deleted all my hard drive."
date: 2008-09-04
forum: New to Ubuntu
---

### Post by xwhisper on 2008-09-04
I "accidentally" deleted all my partitioning. Now it shows only unpartitioned space in GParted. I was playing with GParted and wanted to add new partition that was not formatted. I didn't formatted anything else. But now everything is gone. I didn't used any format and never hit Apply button. I hope that it is reading partition info wrong. Is there any way to restor it or I'm f****d up?

GParded now reads /dev/hdb/  Free space 41110 MB

---

### Post by Peter09 on 2008-09-04
Gparted will show you the status to be AFTER you hit the apply button. You may still be able to backout if you don't apply the partion scheme.

---

### Post by cariboo on 2008-09-04
If you have access  to another computer you may want to download this:

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

This should help you recover your deleted partitions.

Jim

---

### Post by halitech on 2008-09-04
> **xwhisper said:**
> I "accidentally" deleted all my partitioning. Now it shows only unpartitioned space in GParted. I was playing with GParted and wanted to add new partition that was not formatted. I didn't formatted anything else. But now everything is gone. I didn't used any format and never hit Apply button. I hope that it is reading partition info wrong. Is there any way to restor it or I'm f****d up?

GParded now reads /dev/hdb/  Free space 41110 MB

if you didn't click apply, you should be able to just close gparted and your partitions should still be there. Did you run gparted from System - Admin - Partition editor or from a live cd?

---

### Post by xwhisper on 2008-09-05
Administrator mode
Damn, I don't want to lose data

Thank you anyway!

---

### Post by Sef on 2008-09-05
Get [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").  It can help you recover your partitions.  Use only the live cd or another computer, do not use the hard drive that has been affected.  You will have better results if you do.

---

### Post by iaculallad on 2008-09-05
> **xwhisper said:**
> Administrator mode
Damn, I don't want to lose data

Thank you anyway!

Try using [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover those deleted partitions.

---

