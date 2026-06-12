---
title: "cdrom mounting problem"
date: 2014-03-18
forum: New to Ubuntu
---

### Post by jrhal65 on 2014-03-18
Error mounting system-managed device /dev/sr0: Command-line `mount "/mnt/ata-SONY_DVD_RW_DRU-V200A"' exited with non-zero exit status 32: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so        


 it plays with some cd but not cod 4

---

### Post by 7sbaV8Kt5PTh on 2014-03-19
You may want to try your mount command with the "-t auto" parameter to let it choose the CD filesystem, if it is not defined in /etc/fstab.  If you are using an older distro, use -t cdfs.

---

