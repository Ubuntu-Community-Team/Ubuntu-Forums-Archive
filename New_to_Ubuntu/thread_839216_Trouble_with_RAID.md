---
title: "Trouble with RAID"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Lano on 2008-06-24
Alrighty then, I'm having a REALLY hard time getting Ubuntu to recognise my raid arrays.

Specs:
Asus P5K-E Board
Intel ICH9R
2x 320gig HDD's,
30 gig mirrored (raid 1), the rest (290ish gig) striped (raid 0).

Ubuntu (Heron) is installed to an 80gig USB hard drive, not to the RAID drives.

I've installed DMRAID, and had a fiddle but cannot get it to recognise the RAID's. The mirrored RAID shows up (twice) in Computer, indicating that it isn't being recognised as a RAID. I also get a "fuse: Mount Failed: Device or resource busy" error when trying to mount either of them.

I've done a few hours of Googling, and couldn't find anything that would help me. Most of the guides I've come across are for people wishing to install to raid arrays, which I don't wish to do. I don't want to destroy or modify the arrays, I just want to be able to read and write to them.

(These aren't sequentially occurring commands, just the way they've been copied and pasted):

j@woo:~$ sudo dmraid -r
/dev/sdb: isw, "isw_dccjiecgjd", GROUP, ok, 625142445 sectors, data@ 0
/dev/sda: isw, "isw_dccjiecgjd", GROUP, ok, 625142445 sectors, data@ 0

j@woo:~$ sudo mkdir /data
j@woo:~$ sudo mount /dev/mapper/isw_dccjiecgjd_stripe /data
mount: /dev/mapper/isw_dccjiecgjd_stripe already mounted or /data busy

j@woo:~$ sudo dmraid -ay
RAID set "isw_dccjiecgjd_Mirror" already active
RAID set "isw_dccjiecgjd_stripe" already active
RAID set "isw_dccjiecgjd_Mirror1" already active
RAID set "isw_dccjiecgjd_stripe1" already active




Any ideas? :D Thanks

---

### Post by gtdaqua on 2008-06-24
Looks like the array has already been mounted.

what is the output of:

```

sudo fdisk -l
sudo mount -l

```

---

### Post by Lano on 2008-06-24
Thanks for your help gtdaqua.
Here are the outputs:

j@woo:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b023b01

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3914    31439173+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b023b01

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3914    31439173+   7  HPFS/NTFS

Disk /dev/dm-0: 32.2 GB, 32212389888 bytes
255 heads, 63 sectors/track, 3916 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b023b01

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1        3914    31439173+   7  HPFS/NTFS

Disk /dev/dm-1: 575.7 GB, 575711477760 bytes
255 heads, 63 sectors/track, 69992 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b4e3b4d

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1               1       69992   562210708+   7  HPFS/NTFS

Disk /dev/dm-2: 32.1 GB, 32193713664 bytes
255 heads, 63 sectors/track, 3913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-2p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-2p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-2p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-3: 575.7 GB, 575703765504 bytes
255 heads, 63 sectors/track, 69991 cylinders
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

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd04cc0ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris




j@woo:~$ sudo mount -l
/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/j/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=j)

---

### Post by gtdaqua on 2008-06-25
How did you initially partition your drives?

---

### Post by Lano on 2008-06-25
The RAIDs are pre-existing XP partitions; created and formatted during the XP installation. They are not dynamic partitions.

The Ubuntu paritions were created during installation, with the "Use entire drive" option.

---

### Post by mitscha on 2008-09-16
Hi Lano, did you find a solution to your prob?
I've got exactly the same setup as you, with existing Win-Vista & Ubuntu Hardy Heron installations on ordinary IDE-drives, working fine in a double-boot setup, on an ASROCK K7vt4 pro motherboard.
I have installed 2 Maxtor 500 gigs SATA-drives on the sole SATA-connector, and have set up the Raid-0 in the BIOS.
I want to be able to access data on the RAID from both WIN and Ubuntu, and have formatted the two disks with NTFS. Here is FDISK -L:
Disk /dev/sda: 250.0 Gb, 250059350016 byte
255 heads, 63 sectors/track, 30401 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02a26c98

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1   *           1       16216   130247832+   7  HPFS/NTFS
/dev/sda2           16216       30402   113948672    7  HPFS/NTFS

Disk /dev/sdb: 163.9 Gb, 163928604672 byte
255 heads, 63 sectors/track, 19929 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9db64a0f

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sdb1   *           1       19929   160079661   42  SFS

Disk /dev/hda: 163.9 Gb, 163928604672 byte
255 heads, 63 sectors/track, 19929 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29082908

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/hda1   *           2       19929   160071660    f  w95 udvidet (LBA)
/dev/hda5               2       19929   160071628+   7  HPFS/NTFS

Disk /dev/hdb: 250.0 Gb, 250059350016 byte
255 heads, 63 sectors/track, 30401 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/hdb1   *           1        3040    24418768+  83  Linux
/dev/hdb2            9588       30401   167188455    5  Udvidet
/dev/hdb3            3041        6079    24410767+  83  Linux
/dev/hdb4            6080        9587    28178010   83  Linux
/dev/hdb5            9588        9964     3028221   82  Linux swap / Solaris
/dev/hdb6            9965       30401   164160171   83  Linux

Partitionstabellens indgange er ikke i disk-rækkefølge

Disk /dev/sdc: 500.1 Gb, 500107862016 byte
255 heads, 63 sectors/track, 60801 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00026dca

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetekt

Disk /dev/sdd: 500.1 Gb, 500107862016 byte
255 heads, 63 sectors/track, 60801 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004215a

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetekt

Disk /dev/sde: 250.0 Gb, 250059350016 byte
255 heads, 63 sectors/track, 30401 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe7efe7e

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sde1   *           1       30401   244196001    6  FAT16

So, the disks set up in the RAID are the two 500 Gb-disks SDE & SDD..

mitscha@tower:~$ sudo dmraid -r
[sudo] password for mitscha: 
/dev/sdd: via, "via_ddjcgfebec", mirror, ok, 976773167 sectors, data@ 0
/dev/sdc: via, "via_ddeeiagiaj", mirror, ok, 976773167 sectors, data@ 0

Here you see the same doubling of the RAID, instead of just seeing one...
any solutions?
Greets Mitscha

---

### Post by Lano on 2008-09-22
Hey mate,
nah, I never ended up finding a solution.
Good luck to you though! If you do find one, come back and let me know!
Justin

---

