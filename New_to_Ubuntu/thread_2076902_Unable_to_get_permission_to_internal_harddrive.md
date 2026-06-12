---
title: "Unable to get permission to internal harddrive"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by snoylr on 2012-10-27
When I try to access a second hard drive installed on Ubuntu 12.10 I am denied permission to access the drive.  How do I change ownership of the second drive?

---

### Post by newb85 on 2012-10-27
Welcome to the forums!

More details are needed.  Are you trying to access files on the second drive using Nautilus (the file browser)?  Are you unable to access it at all, or are you only being denied write permissions?

Please give the output of
```
sudo lshw -C disk
sudo lshw -C volume
```

---

### Post by snoylr on 2012-10-27
This is response to sudo lshw -C disk
```

 *-disk                  
       description: ATA Disk
       product: ST3500410AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: CC34
       serial: 5VM0N3PV
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=3e2f3e2f
  *-disk
       description: ATA Disk
       product: ST3500418AS



 *-disk                  
       description: ATA Disk
       product: ST3500410AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: CC34
       serial: 5VM0N3PV
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=3e2f3e2f
  *-disk
       description: ATA Disk
       product: ST3500418AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: CC46
       serial: 6VM67JEJ
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=000cb637
  *-disk
       description: ATA Disk
       product: ST3200827AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdc
       version: 3.AH
       serial: 9ND0A00R
       size: 186GiB (200GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=0006a3c1
  *-cdrom
       description: DVD-RAM writer
       product: iHAS124   A
       vendor: ATAPI
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: BL03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdd
       configuration: sectorsize=512
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@6:0.0.1
       logical name: /dev/sde
       configuration: sectorsize=512
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@6:0.0.2
       logical name: /dev/sdf
       configuration: sectorsize=512
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@6:0.0.3
       logical name: /dev/sdg
       configuration: sectorsize=512

```



This is response to sudo lshw -C volume
  ```

*-volume                
       description: EXT3 volume
       vendor: Linux
       physical id: 1
       bus info: scsi@0:0.0.0,1
       logical name: /dev/sda1
       version: 1.0
       serial: afd6235e-620f-1991-d5d4-30c09b313dc8
       size: 465GiB
       capacity: 465GiB
       capabilities: primary journaled large_files recover ext3 ext2 initialized
       configuration: created=2012-10-26 16:18:24 filesystem=ext3 label=NEW VOLUME1 modified=2012-10-26 23:31:53 mounted=2012-10-26 23:31:53 state=clean
  *-volume:0
       description: EXT4 volume
       vendor: Linux
       physical id: 1
       bus info: scsi@1:0.0.0,1
       logical name: /dev/sdb1
       logical name: /
       version: 1.0
       serial: bb00112f-59dc-4b6d-ac18-0c1da73ec53e
       size: 458GiB
       capacity: 458GiB
       capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
       configuration: created=2012-10-25 16:24:03 filesystem=ext4 lastmountpoint=/ modified=2012-10-27 06:42:37 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2012-10-27 06:42:37 state=mounted
  *-volume:1
       description: Extended partition
       physical id: 2
       bus info: scsi@1:0.0.0,2
       logical name: /dev/sdb2
       size: 7166MiB
       capacity: 7166MiB
       capabilities: primary extended partitioned partitioned:extended
     *-logicalvolume
          description: Linux swap / Solaris partition
          physical id: 5
          logical name: /dev/sdb5
          capacity: 7166MiB
          capabilities: nofs
  *-volume:0
       description: EXT3 volume
       vendor: Linux
       physical id: 1
       bus info: scsi@3:0.0.0,1
       logical name: /dev/sdc1
       version: 1.0
       serial: 99e669ff-a19e-e396-c7c6-41484bcf4271
       size: 185GiB
       capacity: 185GiB
       capabilities: primary bootable journaled large_files recover ext3 ext2 initialized
       configuration: created=2012-10-26 16:43:20 filesystem=ext3 label=NEW VOLUME2 modified=2012-10-26 23:32:16 mounted=2012-10-26 23:32:16 state=clean
  *-volume:1
       description: Extended partition
       physical id: 2
       bus info: scsi@3:0.0.0,2
       logical name: /dev/sdc2
       size: 958MiB
       capacity: 958MiB
       capabilities: primary extended partitioned partitioned:extended
     *-logicalvolume
          description: Extended partition
          physical id: 5
          size: 958MiB
          capacity: 958MiB
          capabilities: extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sdc5
             capacity: 958MiB
             capabilities: nofs

       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: CC46
       serial: 6VM67JEJ
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=000cb637
  *-disk
       description: ATA Disk
       product: ST3200827AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdc
       version: 3.AH
       serial: 9ND0A00R
       size: 186GiB (200GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=0006a3c1
  *-cdrom
       description: DVD-RAM writer
       product: iHAS124   A
       vendor: ATAPI
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: BL03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdd
       configuration: sectorsize=512
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@6:0.0.1
       logical name: /dev/sde
       configuration: sectorsize=512
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@6:0.0.2
       logical name: /dev/sdf
       configuration: sectorsize=512
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@6:0.0.3
       logical name: /dev/sdg
       configuration: sectorsize=512

```

