---
title: "New install: How do I set up fstab to automount 2 ext3 partitions?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by marcelo danico on 2008-05-19
I did a clean install of 8.04. Now my old home folders are on 2 ext3 partitions.
I've mounted them and tried out my files, everything is good.:)
Now I need to know what to enter into /etc/fstab to automount sda7 and sda5.

> daniel@daniel-desktop:/home$ sudo fdisk -l
[sudo] password for daniel: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007077

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1706    13703413+  83  Linux
/dev/sda2            1707        2080     3004155   82  Linux swap / Solaris
/dev/sda4            2081        9729    61440592+   5  Extended
/dev/sda5            4591        8293    29744284+  83  Linux
/dev/sda6            8294        9714    11414151   83  Linux
/dev/sda7            2081        4590    20161512   83  Linux
/dev/sda8            9715        9729      120456   83  Linux

Partition table entries are not in disk order


I already used mkdir for /home1 and /home2 folders in /mnt

so to automount and get unrestricted access (777?) to the files in the partitions what do I enter to fstab?

---

### Post by EXCiD3 on 2008-05-20
Pretty straightforward. Something like:

```
[B]/dev/sda5              /mnt/home1          ext3    defaults        1 1
[/B]**/dev/sda7              /mnt/home2 ext3    defaults        1 1**
```

Also read up on fstab so you know what you are doing. An excellent reference: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by marcelo danico on 2008-05-20
Thank you.

---

