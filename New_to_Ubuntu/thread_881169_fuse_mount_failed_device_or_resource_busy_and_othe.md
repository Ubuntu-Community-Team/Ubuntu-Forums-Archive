---
title: "* fuse: mount failed: device or resource busy* and others"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by lost_poet on 2008-08-05
>  fuse: mount failed: device or resource busy

is what i get when I try to access my partitions. It worked fine when I installed Ubuntu (Studio) and I remember this starting to happen when I first connected to my MacBook's SMB share. I didnt do anything else. Yes I did download a lot of codecs to play my media files, I hope that has got nothing to do with this.

Searching wasn't much help. Didnt find anything on Hardy. And the htfs-3g forum was too technical for me to understand. I have used Ubuntu before (the only linux i have ever used) but that was more than a year back so now I have forgotten most of it. hence a post in this section. i am fairly competent at following instructions and am not afraid of using the terminal (see, I know what it is! ;) )

I do have ntfs-config. but it didn't work. I have restarted a few times, hasn't worked.

One more thing is that my colour quality is low, prolly lower than millions of colours. the shades and gradients are far from smooth, if someone could tell me how to increase my colour depth...

also, i downloaded the volume control applet. it is sitting on my panel, but the main volume controls are of no use. I have to go and change it from the pcm/playback/which ever is applicable.

someone help me out please.

one more thing - kudos to the ppl who finally created support for my bug of a lan-card (the infamous silan sc92031 pci eth card). My network has been working perfectly now!:)


-------

Edit: Okay, I goto sleep and I wake up to find that now along with that error, it also says that I do not have the privileges to mount the device!!! WTF! Also, I see that some of my partitions are mounte under /media but in the properties dilogue box, it says under the permissions tab that I do not own them so i can't change the permissions! Okay now I am thoroughly confused! If i do not own files and partitions on my own PC, then who does?!
----------
Edit2: To top it all off, when i open the partition folders from the /media - it is all a blank. nothing in there. I can read from CDs and DVDs but that's about it. And now it permanently says that i do not have the privileges. I have checked my authorizations. I have allowed myself (!) but nothing's working. Currently in the process uninstalling ntfs-config and then will restart. les c. and then if nothing happens I will reinstall ntfs-config and again restart (although I am kinda unsure if restarting is all that necessary, may be it is my windows experience talking). Some clue anybody? Somebody?...

---

### Post by lost_poet on 2008-08-06
Okay, looks like I have found something. This is the result of (sudo) fdisk -l

I can't remember how i messed it up like this. Could someone tell me how to fix this?

> Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e797e79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         842     6763333+  83  Linux
/dev/sda2             974        7297    50797530    f  W95 Ext'd (LBA)
/dev/sda3             843         973     1052257+  82  Linux swap / Solaris
/dev/sda5             974        1946     7815591    7  HPFS/NTFS
/dev/sda6            1947        2875     7462161    7  HPFS/NTFS
/dev/sda7            2876        4378    12072816    7  HPFS/NTFS
/dev/sda8            4379        5594     9767488+   b  W95 FAT32
/dev/sda9            5595        6567     7815591    b  W95 FAT32
/dev/sda10           6568        7297     5863693+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e551e54

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         646     5188963+   7  HPFS/NTFS
/dev/sdb2             647        4865    33889117+   f  W95 Ext'd (LBA)
/dev/sdb5             647        1429     6289416    7  HPFS/NTFS
/dev/sdb6            1430        2734    10482381    7  HPFS/NTFS
/dev/sdb7            2735        3394     5301418+   7  HPFS/NTFS
/dev/sdb8   *        3395        4865    11815776    7  HPFS/NTFS

Disk /dev/dm-0: 6004 MB, 6004422144 bytes
255 heads, 63 sectors/track, 729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73696420

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   ?      119512      153402   272218546+  20  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(356, 97, 46) logical=(119511, 107, 3)
Partition 1 has different physical/logical endings:
     phys=(357, 116, 40) logical=(153401, 15, 41)
Partition 1 does not end on cylinder boundary.
/dev/dm-0p2   ?       82801      116350   269488144   6b  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 57) logical=(82800, 34, 61)
Partition 2 has different physical/logical endings:
     phys=(269, 101, 57) logical=(116349, 219, 8)
Partition 2 does not end on cylinder boundary.
/dev/dm-0p3   ?       33551      120595   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(33550, 137, 11)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(120594, 153, 54)
Partition 3 does not end on cylinder boundary.
/dev/dm-0p4   *       86812       86813       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(86811, 142, 3)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(86812, 225, 45)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-1: 8003 MB, 8003165184 bytes
255 heads, 63 sectors/track, 972 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(368, 111, 45) logical=(13577, 238, 11)
Partition 1 has different physical/logical endings:
     phys=(371, 101, 51) logical=(119521, 238, 60)
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(67, 115, 32) logical=(45381, 70, 3)
Partition 2 has different physical/logical endings:
     phys=(299, 114, 44) logical=(79242, 34, 29)
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(114, 111, 32) logical=(10498, 56, 41)
Partition 3 has different physical/logical endings:
     phys=(353, 115, 52) logical=(10498, 56, 40)
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          167628      167631       25817+   0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(167627, 190, 52)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(167630, 245, 26)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-2: 7641 MB, 7641252864 bytes
255 heads, 63 sectors/track, 928 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?       13578      119522   850995205   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(368, 111, 45) logical=(13577, 238, 11)
Partition 1 has different physical/logical endings:
     phys=(371, 101, 51) logical=(119521, 238, 60)
