---
title: "XP not booting in a dual boot"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by vampur on 2008-08-22
Dear members 

I installed the ubutnu 8.4 and my previous version is xp and i am not able to acces that os and also not able to viw the disk that is NTFS . and cann't acces the data dere 

i tried many way to make it dual but it doesn't and while booting it shows me the option for xp but it doesn't 

so is dere any way dat i can view the NTFS files.. 



Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c112c10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9729    62790052+   f  W95 Ext'd (LBA)
/dev/sda5            1913        5736    30716248+   b  W95 FAT32
/dev/sda6            5737        7011    10241406    b  W95 FAT32
/dev/sda7            7012        8469    11711353+   b  W95 FAT32
/dev/sda8            8470        9669     9638968+  83  Linux
/dev/sda9            9670        9729      481918+  82  Linux swap / Solaris


Thankx

---

### Post by aloshbennett on 2008-08-22
are you able to mount /dev/sda1 ?

---

### Post by vampur on 2008-08-22
Dat was the Outpout when i did so ??

could u please help me out 


 mount /dev/sda1 
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

---

### Post by vampur on 2008-08-22
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=65adad4e-99ef-4552-9140-478faad5eff7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=65adad4e-99ef-4552-9140-478faad5eff7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by vampur on 2008-08-22
is dere any way dat i can reslove dis prob???????

---

### Post by WRDN on 2008-08-22
To mount a disk in Ubuntu, you need to type (in the Terminal):

```
sudo mkdir /media/windows
```

This is where the disk will be mounted. You can replace the word "windows" with something else if you wish.

Now, type:

```
sudo mount /dev/sda1 /media/windows
```

Sometimes this does not work, so, to forcefully mount the disk:

```
sudo mount /dev/sda1 /media/windows -o force
```

---

### Post by Nepherte on 2008-08-22
Maybe this works:
[LIST]
[*]Create a mount point:
```
sudo mkdir /media/WindowsXP
```
[*]Mount the disk to /media/WindowsXP:
```
sudo mount -t ntfs /dev/sda1 /media/WindowsXP
```
[/LIST]

edit: too late :)

---

### Post by vampur on 2008-08-22
i Tried many things but couldn't understand what to do and is dere any way dat i can have my data dat was in dat xp sfaely ???

some output is  : 
sudo mount -o force -t ntfs /dev/sda1 /media/WindowsXP
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?


Please help me

---

### Post by vampur on 2008-08-22
any help 
????

---

### Post by WRDN on 2008-08-22
Try entering the command in the format(s) show above.

You don't need to enter "-t" or "ntfs". Just:

```
sudo mount /dev/sda1 /media/windows -o force
```

For this command to work, there must be a folder called "windows" in /media.

---

### Post by philinux on 2008-08-22
Post you fstab

cat /etc/fstab

Don't forget to put code(#) marks around it.

---

### Post by vampur on 2008-08-22
> **WRDN said:**
> Try entering the command in the format(s) show above.

You don't need to enter "-t" or "ntfs". Just:

```
sudo mount sudo mount /dev/sda1 /media/windows -o force
```

For this command to work, there must be a folder called "windows" in /media.

for the outpus is 
sudo mount sudo mount /dev/sda1 /media/windows -o force
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

### Post by vampur on 2008-08-22
> **philinux said:**
> Post you fstab

cat /etc/fstab


the output for this  


Don't forget to put code(#) marks around it.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=65adad4e-99ef-4552-9140-478faad5eff7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=741ae686-8436-4ee7-96f2-cdb7000bc9df none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by WRDN on 2008-08-22
> **vampur said:**
> for the outpus is 
sudo mount sudo mount /dev/sda1 /media/windows -o force
Usage: mount -V                 : print version
[Output]

Sorry, the mistake was in my post. The word "sudo mount" have been written twice, and only need to be entered once.
The actual command is:

```
sudo mount /dev/sda1 /media/windows -o force
```

---

### Post by vampur on 2008-08-22
> **WRDN said:**
> Sorry, the mistake was in my post. The word "sudo mount" have been written twice, and only need to be entered once.
The actual command is:

```
sudo mount /dev/sda1 /media/windows -o force
```

gaurav@Gaurav:~$ sudo mount /dev/sda1 /media/windows -o force
mount: you must specify the filesystem type

---

### Post by Nepherte on 2008-08-22
Having had a conversation with the topic starter over msn, I suspect there is something wrong with the disk he tries to mount. On that partition he has a xp installation, which is listed in the grub boot loader. When he selects this option instead of ubuntu, he doesn't get into xp. That, or the entry points to a wrong place. It might explain why he doesn't get the partition mounted in ubuntu.

---

