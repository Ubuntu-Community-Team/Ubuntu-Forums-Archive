---
title: "Hard drives not visible"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by mikee55 on 2013-05-25
Hello all, 2 harddrives appear in bios, but not in Ubuntu 13.04

```

 sudo sfdisk -luS

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *      2048  58361855   58359808  83  Linux
/dev/sdb2      58363902  62531583    4167682   5  Extended
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty
/dev/sdb5      58363904  62531583    4167680  82  Linux swap / Solaris

Disk /dev/sdc: 1008 cylinders, 63 heads, 62 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1   *        32   3933119    3933088   e  W95 FAT16 (LBA)
		start: (c,h,s) expected (0,0,33) found (0,1,1)
		end: (c,h,s) expected (1006,59,26) found (481,254,32)
/dev/sdc2       3934208   3940351       6144  83  Linux
		start: (c,h,s) expected (1007,13,61) found (482,34,1)
		end: (c,h,s) expected (1008,50,4) found (482,225,32)
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty
tux@tux-OEM:~$ 
```
Can you sort me please? :-)

Much obliged,Mike

---

### Post by grahammechanical on 2013-05-25
Are you going to tell us or do we have to guess? Is the print out not reporting sda and sdd? What is on those disks? What file system? Have you tried the Disks utility?

---

### Post by lethall1 on 2013-05-25
Never used sfdisk, but what's wrong? You have 2 HDD
sdb and sdc

---

### Post by mikee55 on 2013-05-25
Got knackered drives :-) thanks all the same!

---

