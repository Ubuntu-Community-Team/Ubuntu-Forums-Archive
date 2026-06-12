---
title: "Partition table entries are not in disk order"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by rsnow on 2008-07-23
Results of running fdisk -l: Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0af4f56c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12750   102414343+  83  Linux
/dev/sdb2           12751       38913   210154297+   5  Extended
/dev/sdb5           19320       32096   102631252+  83  Linux
/dev/sdb6           38726       38913     1510078+  82  Linux swap / Solaris
/dev/sdb7           12751       19319    52765429+  83  Linux

Partition table entries are not in disk order

Will this work? If not what do I need to change?

---

### Post by Joeb454 on 2008-07-23
Will it work for what?

Could you be a little more descriptive

---

### Post by rsnow on 2008-07-23
When it said the partition tables were not in disk order I thought it might be indicating that I could not install a linux distro to that hard drive and that I would need to make some changes before I could do that.

---

### Post by cjv8888 on 2008-07-23
That is a standard phrase in everybody's fdisk -l
Don't worry about it.

---

### Post by rsnow on 2008-07-23
OK, thanks.

---

### Post by bodhi.zazen on 2008-07-23
gparted seems to do this and I don't know about you, but it drives me crazy :)

<enter command line> This is easily fixed. You do not need to fix it (this "problem is not harming your system in any way).

sudo fdisk /dev/sdxy

at the menu type x (for expert menu) ; m to list commands

fix -> exit -> write changes to disk -> exit fdisk

Reboot -> viola

---

### Post by rsnow on 2008-07-24
Followed instructions - fdisk reported  everything now in order. Thanks

---

