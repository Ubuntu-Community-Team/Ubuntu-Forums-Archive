---
title: "Fail to boot into Ubuntu 14.04.5 LTS"
date: 2017-11-02
forum: New to Ubuntu
---

### Post by mackiiiii on 2017-11-02
My old laptop has refused to boot after shut down and I believe my hard drive might have given up on me. After powering on I get the message "Operating system not found". I read a couple of forums and a suggestion was to boot from a USB and run the repair-boot application. After this I tried to reboot and see if I could boot from my HDD, but I was not able to. As instructed by repair-boot I am pasting the diagnostic generated. [http://paste.ubuntu.com/25875482/](http://paste.ubuntu.com/25875482/)

Any help with this would be greatly appreciated. Thanks!

---

### Post by Bashing-om on 2017-11-02
mackiiiii; Hello - Welcome to the forum .

Ouch ! only device seen is the USB drive as sda .. no internal drive seen .

So, when booting up does bios see the hard drive(s) ?

What does the system see ? From the liveUSB post back the results of terminal commands:
```

sudo fdisk -lu
sudo blkid

``` as we try and get another look at things .

[INDENT]bad things can happen and
[INDENT][INDENT][INDENT]no hardware last forever
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mackiiiii on 2017-11-02
Thanks for the reply! 

> **Bashing-om said:**
> 

So, when booting up does bios see the hard drive(s) ?



I believe BIOS does not see the hard drive, almost everything except USB and DVD show as N/A.

Output from fdisk -lu:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2003 MB, 2003795968 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3913664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x60dfafa1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           0     2156351     1078176    0  Empty
/dev/sda2         2135488     2140031        2272   ef  EFI (FAT-12/16/32)

WARNING: GPT (GUID Partition Table) detected on '/dev/sda1'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda1: 1104 MB, 1104052224 bytes
255 heads, 63 sectors/track, 134 cylinders, total 2156352 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x60dfafa1

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           0     2156351     1078176    0  Empty
/dev/sda1p2         2135488     2140031        2272   ef  EFI (FAT-12/16/32)

```

Output from blkid:

```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="Ubuntu 14.04.5 LTS amd64" TYPE="iso9660" 
/dev/sda2: SEC_TYPE="msdos" UUID="8432-2FF8" TYPE="vfat" 

```

Thanks again!

---

### Post by Bashing-om on 2017-11-02
mackiiiii; Yukkie poo !

Nope not seen . As bios also does not see the drives - "Houston we have a problem" .

So, at this point you are looking at swapping out the hard drive as the more expedient thing to try .
a) No power to the drive from the PSU
b) no data from the mainboard sata controller
c) bad disk controller
d) no power to the disk motor 
amongst what else might be.

Maybe a easy as a bad connection ? maybe a bad sata cable ?

[INDENT][INDENT]hate when this happens
[/INDENT][/INDENT]

---

### Post by mackiiiii on 2017-11-02
Yeah... As I was reading more the pastebin I slowly realized the drive was missing completely. I don't have any experience swapping parts or checking connections, so I think I'll take it to a repair shop and see if they can do something, I just wanted to be sure it warranted it. I guess eventually hardware dies even if you try to keep it from doing it. Thanks a lot!

---

### Post by Bashing-om on 2017-11-02
mackiiiii; K :(

Let us know how it goes - 

-keep the forum clean-

---

