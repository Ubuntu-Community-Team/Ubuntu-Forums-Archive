---
title: "Ubuntu not booting after installed"
date: 2017-07-30
forum: New to Ubuntu
---

### Post by iamazon on 2017-07-30
Hey, I'm new to linux, and i was trying to install
Ubuntu. After it was done, it had told me to restart.
After i restarted, nothing was booting up, I had chose
to remove windows 10 to install ubuntu. I need some help,
and help would be great!
```
Disk /dev/loop0: 1.5 GiB, 1553670144 bytes, 3034512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 07BE6FCB-0B05-4F02-8CA4-B10DD815A2B8

Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2  937709568 938881023   1171456   572M Linux filesystem
/dev/sda3  938881024 976771071  37890048  18.1G Linux swap
/dev/sda4    1050624 937709567 936658944 446.6G Linux filesystem

Partition table entries are not in disk order.

```

I also tried to use boot-repair, (as I heard it could help repair Ubuntu),
but it did not work also.

EDIT: Below is my device information:
```
 Device Information

Model:  ATA TOSHIBA DT01ACA0
Serial:  94M1RBGAS
Size:    465.76 GiB
Path:    /dev/sda

Partition table: gpt
Heads:           255
Sectors/track:   63
Cylinders:       60801
Total sectors:   976773168
Sector size:     512 
```

I also tried to install from USB.

---

### Post by oldfred on 2017-07-30
Post link from the Summary Report that Boot-Repair creates.

What brand/model system? What video card/chip?

---

### Post by johndough2 on 2017-07-31
Hi

Lets hope you can try and undo the damage with clonezilla on a new media device like USB...

Based on Partclone (default), Partimage (optional), ntfsclone (optional), or dd to image or clone a partition. However, Clonezilla, containing some other programs, can save and restore not only partitions, but also a whole disk. 

AND I would consider whether you really meant to get rid of windows, or try and bring it back with the above option.

ALSO I note a swap partition of 18.1 gigabytes  (should be half to maybe 2 gigabytes) and a main file partition of 572 MEGAbytes, should be somewhere around the 12 - 20 GIGAbytes and perhaps a separate HOME of 250 Gb.

So I suggest either you try and recover windows or redo Ubuntu completely.

If in doubt please ask.

---

### Post by lammert-nijhof on 2017-07-31
That boot repair programme never worked, when I needed it. If you want to keep Windows, try to correct the Windows situation with you Windows DVD and the boot repair options of that DVD? Afterwards install Ubuntu again; Try to read how to dual boot Ubuntu on PCs with UEFI, there might be a problem, but I'm not familiar with it, because I don't use UEFI. 
Use the following partitions:
- Ubuntu 25GB including Home
- Swap size equal to your memory size, but not more the 4GB.
- Remainder a NTFS data partition, since that is useable for both Windows and Ubuntu.

Another option is to repair Windows or install Ubuntu and to install the other OS in a Virtual Machine using Virtualbox. It runs almost as fast as on the real HW. The only exception are games, that run considerably better on the real GPU/HW.

---

