---
title: "Silly Question"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by manij on 2008-08-10
Can I have the Same version of HARDY installed on two different partitions on two different drives in the same 'puter. Here is my fdisk -l out put

[B][I]Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3161    25390701   83  Linux
/dev/sda2           14180       19452    42355372+   b  W95 FAT32
/dev/sda3            3162        3416     2048287+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84788478

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3187    25599546   83  Linux
/dev/sdb2            3188        3442     2048287+  82  Linux swap / Solaris
/dev/sdb3            3443        5995    20506972+  83  Linux
/dev/sdb4            5996       14593    69063435    b  W95 FAT32

[/I][/B]

I'm not able see the linux installation in SDA1 in the grub menu. It is hardy, same as the one in sdb1

Help!

thanks

Mani

---

### Post by Elfy on 2008-08-10
Yes you can - you can add it to the menu list if it isn't there. You don't need 2 swaps though.

---

### Post by ugm6hr on 2008-08-10
Yes.

But here's another silly question.... Why?

---

### Post by Elfy on 2008-08-10
I used to have 2 feistys after I'd reinstalled twice - 1 for not breaking and 1 for breaking :)

---

### Post by hyper_ch on 2008-08-10
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

