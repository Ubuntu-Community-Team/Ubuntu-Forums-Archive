---
title: "Partioning help"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by AprilFool on 2008-09-15
I dual booted Vista and Ubuntu a while back, and now I've stopped using Vista as a whole, so I want to delete the Vista partition, but I need to resize and enlarge my Ubuntu partition to hold some files I still use from the Vista partition. I have already made some unallocated space on my hard drive, and here is some (hopefully) useful information about my partitions-

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x73fd3f7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36942   279280968+   7  HPFS/NTFS
/dev/sda2           37958       40829    21703815   83  Linux
/dev/sda3           40829       41346     3903795   82  Linux swap / Solaris

```

---

### Post by shoot2kill on 2008-09-15
have you tried booting from a live cd, and running
```

sudo gparted

```

---

### Post by AprilFool on 2008-09-15
Nope, but I will right after this message. I'll edit this post and tell you if it works.
EDIT: So far so good, although it is taking a LONG time, longer than Vista's partitioner.

---

### Post by shoot2kill on 2008-09-15
and dont forget to back up any important documents before doing this process, just in case... :/

---

