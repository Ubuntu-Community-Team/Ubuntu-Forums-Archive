---
title: "mdadm and Drive Concencation in Ubuntu"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by stuart264 on 2008-11-13
I was reading up earlier on mdadm but I am unsure how to get started and the "How To"'s on the web seem a bit vague

Right now my Ubuntu Box sits idle a lot of the time, I use it for heavy number crunching, additional storage and to run media files through Mediatomb to my Linksys Kiss box but over the last few months I have "obtained" a few extra ide hard drives through salvaging parts from old pc's etc.

Is it possible to get mdadm to achieve a software raid concencation solution so I can combine the space on the following drives into 1 drive thus eliminating the problems I keep having with moving files between the drives for space reasons.

I have installed a 1 x 200gb SATA I Drive, 2 x 40gb IDE Drives and 1 x 60gb IDE drive which in theory if I could use raid to concencate the drives would give me 340gb storage space and get rid of the problems with one drive getting full and me having to move files around, I know the easy solution would be to buy a 1TB drive for my Windows box, swap it for on of the 500gb drives and put a 500gb drive in my Linux box but to be honest I am broke right now and with Christmas on the horizon it would be a nice stopgap solution until the New Year when I can afford to do the above.

TIA Stuart.

My drives are set up as below

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4750490

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23569   189317961   83  Linux
/dev/sda2           23570       24321     6040440    5  Extended
/dev/sda5           23570       24321     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10dc121b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cb274

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4865    39078081   83  Linux

Disk /dev/sdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dd721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        7297    58613121   83  Linux

---

