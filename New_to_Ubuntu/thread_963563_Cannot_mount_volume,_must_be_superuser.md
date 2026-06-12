---
title: "Cannot mount volume, must be superuser"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by ewingmaestro on 2008-10-30
I have recently installed ubuntu eee on my eee pc and have it running in regular desktop mode.

I have a WD 250gb external harddrive and when i plug it in, it recognizes it by its name (batcave), although when i try and open it, this error message appears.

Cannot mount volume.

Unable to mount the volume 'Batcave 2'.

Details:
Mount: must be superuser to mount

Can anyone please give me a beginners guide to solving this issue, it really would make my life a lot easier

thanks

---

### Post by LowSky on 2008-10-30
is the drive formated to NTFS, sometimes you cannot mount because of a bad shut down from windows.

just use the drive from windows and properly unmount it before trying to use in Linux

---

### Post by ewingmaestro on 2008-10-30
I tired safely removing the software when it was plugged into the windows pc, but still the same error on linux

any other ideas?

---

### Post by thomasyen on 2008-10-30
Use sudo to edit your /etc/fstab file. I think you can find other threads concerning this around the forum so I will not go into detail unless you request it.

---

### Post by ewingmaestro on 2008-10-30
i have tried to follow them but i kept hitting dead ends, could you give you a more indepth help please? it would really be appreciated

thanks

---

### Post by thomasyen on 2008-10-30
Can you post your fstab file for us to see?
(Doesn't contain personal information; just shows the filesystems.)
I'll be back tomorrow night, it's 12:08 AM here and I've got school tomorrow, so I'll be leaving for now.

---

### Post by tarps87 on 2008-10-30
Can you plug the sub in and type ```
fdisk -l
```Then post the output here

---

### Post by ewingmaestro on 2008-10-30
Here is the results from sudo fdisk -l

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd643d643

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         400     3212968+  83  Linux
/dev/sda2             401         488      706860   83  Linux
/dev/sda3             489         489        8032+   c  W95 FAT32 (LBA)
/dev/sda4             490         490        8032+  ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000826dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1874    15052873+  83  Linux
/dev/sdb2            1875        1962      706860    5  Extended
/dev/sdb5            1875        1962      706828+  82  Linux swap / Solaris

Disk /dev/sdd: 8017 MB, 8017936384 bytes
202 heads, 59 sectors/track, 1313 cylinders
Units = cylinders of 11918 * 512 = 6102016 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1314     7825920    b  W95 FAT32

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS
alexander@alexander-laptop:~$

---

### Post by tarps87 on 2008-10-30
It looks like fat32 so try```
sudo mkdir /media/batcave
sudo mount -t vfat /dev/sdd1 /media/batcave
```

(fdisk -l without sudo should have listed just the external harddrive, sudo lists system disks aswell)

---

### Post by echo.whoami on 2008-10-30
try ```
sudo mount /dev/sdc /mnt
``` 
Does it mount there?

---

### Post by ewingmaestro on 2008-10-30
on windows xp the batcave is registered as ntsf, and when i type in sudo mount -t vfat /dev/sdd1 /media/batcave this appears:
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

what do i do??

also i tried your suggestion echo.woami and it asked me to specify the file system type

---

### Post by tarps87 on 2008-10-30
try
```
sudo mount -t ntfs /dev/sdd1 /media/batcave
```
This will be read only but has more chance of working.
Also try this
```
sudo mount -t auto /dev/sdd1 /media/batcave
```

---

### Post by ewingmaestro on 2008-10-30
after i enter the first command i get a lot of dialogue, am i meant to do anything within the dialogue??

---

### Post by tarps87 on 2008-10-30
Sorry my fault
```
sudo mount -t ntfs /dev/sdc1 /media/batcave
```
I was looking at the wrong drive, this one if ntfs formated, if it works you shouldn't see any dialog.

---

### Post by ewingmaestro on 2008-10-30
i just get the same dialogue, hmmm

---

### Post by tarps87 on 2008-10-30
Can you post the dialoge and wrap it with [code] tags

---

### Post by ewingmaestro on 2008-10-30
```

```alexander@alexander-laptop:~$ sudo mount -t ntfs /dev/sdc1 /media/BATCAVE 2
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
```

```

---

### Post by ewingmaestro on 2008-10-30
```
alexander@alexander-laptop:~$ sudo mount -t ntfs /dev/sdc1 /media/BATCAVE 2
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

```

---

### Post by tarps87 on 2008-10-30
```
sudo mount -t ntfs /dev/sdc1 /media/BATCAVE 2
```
There is a space BATCAVE 2 this should be BATCAVE\ 2
Unix is case sensitive, the easiest way is type /media/BA then this tab, if this auto completes you have typed it correctly

---

### Post by ewingmaestro on 2008-10-30
okay i did the command, and this message appeared 

fuse: failed to access mountpoint /media/BATCAVE 2: No such file or directory

how do i create the directory??

---

### Post by tarps87 on 2008-10-30
```
sudo mkdir mkdir /media/BATCAVE\ 2
```
I would suggest not using spaces as it makes it easier to access from the command line

---

### Post by ewingmaestro on 2008-10-30
problem absolutely solved thanks to you :)

you have been a tremendous help and i can only say im glad theres helpful people like yourself around.

thanks again

---

### Post by tarps87 on 2008-10-31
That's ok, glad I could help.
Could you mark the thread as solved please
howto:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

