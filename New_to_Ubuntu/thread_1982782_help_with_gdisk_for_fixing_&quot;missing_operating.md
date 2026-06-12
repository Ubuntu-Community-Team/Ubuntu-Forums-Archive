---
title: "help with gdisk for fixing &quot;missing operating system&quot; on Mac"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by Wedontplay on 2012-05-19
Hi, after installing ubuntu 12.04 on a macbook pro 6,2 when i try to boot the linux partition with refit i have the message "missing operating system".

I read from a post that i should fix my MBR using gdisc, i have just some doubts:

When i have to choose the partition to add to the hMBR accordly to my setup what partition should i add? 

Linuxboot is the 1 mb partition that linux created on install to put the biosgrub in.
Linux is the partition in with i installed ubuntu

the post says:

>  
For all but the Linux-Root, accept the defaults and always choose 'N' for not boot. For Linux-Root  choose "83" (fs-type: Linux) and 'Y' to boot. (*)


In my case the linux root is the 43.8g partition isn't it?

```


Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0x000059CF
MBR partitions:

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1       409639   primary     0xEE
   2      *         409640    881433247   primary     0xAF
   3             881433248    882702783   primary     0xAB
   4             882704384    884961279   primary     0x82

Recovery/transformation command (? for help): p
Disk /dev/disk0: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 0000594E-3EDB-0000-8C0C-00001F690000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 1622 sectors (811.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       881433247   420.1 GiB   AF00  Customer
   3       881433248       882702783   619.9 MiB   AB00  Recovery HD
   4       882704384       884961279   1.1 GiB     8200  Swap
   5       884961280       884963233   977.0 KiB   EF02  LinuxBoot
   6       884963234       976773118   43.8 GiB    0700  Linux



```


Thanks 

Gabriele

---

