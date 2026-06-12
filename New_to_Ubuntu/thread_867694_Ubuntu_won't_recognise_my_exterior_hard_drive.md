---
title: "Ubuntu won't recognise my exterior hard drive"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Benbow on 2008-07-23
I have bought another hard drive to supplement my main drive in my computer. This exterior drive is in a case which connects to the pc via usb 2 and I have exchanged drives and get the same result - both drives have Ubuntu as their operating system. It will not allow me to mount the drives and gives me the message "Unable to mount location, no media in drive" - this I know is wrong because both drives run fine when in my pc.
Any ideas?

---

### Post by rockerphil on 2008-07-23
have you tried using a forced mount through the terminal? that may do the trick, and remember to have a mount point for the drive, say /home/<yourusername>/Media then figure out what the drive label is of course by running 

sudo fdisk -l (l is a lower case L)

then force mount the drive using the drive label (it would show up on my system as /dev/sdc) so for my system i'd use (not too sure on the force part just a good guess)

sudo mount /dev/sdc --force ~/Media

hope it helps

---

### Post by Benbow on 2008-07-23
Hi, Rockerphil, and thanks for the answer. Got the following result :


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x086c8431

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris
benbow@benbow-desktop:~$ 
benbow@benbow-desktop:~$ sudo mount /dev/sda5 --force ~/Media
mount: unrecognized option `--force'
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
For many more details, say  man 8 mount.

I have the identity of my hard drive partitions but after trying your sudo suggestion I couldn't understand the rest.

All I want is a simple command which will enable me to use a hard drive attached via a usb port. Until yesterday it was simply a case of attaching the drive and my pc instantly recognised it. For some strange reason, it won't do this any more.

---

### Post by sisco311 on 2008-07-23
sda5 is your swap partition.
according to fdisk the external hard disk is not recognised.
plug out and plug in the drive then post the output from:
```
dmesg | tail
```and
```
sudo lshw -C disk
```

---

### Post by rockerphil on 2008-07-23
yes, as stated you're trying to mount your Swap partition, which the system won't let you since it does the same basic job as the Windows paging file, eases the load on your system memory. and also as stated the output says your external isn't recognised by the system, since i'm seeing only one internal hard drive in your system the external SHOULD show up as /dev/sdb, so i'd follow the suggestions stated earlier

edit: you may also try booting with the external connected, i know it's worked for me with external storage media, bst of luck though

---

### Post by Benbow on 2008-07-23
Here are the results sisco. I can't see my exterior drive mentioned. Incidentally, I have changed back to the original configuration - my 500gb drive is now back in the pc and the 160gb is the exterior one.

benbow@benbow-desktop:~$ dmesg | tail
[   57.601202] Bluetooth: HCI socket layer initialized
[   57.689625] Bluetooth: L2CAP ver 2.9
[   57.689631] Bluetooth: L2CAP socket layer initialized
[   57.699180] Bluetooth: RFCOMM socket layer initialized
[   57.699198] Bluetooth: RFCOMM TTY layer initialized
[   57.699202] Bluetooth: RFCOMM ver 1.8
[   60.891395] NET: Registered protocol family 17
[   63.707225] NET: Registered protocol family 10
[   63.708120] lo: Disabled Privacy Extensions
[   74.000537] eth0: no IPv6 routers present
benbow@benbow-desktop:~$ sudo lshw -C disk
[sudo] password for benbow: 
  *-disk                  
       description: ATA Disk
       product: ST3500630A
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 5QG2P9FD
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0c8c0c8b
  *-cdrom:0
       description: DVD writer
       product: DVDRW SOHW-1213S
       vendor: LITE-ON
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TS09
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: DVD writer
       product: IDE1108
       vendor: DVDRW
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: B018
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: MP170Storage
       vendor: Canon
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       version: 0104
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk:0
       description: SCSI Disk
       product: Compact Flash
       vendor: eUSB
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sdc
       version: 5.06
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk:1
       description: SCSI Disk
       product: SmartMedia
       vendor: eUSB
       physical id: 0.0.1
       bus info: scsi@7:0.0.1
       logical name: /dev/sdd
       version: 5.06
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdd
benbow@benbow-desktop:~$

---

