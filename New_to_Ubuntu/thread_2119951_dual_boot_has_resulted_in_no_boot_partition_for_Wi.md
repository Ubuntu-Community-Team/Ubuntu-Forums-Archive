---
title: "dual boot has resulted in no boot partition for Windows"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by KiwiDalang2 on 2013-02-25
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00045079

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760  1953523711   976510976   8e  Linux LVM

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd8e00465

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   977290203   488644078    7  HPFS/NTFS/exFAT
/dev/sdb2       977291262  1953523711   488116225    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5       977291264  1937575935   480142336   83  Linux
/dev/sdb6      1937577984  1953523711     7972864   82  Linux swap / Solaris

Disk /dev/mapper/kubuntu-root: 991.7 GB, 991734792192 bytes
255 heads, 63 sectors/track, 120571 cylinders, total 1936982016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/kubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/kubuntu-swap_1: 8162 MB, 8162115584 bytes
255 heads, 63 sectors/track, 992 cylinders, total 15941632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/kubuntu-swap_1 doesn't contain a valid partition table
```

---

### Post by Elfy on 2013-02-25
Please do not hijack other people's threads, just because your issue is similar - there is no guarantee specific fixes will work for you.

---

### Post by KiwiDalang2 on 2013-02-25
Wow, brutal welcome. Thanks for that.

---

### Post by bigmonmulgrew on 2013-02-25
Ok, First Welcome to the forum.

Nice to see a new face.

Secondly Elfy, How was he hijacking a thread when he's the first poster?

Can you give some more info about your system. Dual booting with XP?

Did you select guided when installing?
Could you have accidentally wiped Windows or do you think that just the boot partition is missing

---

### Post by Elfy on 2013-02-25
> **KiwiDalang2 said:**
> Wow, brutal welcome. Thanks for that.

There is a sensible reason we ask people not to post onto the end of someone else's thread.

While the issue may in fact appear to be the same, there is no guarantee that it is. People responding to the original poster are concentrating on that issue.

---

### Post by oldfred on 2013-02-25
May be best to see details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by KiwiDalang2 on 2013-03-02
Thanks for the info. As per above, I reinstalled from scratch.

---

