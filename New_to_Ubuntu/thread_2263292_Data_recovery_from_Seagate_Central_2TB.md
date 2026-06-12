---
title: "Data recovery from Seagate Central 2TB"
date: 2015-01-30
forum: New to Ubuntu
---

### Post by slick2 on 2015-01-30
Trying to recover data from Seagate Central 2TB.  I've followed a few threads from various forums.  
([http://myanwyn.blogspot.com/2014/08/how-to-recover-seagate-central-data.html](http://myanwyn.blogspot.com/2014/08/how-to-recover-seagate-central-data.html)) is the one that got me to this point.  Not sure what to do from here.  Please  advise.

Thanks in advance for any help
Slick

(Output Below)

$ sudo parted -l
Model: ATA WDC WD3200AAKS-7 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16           diag
 2      41.9MB  15.8GB  15.7GB  primary   ntfs
 3      15.8GB  280GB   264GB   primary   ntfs            boot
 4      280GB   320GB   40.1GB  extended
 5      280GB   318GB   38.3GB  logical   ext4
 6      318GB   320GB   1877MB  logical   linux-swap(v1)




Model: ST2000VM 003-1CT164 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name                Flags
 1      1049kB  22.0MB  21.0MB  ext2         Kernel_1            msftdata
 2      22.0MB  43.0MB  21.0MB  ext2         Kernel_2            msftdata
 3      43.0MB  1117MB  1074MB  ext4         Root_File_System_1  msftdata
 4      1117MB  2190MB  1074MB  ext4         Root_File_System_2  msftdata
 5      2190MB  3264MB  1074MB  ext4         Config              msftdata
 6      3264MB  4338MB  1074MB               Swap
 7      4338MB  5412MB  1074MB  ext4         Update              msftdata
 8      5412MB  2000GB  1995GB               Data                lvm






$ sudo lvs /dev/mapper/vg1-lv1
  LV   VG   Attr      LSize Pool Origin Data%  Move Log Copy%  Convert
  lv1  vg1  -wi------ 1.81t     




                                      
$ sudo mount -t ext4 -o ro /dev/mapper/vg1-lv1/mnt/seagate
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by Bucky Ball on 2015-01-30
Welcome. Testdisk and Photorec are commonly used. Here's some links. Hope they help:

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

Testdisk description:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Photorec description:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

If you boot to a Live session (from the installer disk/USB choose 'Try Ubuntu') can you see your disk and the data on it?

---

