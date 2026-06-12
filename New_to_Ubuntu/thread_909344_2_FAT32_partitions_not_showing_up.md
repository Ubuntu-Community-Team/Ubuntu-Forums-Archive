---
title: "2 FAT32 partitions not showing up"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by velociraptor101 on 2008-09-03
I'm dual booting xp-ubuntu and that went very well, but now I'm trying to get my data drive with 2 120 gig partitions to show up in ubuntu. 

I have no "  ** gb media" icon showing up on my desktop and this is what i got from fdisk, how do i get it to mount?

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc5eac5ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3123    25085466    7  HPFS/NTFS
/dev/sda2            3124        4500    11060752+   5  Extended
/dev/sda5            3124        4436    10546641   83  Linux
/dev/sda6            4437        4500      514048+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92403db4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15300   122897218+   c  W95 FAT32 (LBA)
/dev/sdb2           15301       30515   122214487+   f  W95 Ext'd (LBA)
/dev/sdb5           15301       30515   122214456    b  W95 FAT32

---

### Post by Too Late on 2008-09-03
Probably they're already mounted. Type "mount" (or "cat /etc/mtab") to see if they are somewhere there. Also, see the /etc/fstab file.

---

### Post by TJCIB on 2008-09-03
if you want it to mount automatically at boot, you  need to edit /etc/fstab
That is pretty well documents.

if you want to mount it manually use 

```
sudo mount /dev/sda# /media/*directoryYouWant*
```

Where is # is the number of the partition you want to mount.  You can mount it anywhere, but generally I use /media/something

I hope that helps.

---

### Post by velociraptor101 on 2008-09-03
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/asdf/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=asdf)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

thats what mount spit out

---

### Post by velociraptor101 on 2008-09-03
tried mounting to a folder... no go

asdf@asdf-desktop:~$ sudo mount /dev/sdb1 /home/asdf/media3 fat32
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

### Post by velociraptor101 on 2008-09-03
GNU nano 2.0.7                             File: /etc/fstab                                                                

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8360e7d1-f902-4c51-82c7-a60f993917a6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=4ba59c1f-9b28-4bf2-9149-da8a9e348c8b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


not there

---

### Post by Too Late on 2008-09-03
> **velociraptor101 said:**
> tried mounting to a folder... no go

asdf@asdf-desktop:~$ sudo mount /dev/sdb1 /home/asdf/media3 fat32
You have wrong syntax. The correct is (see "man mount" for more):
```
sudo mount -t vfat /dev/sdb1 /home/asdf/media3
```
Note that the destination directory (media3) must be created before the mounting. Specifying the filesystem type ("-t vfat" section) is not mandatory.

> **velociraptor101 said:**
> GNU nano 2.0.7                             File: /etc/fstab                                                                

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8360e7d1-f902-4c51-82c7-a60f993917a6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=4ba59c1f-9b28-4bf2-9149-da8a9e348c8b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

[color=red]/dev/sdb1       /home/asdf/media3   vfat   defaults     0   0[/color]


```
not there
Now it is.

If you want to replace the device name with UUID, run "sudo blkid" command and find out the right one. Use sda5 and sda6 partitions as a reference.

If you want to have an ownership/write permissons to a fat32 partition, replace the word "defaults" with this:```
uid=1000,gid=1000
```
(Assuming that your UID and GID is 1000. If you're not sure, run the "id" command.)

---

