---
title: "Error &quot;Unsupported operation&quot; creating new folder."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by amit.padhy on 2008-08-05
Hello everyone!!

hey i am getting an error like this:

```
Error "Unsupported operation" creating new folder.
```

i also cannot create new files here.

can anyone give me a suggestion.

i am using ubuntu 7.10 and only this partition shows errors like this.

is it a bug by any chance. or some fragmentation problem,,or .......??

---

### Post by sharks on 2008-08-05
open up terminal, the location is usually in the home folder. paste this:

> mkdir amit


and tell me whether it shows any error now or not.

---

### Post by drs305 on 2008-08-05
You will probably have to give us a bit more information, such as the specific command you are trying to run. Are you trying to create a folder or file with a space in the name, creating a file in a system folder, etc? We can help given a specific example of what you are trying to do.

---

### Post by amit.padhy on 2008-08-05
ok
i have 5 partitons on my hard disk...out of which i am not able to create new files,new folders ,copy files from other partitions,... on only one of them.

but i can read the files,the folders,rename them,and even delete files and folders...and copy from them to other partitions......

and there are no google search results..as in i feel this is the first time anyone is seeing a problem like this...

i am able to create  even through terminal...
i get:
```
mkdir: cannot create directory `amit': Operation not supported

```

please help!!

---

### Post by amit.padhy on 2008-08-05
pretty strange things are happenning!!
i am able to write the files/folders back into this partition after cutting them to another partiton....
can it be a viruss????i mean ...i know linux rarely has viruses....

---

### Post by drs305 on 2008-08-05
If these partitions are all mounted with fstab (automatically at boot) please post the results of:
```
cat /etc/fstab
```
and tell us the partition you are having problems with.

---

### Post by amit.padhy on 2008-08-05
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=7d5e9abf-d07c-4ef0-927c-d0d938d9b1a3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb9
UUID=64e813af-b56f-406a-bd7b-4d0608913003 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

/dev/sda5       /media/downloads        ntfs 0 0 0 0

/dev/sda6       /media/setups   ntfs 0 0 0 0

/dev/sda7       /media/photos   ntfs 0 0 0 0

/dev/sda8       /media/songs    ntfs 0 0 0 0

/dev/sda1       /media/acads    ntfs 0 0 0 0

```

now i am talking about the downloads partition...

---

### Post by drs305 on 2008-08-05
I would change the fstab to look like this:

```
/dev/sda5 /media/downloads ntfs-3g uid=1000,gid=100,dmask=007,fmask=117 0 0

```

This will give you (uid=1000) and your group (gid=1000) ownership of this folder and not allow others to access the folder/files. I would actually change all your ntfs entries to reflect the above.

For a less restrictive entry, you could substitute "umask=000" for the dmask/fmask entries, but it will give access, write and execute capabilities to anyone.

To backup and edit fstab (example uses gedit but you can use nano, etc):
```

sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

```

To allow these changes to take effect (disregard the 'busy' messages):
```

sudo umount -a
sudo mount -a

```

---

### Post by ByteJuggler on 2008-08-05
> **amit.padhy said:**
> pretty strange things are happenning!!
i am able to write the files/folders back into this partition after cutting them to another partiton....
can it be a viruss????i mean ...i know linux rarely has viruses....

No.  It's much more likely permissions issues (mounting permissions, possibly.)

Please post the result of back here (please copy and paste the commands into a terminal, or press alt-f2 and past it into the window that pops up):

```
gksudo fdisk -lu >fdisk.txt; gedit fdisk.txt
```

Also post the output of:

```
gedit /etc/fstab
```

And finally:

```
mount >mount.txt; gedit mount.txt
```

---

### Post by amit.padhy on 2008-08-05
@drs205

it does not work...
same error message...

and two days back it was perfectly fine....
will it help if i say that this partition is used for downloading stuff from the intranet/LAN here(dc++)...so maybe thare are too many read-write-delete proccesses...

---

### Post by amit.padhy on 2008-08-05
Here is my fdisk -l output

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x002c002c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3946    31696213+   7  HPFS/NTFS
/dev/sda2            5044       19456   115772422+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        3947        5043     8811652+  83  Linux
/dev/sda5            5100        8924    30716248+   7  HPFS/NTFS
/dev/sda6            8924       12748    30716248+   7  HPFS/NTFS
/dev/sda7           12748       16572    30716248+   7  HPFS/NTFS
/dev/sda8           16572       19456    23171368+   7  HPFS/NTFS
/dev/sda9            5044        5099      449757   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by drs305 on 2008-08-05
> **amit.padhy said:**
> Here is my fdisk -l output

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, **19457** cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x002c002c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3946    31696213+   7  HPFS/NTFS
/dev/sda2            5044       **19456**   115772422+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        3947        5043     8811652+  83  Linux
/dev/sda5            5100        8924    30716248+   7  HPFS/NTFS
/dev/sda6            8924       12748    30716248+   7  HPFS/NTFS
/dev/sda7           12748       16572    30716248+   7  HPFS/NTFS
/dev/sda8           16572       **19456**    23171368+   7  HPFS/NTFS
/dev/sda9            5044        5099      449757   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I notice that the cylinder numbers are off by 1. On my computers, the numbers always match. That may explains the error message and maybe your problem. There is an app called 'testdisk' you can run to check your partitions. Run it with 'sudo'. I would use the Analyse mode only unless you are sure you know what would happen next.

And if you try to make changes, make a backup of your data first!

---

