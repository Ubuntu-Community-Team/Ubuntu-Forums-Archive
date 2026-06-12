---
title: "external hard drive problem"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by blake7 on 2013-03-21
what does this mean 

Error mounting /dev/sdb2 at /media/wil/New Volume: Command-line `mount -t "vfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush" "/dev/sdb2" "/media/wil/New Volume"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ps how does this web page become so ugly ?

---

### Post by fantab on 2013-03-22
Looks like a corrupted HDD or corrupted filesystem on it. 

Does the External HDD work on windows? If you have an access to a windows machine use "[Check Disk]("http://technet.microsoft.com/en-us/magazine/ee872427.aspx")" to the check and repair the filesystem. We can also use "fsck" from ubuntu but 'Check Disk' will be a better option since its vfat.

---

