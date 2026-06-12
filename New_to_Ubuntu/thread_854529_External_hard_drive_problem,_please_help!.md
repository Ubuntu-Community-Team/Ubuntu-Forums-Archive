---
title: "External hard drive problem, please help!"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by justinram22 on 2008-07-09
ok, i have this external hard drive that i bought awhile ago, i have never been able to mount it in ubuntu, but i have in windows.. i JUST (like 5 min ago) formatted it into a NTFS format and downloaded NTFS ex3 and still cant install. the error message i get when trying to mount it is "CANNOT MOUNT VOLUME (next part underneath) Invalid mount option when attempting to mount the volume 'SignatureMini'." when i right click on properties all is "unknown" except location which is "computer:\\\" and MIME type which is "application/octet-stream", when i type "sudo fdisk-l" i get the following

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2610639

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18796   150978838+  83  Linux
/dev/sda2           18797       19457     5309482+   5  Extended
/dev/sda5           18797       19457     5309451   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x389fd11d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS


any help would be greatly apperciated

---

### Post by logos34 on 2008-07-09
try 

sudo mkdir /media/sdb1

sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

---

