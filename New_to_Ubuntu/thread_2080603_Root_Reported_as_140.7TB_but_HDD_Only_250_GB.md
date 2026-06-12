---
title: "Root Reported as 140.7TB but HDD Only 250 GB"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by mapes12 on 2012-11-04
Can't get Remastersys to complete as the file is too big. / is reported as 140.7TB but HDD is only 250GB? Nothing in /.local/share/Trash that I can find causing a problem. I've attached a screen shot.

And this is the disk section of lshw output:-

> *-disk
                description: ATA Disk
                product: TOSHIBA MK2555GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: FG00
                serial: Z8EJF0FAS
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000c2e85
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 9defaf73-bf2c-45c7-85d4-fdb4302e1b5d
                   size: 82GiB
                   capacity: 82GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-06-12 19:21:04 filesystem=ext4 lastmountpoint=/ modified=2012-06-12 19:36:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-11-04 08:22:00 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 150GiB
                   capacity: 150GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3814MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 146GiB
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L633A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: TM00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc

---

