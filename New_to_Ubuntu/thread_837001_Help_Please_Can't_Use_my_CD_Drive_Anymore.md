---
title: "Help Please: Can't Use my CD Drive Anymore?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by cklf0 on 2008-06-22
Hi. I am a newbie, installed Ubuntu 8.04 today to replace XP. Can no longer use my CD drive with a message of 'Unable to Mount Location No Media in the Drive'
Can someone please advise? I have tried looking for a similar forum answer but had no luck.
Thanks in advance!

---

### Post by fahadsadah on 2008-06-22
Please can you do a ```
sudo fdisk -l
``` in a Terminal (System->Accessories->Terminal, you will be asked for a password after typing the command) and paste the output here?

---

### Post by cklf0 on 2008-06-22
After much to and fro as Ubuntu system can't access internet at moment (until get CD working!), here it is...

carl@carl-desktop:~$ sudo fdisk -1 
[sudo] password for carl: 
fdisk: invalid option -- 1 

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table 
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s) 
       fdisk -s PARTITION           Give partition size(s) in blocks 
       fdisk -v                     Give fdisk version 
Here DISK is something like /dev/hdb or /dev/sda 
and PARTITION is something like /dev/hda7 
-u: give Start and End in sector (instead of cylinder) units 
-b 2048: (for certain MO disks) use 2048-byte sectors 
carl@carl-desktop:~$

---

### Post by Oldsoldier2003 on 2008-06-22
> **cklf0 said:**
> After much to and fro as Ubuntu system can't access internet at moment (until get CD working!), here it is...

carl@carl-desktop:~$ sudo fdisk -1 
[sudo] password for carl: 
fdisk: invalid option -- 1 

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table 
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s) 
       fdisk -s PARTITION           Give partition size(s) in blocks 
       fdisk -v                     Give fdisk version 
Here DISK is something like /dev/hdb or /dev/sda 
and PARTITION is something like /dev/hda7 
-u: give Start and End in sector (instead of cylinder) units 
-b 2048: (for certain MO disks) use 2048-byte sectors 
carl@carl-desktop:~$

the command flag is a lower case L not a "one" :)

---

### Post by cklf0 on 2008-06-22
sorry...did say I was a newbie :-)

carl@carl-desktop:~$ sudo fdisk -l 
[sudo] password for carl:  
Disk /dev/sda: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xa3b8a3b8 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       14405   115708131   83  Linux 
/dev/sda2           14406       14593     1510110    5  Extended 
/dev/sda5           14406       14593     1510078+  82  Linux swap / Solaris 
Disk /dev/sdb: 1059 MB, 1059323904 bytes 
2 heads, 63 sectors/track, 16420 cylinders 
Units = cylinders of 126 * 512 = 64512 bytes 
Disk identifier: 0x0022e6e0 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1       16421     1034480    6  FAT16 
carl@carl-desktop:~$

---

