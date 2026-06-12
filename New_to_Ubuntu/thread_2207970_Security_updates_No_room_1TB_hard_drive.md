---
title: "Security updates No room 1TB hard drive"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by grewolf on 2014-02-26
I am using ubuntu 13.10 and I had encrypted the hard drive at install.  I am now trying to do security updates to the ubuntu base using the software updater and it is telling me that I have no hard drive space left.  I have used disk usage analyzer and disks.  It looks like the disk is partitioned and that I need to resize the partition.  Not sure how to do this without damaging the install.  I also receive this error from disk analyzer  Error mounting system-managed device /dev/fd0: Command-line `mount "/media/floppy0"' exited with non-zero exit status 32: mount: block device /dev/fd0 is write-protected, mounting read-only
mount: /dev/fd0: can't read superblock

---

### Post by zvacet on 2014-02-26
Run this command 

```
df -h
```

and post output here.

---

### Post by Impavidus on 2014-02-26
Most likely your /boot partition is full. There should be a separate /boot partition when you encrypt the hard drive. I believe on 13.10 you can autoremove old kernels. Best not to resize partitions if you can avoid it by removing files, especially on encrypted drives.

---

