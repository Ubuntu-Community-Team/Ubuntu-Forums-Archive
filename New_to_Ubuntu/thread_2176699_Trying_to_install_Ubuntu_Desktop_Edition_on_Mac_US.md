---
title: "Trying to install Ubuntu Desktop Edition on Mac USB drive"
date: 2013-09-25
forum: New to Ubuntu
---

### Post by Paul_Denlinger on 2013-09-25
Brand new Ubuntu user trying to create a Mac USB drive for Ubuntu Desktop (64-bit) edition.

Have been following the instructions on [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

Keep on getting a "file not found error". 

Here is what I have been getting in Terminal: 

```
Pauls-MacBook-Air:Desktop pdenlinger$ hdiutil convert -format UDRW -o ~/Desktop/ubuntu-12.04.3-desktop-amd64.img /Users/pdenlinger/Desktop/ubuntu-12.04.3-desktop-amd64.iso 
Reading Driver Descriptor Map (DDM : 0)…
Reading Ubuntu 12.04.3 LTS amd64         (Apple_ISO : 1)…
Reading Apple (Apple_partition_map : 2)…
Reading Ubuntu 12.04.3 LTS amd64         (Apple_ISO : 3)…
..............................................................................
Reading EFI (Apple_HFS : 4)…
..............................................................................
Reading Ubuntu 12.04.3 LTS amd64         (Apple_ISO : 5)…
..............................................................................
Elapsed Time:  8.662s
Speed: 81.7Mbytes/sec
Savings: 0.0%
created: /Users/pdenlinger/Desktop/ubuntu-12.04.3-desktop-amd64.img.dmg
Pauls-MacBook-Air:Desktop pdenlinger$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *121.3 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            120.5 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *32.1 GB    disk1
   1:             Windows_FAT_32 SONY_32G_SD             32.1 GB    disk1s1
Pauls-MacBook-Air:Desktop pdenlinger$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *121.3 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            120.5 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *32.1 GB    disk1
   1:             Windows_FAT_32 SONY_32G_SD             32.1 GB    disk1s1
/dev/disk2
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *16.0 GB    disk2
   1:                 DOS_FAT_32 UNTITLED                16.0 GB    disk2s1
Pauls-MacBook-Air:Desktop pdenlinger$ diskutil unmountDisk /dev/disk2
Unmount of all volumes on disk2 was successful
Pauls-MacBook-Air:Desktop pdenlinger$ sudo dd if=/Users/pdenlinger/Desktop/ubuntu-12.04.3-desktop-amd64.img of=dev/disk2 bs=1m
Password:
dd: dev/disk2: No such file or directory
Pauls-MacBook-Air:Desktop pdenlinger$ sudo dd if=/Users/pdenlinger/Desktop/ubuntu-12.04.3-desktop-amd64.img of=dev/rdisk2 bs=1m
dd: dev/rdisk2: No such file or directory
Pauls-MacBook-Air:Desktop pdenlinger$ sudo dd if=/Users/pdenlinger/Desktop/ubuntu-12.04.3-desktop-amd64.img of=dev/disk2 bs=1M
dd: bs: illegal numeric value
Pauls-MacBook-Air:Desktop pdenlinger$ sudo dd if=/Users/pdenlinger/Desktop/ubuntu-12.04.3-desktop-amd64.img of=dev/disk2 bs=1m
dd: dev/disk2: No such file or directory
Pauls-MacBook-Air:Desktop pdenlinger$ 

```

---

