---
title: "[SOLVED] How can I mount my OpenSolaris partition in Ubuntu?"
date: 2008-07-04
forum: Other OS Talk
---

### Post by the8thstar on 2008-07-04
Hello,

I'm looking for a way to (auto)mount my OpenSolaris partition in Ubuntu. However, the instructions I followed on a tutorial do not work

For clarification, 

> root@the8thstar-laptop:/home/the8thstar# sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dda30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         811     6514326   83  Linux
/dev/sda2             812        5776    39881362+  83  Linux
/dev/sda3   *        5777        8528    22105440    7  HPFS/NTFS
/dev/sda4            8529        9729     9647032+  bf  Solaris


> root@the8thstar-laptop:/home/the8thstar# dmesg | grep sda
[   20.728848] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   20.728861] sd 2:0:0:0: [sda] Write Protect is off
[   20.728864] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.728879] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.728924] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   20.728933] sd 2:0:0:0: [sda] Write Protect is off
[   20.728936] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.728951] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.728954]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   20.810366]  sda1 sda2 sda3 sda4
[   20.840595]  sda4: <solaris: [s0] sda5 [s1] sda6 [s2] sda7 [s8] sda8 >
[   20.840738] sd 2:0:0:0: [sda] Attached SCSI disk
[  106.616026] EXT3 FS on sda1, internal journal
[  107.255618] EXT3 FS on sda2, internal journal

The command *mount* doesn't work either:

> mount -t ufs -o ro /dev/sdaX /mnt (X is either 5, 6, 7 or 8 in this example)
mount: wrong fs type, bad option, bad superblock on /dev/sda8,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Am I missing some packages?

How can I edit *fstab* to do an automount for me?

Also, is there a way to include to have Grub recognize this partition?

---

### Post by the8thstar on 2008-07-04
Bump

---

### Post by logos34 on 2008-07-04
where's your swap?

maybe these threads will help:
[http://ubuntuforums.org/archive/index.php/t-442358.html](http://ubuntuforums.org/archive/index.php/t-442358.html)
[http://www.linuxquestions.org/questions/solaris-opensolaris-20/mount-solaris-partition-in-fc7-602167/](http://www.linuxquestions.org/questions/solaris-opensolaris-20/mount-solaris-partition-in-fc7-602167/)

---

### Post by the8thstar on 2008-07-04
I don't use ANY swap. I don't use Hibernation and I have 2Gb of RAM, so a swap file is not really needed here.

---

### Post by logos34 on 2008-07-04
ok, I see

---

### Post by cardinals_fan on 2008-07-04
I don't know whether Ubuntu can mount ZFS   *googles*

---

### Post by D-EJ915 on 2008-07-04
Solaris uses slices which are different than usual partitions, if it's even possible it'll be difficult because there's a swap slice and actual data slice inside that solaris partition.

---

### Post by cammin on 2008-07-05
> **D-EJ915 said:**
> Solaris uses slices which are different than usual partitions, if it's even possible it'll be difficult because there's a swap slice and actual data slice inside that solaris partition.

Ubuntu sees the slices as partitions sda5 - sda8.

---

### Post by cammin on 2008-07-05
Apparantly you need the zfs module for the fuse filesystem.
[http://www.wizy.org/wiki/ZFS_on_FUSE](http://www.wizy.org/wiki/ZFS_on_FUSE)

seems to be the project page for that. 

[http://www.linux.com/feature/138452](http://www.linux.com/feature/138452)

should give you enough info on how to get it set up.

---

### Post by the8thstar on 2008-07-06
I believe I need to recompile the kernel to get UFS support. Any ideas on how I could achieve that?

---

### Post by cardinals_fan on 2008-07-06
There seems to be a lot of uncertainty about what file system you're using.  Is it ZFS or UFS?

---

### Post by D-EJ915 on 2008-07-06
> **cardinals_fan said:**
> There seems to be a lot of uncertainty about what file system you're using.  Is it ZFS or UFS?
If it's the booting partition it's not ZFS

---

### Post by the8thstar on 2008-07-13
Well, nevermind. I removed OpenSolaris altogether because I had too many problems with Grub and with wireless connections. So long... So I'm back to dual booting Ubuntu and Windows for now.

---

### Post by Bachstelze on 2008-07-13
Solaris is not BSD. Thread moved.

---

### Post by unisol on 2008-07-18
try here; [http://www.faqs.org/docs/Linux-mini/Linux+Solaris.html](http://www.faqs.org/docs/Linux-mini/Linux+Solaris.html) i hope it helps.

---

