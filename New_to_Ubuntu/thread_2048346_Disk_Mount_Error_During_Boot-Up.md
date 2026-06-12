---
title: "Disk Mount Error During Boot-Up"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by Tosho on 2012-08-26
bump
I've got the same problem. While I'm trying to install Xubuntu 12.04 from USB Flash Stick I met few problems with Gparted when I tried to format and resize my partitions.
fdisk -l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b7be8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   103407615    51702784    7  HPFS/NTFS/exFAT
/dev/sda2       103410466   976771071   436680303    5  Extended
/dev/sda5       103410468   794218495   345404014    7  HPFS/NTFS/exFAT
/dev/sda6       859586560   976771071    58592256   83  Linux
/dev/sda7       795271168   803463167     4096000   82  Linux swap / Solaris
/dev/sda8       803465216   859584511    28059648   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 8016 MB, 8016363520 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15656960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0170b60c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15656959     7828448+   b  W95 FAT32

```

fstab
```
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0

```
I tried to edit /etc/fstab but I can't - > "Can't open file to write"

this is when I try to open a partition from Thunar
> Failed to mount "Storage".
Daemon is inhibited.

or > 
Failed to mount "Storage".
Error mounting: mount exited with exit code 21: mount: according to mtab, /dev/sda5 is already mounted on /media/Storage

.
and this is my gparted.error.log when I try to format a partition to ext4
```
GParted 0.11.0 --enable-libparted-dmraid

Libparted 2.3
Create Logical Partition #1 (ext4, 26.76 GiB) on /dev/sda  00:00:02    ( ERROR )
     	
create empty partition  00:00:01    ( SUCCESS )
     	
path: /dev/sda8
start: 803,465,216
end: 859,584,511
size: 56,119,296 (26.76 GiB)
set partition type on /dev/sda8  00:00:01    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:00    ( ERROR )
     	
mkfs.ext4 -j -O extent -L "ubuntu" /dev/sda8
     	
Filesystem label=ubuntu
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
1754400 inodes, 7014912 blocks
350745 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
215 block groups
32768 blocks per group, 32768 fragments per group
8160 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks):
mke2fs 1.42 (29-Nov-2011)
ext2fs_check_if_mount: Input/output error while determining whether /dev/sda8 is mounted.
mkfs.ext4: Input/output error
while trying to create journal
```

xubuntu@xubuntu:~/Desktop$ sudo umount -a /dev/sda8
```
umount: /run/shm: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /tmp: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /cdrom: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /run: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

xubuntu@xubuntu:~/Desktop$ sudo umount /dev/sda8
```
umount: /dev/sda8: not mounted
```

xubuntu@xubuntu:/etc$ df -h
```
df: cannot read table of mounted file systems: Input/output error
```

Choosing Install Xubuntu from the boot gives me this when I try to formata partition:
> The ext4(3) file system creatin in partition #7 of SCSI1 (0,0,0)(sda) failed.

Open  Home folder gives me this:
> Failed to open directory "xubuntu".
Error when getting information for file '/home/xubuntu/.gvfs': Transport endpoint is not connected.


Any help on that, please?

---

### Post by oldos2er on 2012-08-26
Post moved to its own thread.

---

