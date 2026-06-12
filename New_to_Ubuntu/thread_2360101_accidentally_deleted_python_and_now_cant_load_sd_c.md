---
title: "accidentally deleted python and now cant load sd card"
date: 2017-05-01
forum: New to Ubuntu
---

### Post by micahpage on 2017-05-01
I accidentally deleted python2.x, then reinstalled python2.x, but i noticed afterwords that i can no longer can just insert my sd vard into my desktop and have it mount it

this is the error i get when i click on the drive to open
```
Error mounting /dev/sdb1 at /media/metulburr/200B-57C0: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/metulburr/200B-57C0"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'
```

fdisk
```
metulburr@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x9664c0d1


Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048 1924345855 1924343808 917.6G 83 Linux
/dev/sda2       1924347902 1953523711   29175810  13.9G  5 Extended
/dev/sda5       1924347904 1953523711   29175808  13.9G 82 Linux swap / Solaris








Disk /dev/sdf: 3.7 TiB, 4000752599040 bytes, 976746240 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xdb4bf07b


Device     Boot Start       End   Sectors  Size Id Type
/dev/sdf1         256 976746239 976745984  3.7T  7 HPFS/NTFS/exFAT




Disk /dev/sdb: 125 GiB, 134217728000 bytes, 262144000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7c1ea365


Device     Boot Start       End   Sectors  Size Id Type
/dev/sdb1  *     1448 262143999 262142552  125G  7 HPFS/NTFS/exFAT



```

---

### Post by cclothier on 2017-05-02
Sounds like maybe exfat drivers also got uninstalled?

To check run
```
dpkg -l | grep 'exfat'
```

If not installed run
```
sudo apt-get install exfat-fuse exfat-utils
```

---

### Post by micahpage on 2017-05-02
that fixed it. Thanks

---