I am denied permission to access  /dev/sdb and /dev/sdc

---

### Post by newb85 on 2012-10-27
Please post terminal outputs inside code tags, like this:
[noparse]```
Output
Lines
Here
```[/noparse]
It makes posts much easier to read.  Please edit your last post and fix this.

I still don't understand what you're trying to do.

---

### Post by snoylr on 2012-10-27
I have revised my last reply to make the code sections more readable.

Three hard drives are installed on my ubuntu 12.10 computer.  One hard drive is called new volume1.  Another is called new volume2.

Both volumes are owned by "root"

I have not been able to find a way to add files to either of the "new volume" drives.  

When I try to give folder access to the drive to myself I get the message, "You are not the owner, so you cannot change these permissions."

In other words I have no way to place or access any data on either of those two drives.  According to the command print-outs you asked me to run it appears that these two drives are recorded in the system as  /dev/sdb and /dev/sdc

---

### Post by VCoolio on 2012-10-27
You need to own the mount point, or at least have rw permissions. So if you mount the drives to, for example, /media/drive1 and /media/drive2, make sure you have permissions to those folders before you mount the drives.

So unmount the drives. Then:
sudo chown snoylr:users /media/drive1

replace snoylr with your username and replace drive1 with the correct folder. The same for the 2nd drive.

Then in /etc/fstab, specify how to mount the drives. Add lines like this:

/dev/sdb /media/drive1 ext4 noauto,users,rw 0 0
/dev/sdc /media/drive2 ext4 noauto,users,rw 0 0

Again, replace drive{1,2} with the correct folders, also change ext4 to the correct filesystem. Remove "noauto" if you need to have them automatically mounted. 

Then try again.

---

### Post by snoylr on 2012-10-27
Thanks for your assistance.  I am very new to Ubuntu.  What do you mean by "correct folder" in the following line:

replace snoylr with your username and replace drive1 with *the correct folder*. The same for the 2nd drive.

---

### Post by VCoolio on 2012-10-27
That's the folder where you mount the drive to. /dev/sdb and /dev/sdc is the hardware. Now you need to mount them to a folder where you can browse them and use them to copy files to. Those mount points usually are in /media. You can create folders there (sudo mkdir /media/foldername) and then use those folders in fstab so you have the drives always mounted to those folders.

Enter "mount"  in the terminal. You'll see that you have your main disk mounted to several folders. /dev/sda1 to / maybe and /dev/sda2 to /home, if you have the drive partitioned.

---

### Post by newb85 on 2012-10-27
Shouldn't the OP be mounting volumes on the drives, rather than the drives themselves?

E.g.,
/dev/sdb1
/dev/sdc1
etc...

---

### Post by NetoriusNick on 2012-12-11
Hi please bare with me I am still a noob (for a lack of better words) at linux.
I think that I am having the same problem but I am trying to use the additional drive to run a virtualbox machine from. (pic shows reply from the vm virtualbox command to create a file that points to the hard drive, see page 151 in the vm virtualbox manual)

The logical drive name for the target drive is /dev/sda.

