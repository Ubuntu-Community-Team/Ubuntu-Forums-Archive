---
title: "Trying to salvage pictures from a netbook using Ubuntu USB drive."
date: 2013-06-20
forum: New to Ubuntu
---

### Post by herrdresservonfyre on 2013-06-20
it's an HP Mini netbook, running Windows XP. Windows won't boot because there is a missing or corrupt file. I can't replace the file because I don't have a Windows disk, and the netbook has no optical drive.

When I boot from the USB, everything runs, but the windows partition will NOT mount. I've tried mounting it using the GUI and the terminal. Every attempt ends up with[COLOR=#000000] [FONT=verdana]"failed to write lock '/dev/sda1': Resource temporarily unavailable".[/FONT][/COLOR][COLOR=#DDDDDD][FONT=verdana]

[/FONT][/COLOR]Any help would be greatly appreciated, I'm trying to save a few hundred pictures and videos of my son's first 2 years!

---

### Post by MidnightGrey on 2013-06-20
what is the output of
```
 sudo fdisk -l
```
and 
```
 sudo blkid 
```

edit: also i believe HP Mini's come with a partition called HP_Tools or Recovery or something similiar which contains tools used to repair windows in situations like these, similiar to a Windows repair disk.

---

### Post by herrdresservonfyre on 2013-06-20
fdisk
>  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   312560639   156279296    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8019 MB, 8019509248 bytes
256 heads, 44 sectors/track, 1390 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2264    15663103     7830420    b  W95 FAT32



blkid:
> 
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="CA541B70541B5F0F" TYPE="ntfs" 
/dev/sdb1: LABEL="JAS_DAMIAN" UUID="7E96-0940" TYPE="vfat" 


---

### Post by MidnightGrey on 2013-06-20
what commands have you tried already?
have you tried:

```
 
sudo mkdir /media/win
sudo mount -t ntfs-3g /dev/sda1 /media/win

```

---

### Post by herrdresservonfyre on 2013-06-20
> ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.



was the result of those commands. This is the first time it has said that.

---

### Post by MidnightGrey on 2013-06-20
Your hard drive may be corrupt.
Any possibilty you can perform a chkdsk on it? from a windows environment.

---

### Post by herrdresservonfyre on 2013-06-20
That's what I was afraid of.  I can't chkdsk it, Windows won't even start to boot.

---

### Post by daengbo on 2013-06-20
> **herrdresservonfyre said:**
> That's what I was afraid of.  I can't chkdsk it, Windows won't even start to boot.

Try using testdisk or scrounge-ntfs
```
apt-get install testdisk scrounge-ntfs
```

---

### Post by MidnightGrey on 2013-06-20
Ideally you want to use chkdsk, however if you dont have a Windows environment you can try ntfsfix.
type *'ntfsfix -V'  *to check to see if you have it installed or not.

if you do run this command:
```

sudo ntfsfix /dev/sda1

```

if do you not have ntfsfix installed use this code to install it. You may need internet access.
```


sudo apt-get install ntfsprogs


```

---

### Post by herrdresservonfyre on 2013-06-20
sorry... heres what I got after runnng ntfsfix

> Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.



---

### Post by MidnightGrey on 2013-06-20
You need to enable the universe repository, to do this you can goto
Ubuntu Software Centre > Edit > Software Sources > Ubuntu Software; Enable the universe entry (2nd from the top).

or just copy past this command.
```
 

sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu $(lsb_release -sc) main universe"


```

---

### Post by herrdresservonfyre on 2013-06-20
after running ntfsfix:
> Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.



---

