---
title: "NTFS support Hardy"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by catroaring on 2008-04-26
I've got one external and one internal drive in NTFS format.  Any help on getting them mounted on Hardy, i've heard it's supported in Hardy.

---

### Post by tamoneya on 2008-04-26
NTFS has been supported for a while now. Should just be done with a simple mount command.```
sudo mkdir /windows
sudo mount /dev/sda2 /windows
```
This worked fine on my machine.

---

### Post by catroaring on 2008-04-26
this is what i get
human@athlon1800:~$ sudo mount /dev/sda2 /windows
mount: you must specify the filesystem type

---

### Post by tamoneya on 2008-04-26
well then just specify with the -t option:```
sudo mount -t ntfs /dev/sda2/windows
```

---

### Post by catroaring on 2008-04-26
i get this

human@athlon1800:~$ sudo mount -t ntfs /dev/sda2/windows
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

### Post by tamoneya on 2008-04-26
sorry that was my fault i missed a space between the device and the directory
```
sudo mount -t ntfs /dev/sda2 /windows
```

---

### Post by catroaring on 2008-04-26
For many more details, say  man 8 mount .
human@athlon1800:~$ sudo mount -t ntfs /dev/sda2 /windows
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by tamoneya on 2008-04-26
/dev/sda2 is my ntfs partition it may be different on your computer.  are you certain that yours is /dev/sda2.  post the output of ```
sudo fdisk -l
```

---

### Post by catroaring on 2008-04-26
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x220a5000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      208813+  83  Linux
/dev/sda2           18988       19457     3775275    5  Extended
/dev/sda3   *        9950       18987    72597735   83  Linux
/dev/sda4              27        9949    79706497+  8e  Linux LVM
/dev/sda5           19223       19457     1887606   82  Linux swap / Solaris
/dev/sda6           18988       19222     1887574+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2cb3844

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14945   120045681    7  HPFS/NTFS

---

### Post by ad_267 on 2008-04-26
Your ntfs partition is /dev/sdb1, so you want to use:
```
sudo mount -t ntfs /dev/sdb1 /windows
```

When someone gives you commands to enter it's best to enter "man command_name" to see what the command does and understand what you are actually doing. For example to see what man does you would enter "man man"

---

### Post by catroaring on 2008-04-26
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by ad_267 on 2008-04-26
Ok can you try then:
```
sudo mount /dev/sdb1 /windows
```

I've just removed the "-t ntfs" part. The partition is probably recognised as hpfs or something else, however you shouldn't need to specify the file system. You probably got this error (mount: you must specify the filesystem type) because you were trying to mount an extended partition before, not the ntfs partition.

From man mount: 
> -t vfstype
The  argument following the -t is used to indicate the file sys&#8208;
tem type.  The file system types which are  currently  supported
include:  adfs,  affs,  autofs,  cifs,  coda,  coherent, cramfs,
debugfs, devpts, efs,  ext,  ext2,  ext3,  hfs,  hfsplus,  hpfs,
iso9660,  jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc, qnx4,
ramfs, reiserfs, romfs, smbfs, sysv, tmpfs,  udf,  ufs,  umsdos,
usbfs,  vfat,  xenix,  xfs, xiafs.  Note that coherent, sysv and
xenix are equivalent and that xenix and coherent will be removed
at  some  point  in  the future &#8212; use sysv instead. Since kernel
version 2.1.21 the types ext and xiafs  do  not  exist  anymore.
Earlier,  usbfs  was  known as usbdevfs.  Note, the real list of
all supported filesystems depends on your kernel.

For most types all the mount program has to do is issue a simple
mount(2)  system call, and no detailed knowledge of the filesys&#8208;
tem type is required.  For a few types however (like nfs,  nfs4,
cifs,  smbfs,  ncpfs)  ad  hoc code is necessary. The nfs, nfs4,
cifs, smbfs, and ncpfs have a separate mount program.  In  order
to  make  it possible to treat all types in a uniform way, mount
will execute the program /sbin/mount.TYPE (if that exists)  when
called  with  type TYPE.  Since various versions of the smbmount
program have different  calling  conventions,  /sbin/mount.smbfs
may have to be a shell script that sets up the desired call.

If  no  -t  option  is  given, or if the auto type is specified,
mount will try to guess the desired type.  Mount uses the  blkid
or  volume_id  library for guessing the filesystem type; if that
does not turn up anything that looks familiar, mount will try to
read  the  file  /etc/filesystems,  or,  if that does not exist,
/proc/filesystems.  All of the  filesystem  types  listed  there
will  be tried, except for those that are labeled "nodev" (e.g.,
devpts, proc and nfs).  If /etc/filesystems ends in a line  with
a single * only, mount will read /proc/filesystems afterwards.

---

### Post by ad_267 on 2008-04-26
Also, hard drives should be recognised and mounted by default in the /media directory. Is your ntfs partition not already mounted there? It would be at /media/sdb1

---

### Post by gn2 on 2008-04-26
Open Add/Remove, search for and install Storage Device Manager.

It's listed as pysdm in Synaptic.

---

