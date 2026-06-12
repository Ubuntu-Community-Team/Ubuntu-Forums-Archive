---
title: "trying to install Ubuntu and fix/reclaim ssd"
date: 2023-08-03
forum: New to Ubuntu
---

### Post by mkhas on 2023-08-03
Hi, I'm trying to install Ubuntu because I was having problems with my ssd and I heard it's possible to recover bad sectors and run with minimal space here. Problem is however, I can't even detect my SSD now, even though I'm on a laptop. Sometimes it will appear and sometimes it won't and after the install failed earlier I can't seem to find it anymore. So the installer can't find it and  fdisk, gparted and disks can't detect it either. Is there any way I can fix or recover it?

---

### Post by yancek on 2023-08-03
Does it show in the BIOS?  It is possible the drive is bad, they don't last forever.  You can't really 'fix' drives with bad sectors.  What happens is bad sectors are marked so the system does not try to use them.  Have you tried to run fsck on the partitions on that drive?  If not, that would be the  first step.

---

### Post by mkhas on 2023-08-03
No, the drive doesn't show in the BIOS either, or rather, sometimes it shows and sometimes it doesn't.

---

### Post by ActionParsnip on 2023-08-03
Have you checked the connections to it are solid? Maybe a different power cable if it has one

---

### Post by mkhas on 2023-08-03
Ok it has showed up in the bios again, running the disk check in the disks utility says the hard drive itself is fine, so I'm guessing the connections to it might be the problem? we'll see

---

### Post by MAFoElffen on 2023-08-03
I would do a long test on it via smartmontools...

Something along the lines of
```

sudo smartctl -t long /dev/sdX

```
replacing "X" with the designation of the drive. package smartmontools is not installed by default.

That way you cqan check the drive via it's own firmware for errors that it finds. It the error count is high, then do nto trust that it will stay at only those errors.

Also, if it is popping in and out of being found, it may be either a loose connection or a failing controller on the drive, using smartctl will see those errors and log them.
```

sudo smartctl -l error /dev/sdX

```

---