Partition 1 does not end on cylinder boundary.
/dev/dm-2p2   ?       45382       79243   271987362   74  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(67, 115, 32) logical=(45381, 70, 3)
Partition 2 has different physical/logical endings:
     phys=(299, 114, 44) logical=(79242, 34, 29)
Partition 2 does not end on cylinder boundary.
/dev/dm-2p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(114, 111, 32) logical=(10498, 56, 41)
Partition 3 has different physical/logical endings:
     phys=(353, 115, 52) logical=(10498, 56, 40)
Partition 3 does not end on cylinder boundary.
/dev/dm-2p4          167628      167631       25817+   0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(167627, 190, 52)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(167630, 245, 26)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-3: 12.3 GB, 12362563584 bytes
255 heads, 63 sectors/track, 1502 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-3p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-3p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-3p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-3p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-4: 10.0 GB, 10001908224 bytes
255 heads, 63 sectors/track, 1215 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-4p1   ?       48437      119493   570754815+  72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-4p2   ?       10501      131013   968014120   65  Novell Netware 386
Partition 2 does not end on cylinder boundary.
/dev/dm-4p3   ?      116395      236907   968014096   79  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-4p4   ?      179626      179629       27749+   d  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-5: 8003 MB, 8003165184 bytes
255 heads, 63 sectors/track, 972 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73696420

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-5p1   ?      119512      153402   272218546+  20  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(356, 97, 46) logical=(119511, 107, 3)
Partition 1 has different physical/logical endings:
     phys=(357, 116, 40) logical=(153401, 15, 41)
Partition 1 does not end on cylinder boundary.
/dev/dm-5p2   ?       82801      116350   269488144   6b  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 57) logical=(82800, 34, 61)
Partition 2 has different physical/logical endings:
     phys=(269, 101, 57) logical=(116349, 219, 8)
Partition 2 does not end on cylinder boundary.
/dev/dm-5p3   ?       33551      120595   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(33550, 137, 11)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(120594, 153, 54)
Partition 3 does not end on cylinder boundary.
/dev/dm-5p4   *       86812       86813       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(86811, 142, 3)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(86812, 225, 45)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-6: 5313 MB, 5313498624 bytes
255 heads, 63 sectors/track, 645 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-6p1   ?       13578      119522   850995205   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(368, 111, 45) logical=(13577, 238, 11)
Partition 1 has different physical/logical endings:
     phys=(371, 101, 51) logical=(119521, 238, 60)
Partition 1 does not end on cylinder boundary.
/dev/dm-6p2   ?       45382       79243   271987362   74  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(67, 115, 32) logical=(45381, 70, 3)
Partition 2 has different physical/logical endings:
     phys=(299, 114, 44) logical=(79242, 34, 29)
Partition 2 does not end on cylinder boundary.
/dev/dm-6p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(114, 111, 32) logical=(10498, 56, 41)
Partition 3 has different physical/logical endings:
     phys=(353, 115, 52) logical=(10498, 56, 40)
Partition 3 does not end on cylinder boundary.
/dev/dm-6p4          167628      167631       25817+   0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(167627, 190, 52)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(167630, 245, 26)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-7: 6440 MB, 6440361984 bytes
255 heads, 63 sectors/track, 782 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-7p1   ?       13578      119522   850995205   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(368, 111, 45) logical=(13577, 238, 11)
Partition 1 has different physical/logical endings:
     phys=(371, 101, 51) logical=(119521, 238, 60)
Partition 1 does not end on cylinder boundary.
/dev/dm-7p2   ?       45382       79243   271987362   74  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(67, 115, 32) logical=(45381, 70, 3)
Partition 2 has different physical/logical endings:
     phys=(299, 114, 44) logical=(79242, 34, 29)
Partition 2 does not end on cylinder boundary.
/dev/dm-7p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(114, 111, 32) logical=(10498, 56, 41)
Partition 3 has different physical/logical endings:
     phys=(353, 115, 52) logical=(10498, 56, 40)
Partition 3 does not end on cylinder boundary.
/dev/dm-7p4          167628      167631       25817+   0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(167627, 190, 52)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(167630, 245, 26)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-8: 10.7 GB, 10733958144 bytes
255 heads, 63 sectors/track, 1304 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-8p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-8p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-8p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-8p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-9: 5428 MB, 5428652544 bytes
255 heads, 63 sectors/track, 659 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-9p1   ?       13578      119522   850995205   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(368, 111, 45) logical=(13577, 238, 11)
Partition 1 has different physical/logical endings:
     phys=(371, 101, 51) logical=(119521, 238, 60)
Partition 1 does not end on cylinder boundary.
/dev/dm-9p2   ?       45382       79243   271987362   74  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(67, 115, 32) logical=(45381, 70, 3)
Partition 2 has different physical/logical endings:
     phys=(299, 114, 44) logical=(79242, 34, 29)
Partition 2 does not end on cylinder boundary.
/dev/dm-9p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(114, 111, 32) logical=(10498, 56, 41)
Partition 3 has different physical/logical endings:
     phys=(353, 115, 52) logical=(10498, 56, 40)
Partition 3 does not end on cylinder boundary.
/dev/dm-9p4          167628      167631       25817+   0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(167627, 190, 52)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(167630, 245, 26)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-10: 12.0 GB, 12099354624 bytes
255 heads, 63 sectors/track, 1470 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

      Device Boot      Start         End      Blocks   Id  System
/dev/dm-10p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-10p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-10p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-10p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


I can't access any of my data, so I am beginning to get slightly hysterical. Please help.

---

### Post by lost_poet on 2008-08-06
it has been solved...for now. I did a clean install! so for now it is all peachy! Will mark it as solved as soon as I get back to full steam and if everything still holds up.

---

