---
title: "[SOLVED] Lilo errors"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by theozzlives on 2008-08-13
WARNING!                                                                                                                                 Your /etc/fstab configuration file gives device                           UUID=f083413b-634b-4bed-9fa6-e7d1df5a10c0 as the root filesystem device.   
This doesn't look to me like an "ordinary" block device. Either your 
fstab is broken and you should fix it, or you are using hardware (such 
as a RAID array) which this simple configuration program does not handle.


I get this error when installing Lilo, My fstab is fine. sda1=boot, sda3=home, sda2-extended, and sda5=swap. Any ideas?

---

### Post by SkonesMickLoud on 2008-08-13
You could remove the UUID's and replace them with the partition names.  Make sure that you make a backup of fstab first.

---

