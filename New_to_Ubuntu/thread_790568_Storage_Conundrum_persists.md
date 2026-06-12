---
title: "Storage Conundrum persists"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by nnjond on 2008-05-11
Hi, can you please help me? 

I have re-installed my dual boot Win 2000+ Hardy on one physical drive with all my data on a second, ancillary  HD which I can access from either O.S. However the files I have saved in Win 2000 since  re-instal don't show up in Hardy? - Just the empty 'folders' or gobbledygook? Also; I would like to be rid of the padlocks that mysteriously come and go on my ancillary drive.

Here is some info that might be revealing:

nnjond@nnjond-desktop:~$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda3 14G 3.3G 9.4G 26% /
varrun 744M 108K 744M 1% /var/run
varlock 744M 0 744M 0% /var/lock
udev 744M 76K 744M 1% /dev
devshm 744M 12K 744M 1% /dev/shm
lrm 744M 38M 706M 6% /lib/modules/2.6.24-16-generic/volatile
/dev/sdb5 150G 131G 19G 88% /media/disk
nnjond@nnjond-desktop:~$

nnjond@nnjond-desktop:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa459283

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3666 29439112 7 HPFS/NTFS
/dev/sda2 3666 8246 36796851+ f W95 Ext'd (LBA)
/dev/sda3 8247 10011 14177362+ 83 Linux
/dev/sda5 3666 3927 2104483+ 82 Linux swap / Solaris
/dev/sda6 3928 4189 2104483+ 82 Linux swap / Solaris
/dev/sda7 4190 6536 18852246 83 Linux
/dev/sda8 6537 8162 13060813+ 83 Linux
/dev/sda9 8163 8246 674698+ 82 Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31ac70c9

Device Boot Start End Blocks Id System
/dev/sdb1 2 19457 156280320 f W95 Ext'd (LBA)
/dev/sdb5 2 19457 156280288+ b W95 FAT32
nnjond@nnjond-desktop:~$

---

