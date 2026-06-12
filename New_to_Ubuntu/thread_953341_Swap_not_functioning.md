---
title: "Swap not functioning"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by ajorb11 on 2008-10-20
I can't seem to get my swap working correctly.  Here is some info that hopefully will help someone out.  Let me know if you want to see additional things
```

aaron@aaron-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1489564     728764     760800          0      22816     340620
-/+ buffers/cache:     365328    1124236
Swap:      7807580          0    7807580
aaron@aaron-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1454        711        742          0         22        332
-/+ buffers/cache:        356       1097
Swap:         7624          0       7624

aaron@aaron-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=2ed96994-726e-425a-9e7d-69e9598dc926 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=4a589f5e-d76d-4337-80ea-8756149623b3 /home           ext3    relatime        0       2
# /dev/sda1
UUID=64ef385a-880f-499d-851c-56256b73d90a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

aaron@aaron-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x154e154d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            8758        9729     7807590   82  Linux swap / Solaris
/dev/sda2   *        7299        8757    11719417+  83  Linux
/dev/sda3               1        7298    58621153+  83  Linux
Partition table entries are not in disk order

```

I tried remaking my swap as suggest at [https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq") in 2.2
under trouble shooting; and got the following error.
```

aaron@aaron-laptop:~$ sudo swapoff -a

aaron@aaron-laptop:~$ sudo /sbin/mkswap /dev/sda1
Setting up swapspace version 1, size = 7994966 kB
no label, UUID=438ba0e1-f8a4-41ec-9950-42f993ff1ddb


```

Help towards fixing this is greatly appreciated.

---

### Post by Sef on 2008-10-20
1) Moved to absolute beginners.

2) Your swap is not needed at this time; hence, it is not being used.

---

### Post by billgoldberg on 2008-10-20
aaron@aaron-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1489564     728764     760800          0      22816     340620
-/+ buffers/cache:     365328    1124236
Swap:      7807580          0    7807580


You still have ram memory, hence swap will not kick in.

Swap is used when you are out of ram memory.

---

### Post by oldos2er on 2008-10-20
"Help towards fixing this is greatly appreciated."

 As others have pointed out, there's nothing to fix. Can you explain why you think your system should be using swap? RAM is far, far faster; so you would definitely notice a slowdown if your system was using swap.

 From the URL you posted:

**Help!** The swap is not being used! When I issue the free command, it shows something like this: 
tom@tom:~$ free
             total       used       free     shared    buffers     cached
Mem:        515980     448664      67316          0      17872     246348
-/+ buffers/cache:     184444     331536

Swap:       674688          0     6746881- First try, if it is because the system cannot use swap or because it just does not need it. Start many memory consuming applications (e.g. Gimp, web browsers, [OpenOffice]("https://help.ubuntu.com/community/OpenOffice") etc) and then issue the free command again. Is swap being used now?

---

