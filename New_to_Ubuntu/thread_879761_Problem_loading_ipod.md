---
title: "Problem loading ipod"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by pkj on 2008-08-04
Hi,
Was using ipod until now (via floola or gtkpod)
On connecting with the USB port the ipod icon used to appear on screen.

However, due to some problem, the icon does not appear anymore nor does the ipod gets detected by Floola...

Seems something wrong with the software..

How do i detect the ipod and format/reinstall the software...

pkj

---

### Post by django0909 on 2008-08-04
You said Floola doesn't detect the ipod...does gtkpod detect it?

Did this happen after an update?

---

### Post by pkj on 2008-08-04
No none of them are detecting it...
As on yesterday, i had used both and was able to access the ipod and its songs..everything was working fine till yesterday...

Problem seems to be with the ipod...without it getting detected how do i access it or re-format/repair it

pkj

---

### Post by phidia on 2008-08-04
With the ipod plugged in open a terminal and enter > sudo fdisk -l
Does the disk appear in the output?

---

### Post by pkj on 2008-08-04
NO..It does'nt

output is as follows
Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         766     6152863+   7  HPFS/NTFS
/dev/hdc2             767        4865    32925217+   f  W95 Ext'd (LBA)
/dev/hdc5             767        3057    18402426    7  HPFS/NTFS
/dev/hdc6            3058        4865    14522728+   7  HPFS/NTFS

Disk /dev/hdd: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1         249     2000061   82  Linux swap / Solaris
/dev/hdd2             250        2681    19535040   83  Linux
/dev/hdd3            2682        4870    17583142+  83  Linux


I run a dual boot system..That's why the win partition...

pkj

---

### Post by gjoellee on 2008-08-04
I have the same problem..this is my output:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4dfe4df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14406   115716163+  83  Linux
/dev/sda2           14407       14593     1502077+   5  Extended
/dev/sda5           14407       14593     1502046   82  Linux swap / Solaris

---

