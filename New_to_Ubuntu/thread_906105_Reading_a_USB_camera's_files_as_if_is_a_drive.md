---
title: "Reading a USB camera's files as if is a drive"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2008-08-31
How can i read my usb camera the same way as I do in XP..

Sometimes I use it to read/transfer flash cards that have files other than pictures on it

---

### Post by Pro-reason on 2008-08-31
> **Ducatiboy Stu said:**
> How can i read my usb camera the same way as I do in XP..

Sometimes I use it to read/transfer flash cards that have files other than pictures on it

I take it that the device is failing to automount.  You need to manually mount it then.  Try reading some guides such as [https://help.ubuntu.com/community/MountDevicesTroubleshooting](https://help.ubuntu.com/community/MountDevicesTroubleshooting).

---

### Post by Ducatiboy Stu on 2008-08-31
The camera mounts, as it brings up Fspot( or Picassa ) when it does

I just want to be able to browse the camera using nautilus..

---

### Post by Rocket2DMn on 2008-08-31
It may have already put an icon on your desktop - the device has to be mounted for the image program to read from it.

If you don't see it, please post the output of
```
sudo fdisk -l
mount
cat /etc/fstab
sudo blkid
```

---

### Post by solitaire on 2008-08-31
Check the camera settings.
It may have the option of connecting as a "Mass Storage" device.

My small Sony Cybershot auto-mounts if i set it to be a"Mass  Storage Device" as well as starting FSpot.
If I set it to connect as a "PictBridge" then it just starts FSpot and does not mount the camera.

---

### Post by Pro-reason on 2008-08-31
> **Ducatiboy Stu said:**
> The camera mounts, as it brings up Fspot( or Picassa ) when it does

I just want to be able to browse the camera using nautilus..

Then... browse it using Nautilus.

Automounted devices will usually be mounted at */media*.  Go to that location, or else you can find them by clicking on &#8220;Computer&#8221; in the &#8220;Places&#8221; menu.  If it is not there, then it is not properly mounted, and you'll have to follow solitaire's suggestion.

---

### Post by Ducatiboy Stu on 2008-08-31
Fspot downloads the pics, but I cant see the device as an icon or thru nautilus..



As per Solitair  ( sorry but the code wrap is not working )

ncts@ncts:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        6028    48371715    7  HPFS/NTFS
/dev/sda4            6029        7296    10185210    f  W95 Ext'd (LBA)
/dev/sda5            7237        7296      481918+  82  Linux swap / Solaris
/dev/sda6            6029        7178     9237312   83  Linux
/dev/sda7            7179        7236      465853+  82  Linux swap / Solaris

Partition table entries are not in disk order
ncts@ncts:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
none on /proc/bus/usb type usbfs (rw,devgid=46,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ncts/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ncts)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=ncts)
ncts@ncts:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1ca445cc-89ad-4201-9f2c-4d0fddc2355f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=41d29e5b-9c29-4251-8d7b-78476d7e747a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
#none /proc/bus/usb usbfs devgid= 124,devmode=664 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
ncts@ncts:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-041B" TYPE="vfat" 
/dev/sda2: UUID="86E07E37E07E2D95" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="9973d9a8-3970-415f-8cb9-6ad3b3f4d659" 
/dev/sda6: UUID="1ca445cc-89ad-4201-9f2c-4d0fddc2355f" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="41d29e5b-9c29-4251-8d7b-78476d7e747a" 
ncts@ncts:~$

---

### Post by Rocket2DMn on 2008-08-31
Did you have your camera plugged in when you posted those commands?  If not, plug it in then run the commands again, please :)

---

### Post by malspa on 2008-08-31
How about using a USB memory card reader -- not even bothering with plugging your camera in?  I use mine with various distros and also with XP, just browse the files with the file browser of choice.

---

### Post by Pro-reason on 2008-08-31
Check the camera manual to see what it says about how it connects to a computer.  Follow the instructions for making it use [MSC]("http://en.wikipedia.org/wiki/USB_mass_storage_device_class").

Then plug it in and type “*sudo fdisk -l*” or “*sudo blkid*”.

For very verbose system information, type “*sudo lshw*”.

Put *[noparse]```
..
```[/noparse]* tags around anything you paste.

---

