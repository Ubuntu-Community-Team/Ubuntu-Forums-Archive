---
title: "USB pendrive doesn't work on Ubuntu"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Horizon101 on 2008-10-05
Hi,

I've installed Ubuntu 8.04(Hardy) inside Windows.
When I plug my pendrive on to Ubuntu, it does not auto detect my pendrive and the pen drive icon is not shown on the desktop.
Earlier, when I have installed Ubuntu on a seperate Hard disk the pendrive worked fine.
(It works well on windows.)

How can i set Ubuntu to autodetect USB external storage devices??

Thanks in advance for any suggestions.

---

### Post by Stefanie on 2008-10-05
so you installed Ubuntu using Wubi? i don't have any experience with wubi but if you post the output of ```
sudo fdisk -l
``` (run this command in a terminal window) we can see if the device is detected by ubuntu, but not mounted.

---

### Post by Horizon101 on 2008-10-06
Thanks a lot for replying

I ran the command and this was the output

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe66be66

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4997    40138371    7  HPFS/NTFS

---

### Post by drowner on 2008-10-06
Stupid question, but was the USB pendrive plugged in when you gave that command?

---

### Post by Horizon101 on 2008-10-09
yes, it was plugged in.

---

### Post by Stefanie on 2008-10-10
weird. it doesn't seem like the drive is being recognized. are you sure you posted the whole output? when you run the command again, do you see any other lines than /dev/sda1?

---

### Post by Horizon101 on 2008-11-01
Hi,

I ran the command again while the USB is plugged in to the system. This was what i got.

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe66be66

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/sdb: 1027 MB, 1027604480 bytes
16 heads, 32 sectors/track, 3920 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x3eae3a4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3920     1003504    b  W95 FAT32


But still the pendrive is not shown on the desktop or in the "places" menu.

---

### Post by dominik_ap on 2008-12-04
Hi I have the same problem... I am using Ubuntu maybe 1.5 year and normally the USB was working...
But now something happened and when I put my Pen drive to USB nothing happens...

output of sudo fdisk -l:
Disk /dev/sda: 80,0 GB, 80,026,361,856 bajt&#367;
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 9,729
Jednotky = cylindry po*16065 * 512 = 8,225,280 bajtech
Identifikátor disku:&#8239;0x000a41d1

Za&#345;ízení Zavád&#283;t   Za&#269;átek       Konec    Bloky    Id  Systém
/dev/sda1               1        1602    12867187+  83  Linux
/dev/sda2            4866        9729    39070080    7  HPFS/NTFS
/dev/sda3   *        1603        4724    25077465   83  Linux
/dev/sda4            4725        4865     1132582+   5  Roz&#353;í&#345;ený
/dev/sda5            4725        4865     1132551   82  Linux swap/Solaris

Diskové oddíly jsou chybn&#283; se&#345;azeny

and output of dmesg is:
[  340.889490] usb 5-1: new high speed USB device using ehci_hcd and address 11
[  341.022691] usb 5-1: configuration #1 chosen from 1 choice
[  366.177960] usb 5-1: USB disconnect, address 11
[  555.817342] usb 5-1: new high speed USB device using ehci_hcd and address 12
[  555.950330] usb 5-1: configuration #1 chosen from 1 choice


if i make cat /proc/partitions
it shows only my HDD:
major minor  #blocks  name

   8     0   78150744 sda
   8     1   12867187 sda1
   8     2   39070080 sda2
   8     3   25077465 sda3
   8     4          1 sda4
   8     5    1132551 sda5


So can somebody help me? I can't use sudo mount -t vfat /dev/sda5 /media/usb 
and automount of Ubuntu also doesn't start..


Thanks

Dominik Franek

---

### Post by ushills on 2008-12-04
I am having the same issue under 8.04, drives shows in places where i can mount but does not automount.

Was working fine last week, perhaps an update changed things.

---

### Post by vishvesh on 2010-01-25
hi all,
   I am using Ubuntu 9.10 and am facing the same issue. My machine was detecting my pen drive before but it doesn't do it anymore.

I get this on sudo fdisk -l
> 


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002c8cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13       19457   156191962+   5  Extended
/dev/sda5              13         510     4000153+  82  Linux swap / Solaris
/dev/sda6             511       19457   152191746   83  Linux

Disk /dev/sdb: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders
Units = cylinders of 160 * 512 = 81920 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          51       49600     3963968    b  W95 FAT32



---

### Post by Grenage on 2010-01-25
Have you tried formatting the drive?  Assuming sdb/sdb1 is your USB drive (for the love of God, make sure):

```
sudo fdisk /dev/sdb
```

d (delete partition)
n (new partition)
p (primary partition)
1 (partition number)
Press return for defaults on the next two (cylinder range)
t (type of partition)
c (FAT32 type)
w (write changes and quit)

Then format the drive with:

```
sudo mkdosfs -F 32 /dev/sdb1
```

Take it out, and plug it back in.

---

### Post by vishvesh on 2010-03-11
It worked fine after formatting. The issue was with the pen-drive. Thanks

---