Sudo lshw -c disk
```

 *-disk                  
       description: ATA Disk
       product: WDC WD3200AAKS-7
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WMAV2DE62482
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=90000000
  *-disk
       description: ATA Disk
       product: WDC WD1600AAJS-7
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WCAT23361268
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=00022422
  *-cdrom
       description: DVD-RAM writer
       product: DVD+-RW TS-H653H
       vendor: TSSTcorp
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: D400
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       product: GoFlex Desk
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 0D19
       serial: NA0LR0DY
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=b8c9fb73
  *-disk
       description: SCSI Disk
       product: GoFlex Desk
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdd
       version: 0D19
       serial: NA0LR0A9
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=1a1df41a
  *-disk:0
       description: SCSI Disk
       product: mSD SDDR-189
       vendor: SanDisk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sde
       version: 1804
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sde
  *-disk:1
       description: SCSI Disk
       product: SD  SDDR-189
       vendor: SanDisk
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdf
       version: 1804
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdf
  *-disk:2
       description: SCSI Disk
       product: MSxDSDDR-189
       vendor: SanDisk
       physical id: 0.0.2
       bus info: scsi@4:0.0.2
       logical name: /dev/sdg
       version: 1804
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdg
  *-disk:3
       description: SCSI Disk
       product: CF  SDDR-189
       vendor: SanDisk
       physical id: 0.0.3
       bus info: scsi@4:0.0.3
       logical name: /dev/sdh
       version: 1804
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdh
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdi
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: sectorsize=512 signature=e8900690

```sudo lshw -c volume
```

  *-volume:0              
       description: Windows FAT volume
       vendor: MSWIN4.1
       physical id: 1
       bus info: scsi@0:0.0.0,1
       logical name: /dev/sda1
       version: FAT16
       serial: 07da-0b0d
       size: 62MiB
       capacity: 62MiB
       capabilities: primary fat initialized
       configuration: FATs=2 filesystem=fat
  *-volume:1
       description: Windows NTFS volume
       physical id: 2
       bus info: scsi@0:0.0.0,2
       logical name: /dev/sda2
       version: 3.1
       serial: 4cf1-36d0
       size: 9986MiB
       capacity: 10018MiB
       capabilities: primary bootable ntfs initialized
       configuration: clustersize=4096 created=2010-11-13 15:53:39 filesystem=ntfs label=RECOVERY state=clean
  *-volume:2
       description: Windows NTFS volume
       physical id: 3
       bus info: scsi@0:0.0.0,3
       logical name: /dev/sda3
       logical name: /media/nick/OS
       version: 3.1
       serial: 984460b8-99be-d347-a92a-7f8aebb45494
       size: 288GiB
       capacity: 288GiB
       capabilities: primary ntfs initialized
       configuration: clustersize=4096 created=2010-11-13 15:53:43 filesystem=ntfs label=OS modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
  *-volume:0
       description: Linux filesystem partition
       vendor: Linux
       physical id: 1
       bus info: scsi@1:0.0.0,1
       logical name: /dev/sdb1
       logical name: /boot
       version: 1.0
       serial: 18ce208d-f217-48fc-b75c-85677f06ac33
       size: 243MiB
       capacity: 243MiB
       capabilities: primary bootable ext2 initialized
       configuration: filesystem=ext2 modified=2012-12-11 16:34:18 mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
  *-volume:1
       description: Extended partition
       physical id: 2
       bus info: scsi@1:0.0.0,2
       logical name: /dev/sdb2
       size: 148GiB
       capacity: 148GiB
       capabilities: primary extended partitioned partitioned:extended
     *-logicalvolume
          description: Linux LVM Physical Volume partition
          physical id: 5
          logical name: /dev/sdb5
          serial: 5Ws5uK-KVIw-aQHu-4OIz-LEm9-V1ff-Yj8fcx
          size: 148GiB
          capacity: 148GiB
          capabilities: multi lvm2
  *-volume
       description: Extended partition
       physical id: 1
       bus info: scsi@2:0.0.0,1
       logical name: /dev/sdc1
       size: 1863GiB
       capacity: 1863GiB
       capabilities: primary extended partitioned partitioned:extended
     *-logicalvolume
          description: HPFS/NTFS partition
          physical id: 5
          logical name: /dev/sdc5
          logical name: /media/nick/Flex2
          capacity: 1863GiB
          configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
  *-volume
       description: Windows NTFS volume
       physical id: 1
       bus info: scsi@3:0.0.0,1
       logical name: /dev/sdd1
       logical name: /media/nick/FreeAgent GoFlex Drive
       version: 3.1
       serial: 1e744625-1c50-2646-8151-c2a9f2994314
       size: 1863GiB
       capacity: 1863GiB
       capabilities: primary ntfs initialized
       configuration: clustersize=4096 created=2011-10-14 10:15:04 filesystem=ntfs label=FreeAgent GoFlex Drive mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
  *-volume:0
       description: Windows NTFS volume
       physical id: 1
       bus info: scsi@5:0.0.0,1
       logical name: /dev/sdi1
       logical name: /media/nick/HP Old
       version: 3.1
       serial: 0ac4863b-ad64-5b45-b31c-85c6a7bca91b
       size: 38GiB
       capacity: 38GiB
       capabilities: primary ntfs initialized
       configuration: clustersize=4096 created=2012-01-31 00:20:30 filesystem=ntfs label=HP Old mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
  *-volume:1
       description: Windows NTFS volume
       physical id: 2
       bus info: scsi@5:0.0.0,2
       logical name: /dev/sdi2
       logical name: /media/nick/XP Master
       version: 3.1
       serial: 90b79390-04a9-fb4f-b7d5-edf806ea47aa
       size: 2990MiB
       capacity: 2996MiB
       capabilities: primary ntfs initialized
       configuration: clustersize=4096 created=2012-01-31 00:20:30 filesystem=ntfs label=XP Master mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
  *-volume:2
       description: Extended partition
       physical id: 3
       bus info: scsi@5:0.0.0,3
       logical name: /dev/sdi3
       size: 890GiB
       capacity: 890GiB
       capabilities: primary extended partitioned partitioned:extended
     *-logicalvolume:0
          description: Linux filesystem partition
          physical id: 5
          logical name: /dev/sdi5
          capacity: 886GiB
     *-logicalvolume:1
          description: Linux swap / Solaris partition
          physical id: 6
          logical name: /dev/sdi6
          capacity: 4093MiB
          capabilities: nofs

```

---

