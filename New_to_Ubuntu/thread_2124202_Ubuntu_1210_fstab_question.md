---
title: "Ubuntu 12:10 fstab question"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by stuart264 on 2013-03-10
My knowledge of Ubuntu is improving but I am really stuck on one thing, when I originally built this box to run Ubuntu I set it up with 2 x 500gb drives mapped as a Raid1 array with no problems. Since then I struck lucky and got a decent deal on 2 x 1TB drives that I have installed and set up as a separate Raid1 array that I want to share to the network as Network Storage called "Multimedia". NB Both Arrays are "fake raid" run by the motherboard and not the fake software raid in bunting.

I have used the disks/drive program in 12:10 and I have no problems mounting the array if I leave it on automount, the problems start when I am changing the mount point in /etc/fstab I get the following error on boot:-

Error mounting system-managed device /dev/dm-0: Command-line `mount "/media/Multimedia"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/mapper/pdc_egfdbddc, missing codepage or helper program, or other error

Right now my /etc/fstab reads:-

/dev/disk/by-uuid/1629277d-31a9-4537-8615-c32d99172c0a /media/Multimedia ext4 nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Multimedia 0 0

and the output of sudo fdisk -l is 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a8104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   960851967   480424960   83  Linux
/dev/sda2       960854014   976562175     7854081    5  Extended
/dev/sda5       960854016   976562175     7854080   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a8104

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   960851967   480424960   83  Linux
/dev/sdb2       960854014   976562175     7854081    5  Extended
/dev/sdb5       960854016   976562175     7854080   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/mapper/pdc_egfdbddc: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_egfdbddc doesn't contain a valid partition table

Disk /dev/mapper/pdc_babhbfjjd: 500.0 GB, 499999965184 bytes
255 heads, 63 sectors/track, 60788 cylinders, total 976562432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a8104

                    Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_babhbfjjd1   *        2048   960851967   480424960   83  Linux
/dev/mapper/pdc_babhbfjjd2       960854014   976562175     7854081    5  Extended
/dev/mapper/pdc_babhbfjjd5       960854016   976562175     7854080   82  Linux swap / Solaris

Disk /dev/mapper/pdc_babhbfjjd1: 492.0 GB, 491955159040 bytes
255 heads, 63 sectors/track, 59810 cylinders, total 960849920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_babhbfjjd1 doesn't contain a valid partition table

Disk /dev/mapper/pdc_babhbfjjd2: 8042 MB, 8042578944 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15708162 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41413535

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_babhbfjjd2p1               2    15708161     7854080   82  Linux swap / Solaris

Disk /dev/mapper/pdc_babhbfjjd5: 8042 MB, 8042577920 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15708160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

I know I have made a mistake somewhere in the fstab line but for the life of me I cant spot the error, so could any kind person please advise what the correct fstab line should be before my blood pressure goes any higher.

Stuart.

---

### Post by ronparent on 2013-03-10
> Error mounting system-managed device /dev/dm-0: Command-line `mount "/media/Multimedia"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/mapper/pdc_egfdbddc, missing codepage or helper program, or other error
the /dev/dm-0 is generally your first raid array - it wouldn't have a file structure - so the statement is correct. But why is the system trying to mount it?

What is the output of 'sudo blkid'. That would show all  the block devices and their uuid's. That should allow you to id the partition you are trying to auto-mount.

---

### Post by stuart264 on 2013-03-11
sudo blkid gives the following output

> /dev/sda: TYPE="promise_fasttrack_raid_member" 
/dev/sdc: TYPE="promise_fasttrack_raid_member" 
/dev/mapper/pdc_egfdbddc: LABEL="Multimedia" UUID="1629277d-31a9-4537-8615-c32d99172c0a" TYPE="ext4" 
/dev/sdd: LABEL="Multimedia" UUID="1629277d-31a9-4537-8615-c32d99172c0a" TYPE="ext4" 
/dev/mapper/pdc_babhbfjjd1: UUID="7746c7bc-4566-4143-91d0-9ccdda2a0e0f" TYPE="ext4" 
/dev/mapper/pdc_babhbfjjd5: UUID="720aa74c-403f-41b3-b271-24af50439d32" TYPE="swap"

as for the /dev/dm-0 being the first array, your right it, but for some reason the system has allocated the first raid array I put in as dm-1 and the subsequently installed array as dm-0, which I suspect is down to the chipset in the motherboard but its not broken so why fix it?

I did some testing yesterday with various settings and I finally managed to get the drive to mount with the /etc/fstab entry of 

> /dev/disk/by-id/dm-uuid-DMRAID-pdc_egfdbddc /media/Multimedia auto defaults 0 0

---

