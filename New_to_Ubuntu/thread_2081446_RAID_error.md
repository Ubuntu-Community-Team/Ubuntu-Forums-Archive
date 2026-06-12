---
title: "RAID error"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by myantivirus2008 on 2012-11-06
HI everybody,
From past two days we guys was trying to install Ubuntu 12.04 LTS on a Intel Made 2U rack Unit.
But Ubuntu disk was always asking us to select the path to install the grub boot-loader.
after many unsuccessful attempts, we finally gone through it & installed the OS.

But after installation when system is booting it is showing following error massage.
[B][COLOR=Lime]
[COLOR=Red]-------------------------- Error Code-----------------------------------[/COLOR][/COLOR][/B]
 [COLOR=Purple]**Ubuntu login: [ 10.810009] XFS (dm-4): metadata I/O error: block 0x1d21db00 (“xfs_trans_read buf”)**[/COLOR]
  [COLOR=Purple]**Error 5 but count 4096**[/COLOR]
  [COLOR=Red]**------------------------------ End  -------------------------------------**[/COLOR]

------------------System & Partitioning details---------
this machine configuration is as follows::
procesor: 2 Intel Xeon Processors
RAM: 64 GB
HDD: 1.3 TB x 3 ( all disk are clubbed ina RAID 5 array, of combined capacity 3 TB)

As we want to run this system for visualization, I done the following partition scheme:::
/boot::100 MB   ( ext4)
/ :: 30 GB  ( ext 4)
/var ::500 GB  (XFS journal File System)
Swap Area :: 160 GB  ( Swap Area)
Recovery boot Area :: 2 MB ( suggested by Ubuntu Installation )
----------------------------------- END of this section----------------

so can anybody help me to resolve above error?
Your help will be highly appreciated.

---

