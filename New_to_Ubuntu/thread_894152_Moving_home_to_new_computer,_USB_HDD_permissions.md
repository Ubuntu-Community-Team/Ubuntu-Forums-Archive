---
title: "Moving home to new computer, USB HDD permissions"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by C.S.Cameron on 2008-08-19
I am building my wife a new computer.
I hope to copy her old home folder to it, her home folder rar'd is 14 GB.
How do I copy this to an external USB hard drive, (PATA).
I am having many problems with permissions. 
Can not even get permission to write to a secondary internal HD for transfer later.
XUbuntu is installed on one partition of the USB drive, The partition I want to write to is FAT32.
I can write to this partition ok from windows or when booted from this disk.
Her old computer will not boot from the USB.
Seems like it should be as simple as plugging in a thumb drive and copying to it>

---

### Post by Bruce M. on 2008-08-19
> **C.S.Cameron said:**
> I am building my wife a new computer.
I hope to copy her old home folder to it, her home folder rar'd is 14 GB.
How do I copy this to an external USB hard drive, (PATA).
I am having many problems with permissions. 
Can not even get permission to write to a secondary internal HD for transfer later.
XUbuntu is installed on one partition of the USB drive, The partition I want to write to is FAT32.
I can write to this partition ok from windows or when booted from this disk.
Her old computer will not boot from the USB.
Seems like it should be as simple as plugging in a thumb drive and copying to it>

[LIST=1]
[*][File Permissions]("http://www.psychocats.net/ubuntu/permissions")
[*]Check out QuickStart in my signature. That will do what you want, note that it is a GNOME app but works well with Xubuntu 8.04.1
[*]To get drive or partition permission:
[/LIST]
```

sudo mount -a
sudo chown YOURNAME /media/mount_point_on_usb_drive
sudo chmod 770 /media/mount_point_on_usb_drive

```
Hope this helps.
Bruce

---

### Post by C.S.Cameron on 2008-08-19
When I gksu nautilus and try to change permissions of the drive to read write I am told that the drive is read only.
All I want to do is drop a tar file onto it.

---

### Post by Bruce M. on 2008-08-19
> **C.S.Cameron said:**
> When I gksu nautilus and try to change permissions of the drive to read write I am told that the drive is read only.
All I want to do is drop a tar file onto it.

Did you run the three terminal commands given above?

When I install Ubuntu fresh, my second HD is always owned by root, but since I create a mount point with gparted while installing:

sdb1 mountpoint: /media/Data
my commands are:
```

sudo mount -a
sudo chown bruloo /media/Data
sudo chmod 770 /media/Data
```
It never fails, I have read & write access.

Have a nice day.
Bruce

**EDIT:** You might want to look at this too, I don't know if it does DVD's:

**multicd**
Backup your data to CD-R/CD-RW
multicd provides an easy way to backup a large number of files to multiple
CDs. Give multicd the files/directories you want backed up and it will
create as many CDs as it needs to, prompting the user to put in a new disc
whenever needed. It can be configured to run in a multi-threading mode,
where it will burn one image to a disc while it is copying files to another
image. This feature can be disabled for slower machines.

---

### Post by C.S.Cameron on 2008-08-19
Thanks Bruce:
When I try above commands it tells me 
ivana@ivana-desktop:~$ sudo mount -a
Password:
ivana@ivana-desktop:~$ sudo chown ivana /media/EXTERNAL
chown: changing ownership of `/media/EXTERNAL': Read-only file system
ivana@ivana-desktop:~$ sudo chmod 770 /media/EXTERNAL
chmod: changing permissions of `/media/EXTERNAL': Read-only file system
and I still can't write to it.
Cork

---

### Post by Bruce M. on 2008-08-19
What does:
```
sudo fdisk -l
```
tell you.

Post the output here please.

EDIT: More info here: [Re: /dev/sdb won't show]("http://ubuntuforums.org/showthread.php?t=874729&highlight=%2Fdev%2Fsdb+won%27t+show")

and here: [Re: External Hard Drive - Cannot Mount Drive]("http://ubuntuforums.org/showpost.php?p=5555296&postcount=4")

---

### Post by C.S.Cameron on 2008-08-19
ivana@ivana-desktop:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4810    38636293+  83  Linux
/dev/hda2            4811        4998     1510110    5  Extended
/dev/hda5            4811        4998     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 9237 MB, 9237086208 bytes
255 heads, 63 sectors/track, 1123 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1023     8217216    7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1530    12289693+  83  Linux
/dev/sda2            1531        2181     5229157+  82  Linux swap / Solaris
/dev/sda3            2182       19457   138769470    7  HPFS/NTFS

---

### Post by C.S.Cameron on 2008-08-19
Seems my wife's computer was the only one that could not write to this FAT 32 partition, she could write to ext 3 partition ok but it was too small.
I deleted the FAT partition, enlarged the ext 3 and reformatted what was left back to FAT 32.
Now it is accessible.

---

### Post by Bruce M. on 2008-08-19
> **C.S.Cameron said:**
> Seems my wife's computer was the only one that could not write to this FAT 32 partition, she could write to ext 3 partition ok but it was too small.
I deleted the FAT partition, enlarged the ext 3 and reformatted what was left back to FAT 32.
Now it is accessible.

Well, that's another way. Something I didn't think of as I have no idea of your setup.

Glad to see you can access it though.
Bruce

---

