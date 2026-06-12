---
title: "How do I mount an external hard-drive via SSH?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by TMcKSmith on 2008-07-24
I'm running Ubuntu Server w/ xubuntu xwindows at home.
I was fooling around via SSH and had to restart the system using:
sudo shutdown -r now
after the system reboot, my external hard drive is no longer available (I'm guessing because I'm no longer logged into xwindows - it usually mounts automatically).  Is there a way I can do this remotely?  Or a way I can set the external drive to mount automatically on restart?  Thanks!

---

### Post by Potatoj316 on 2008-07-24
Yes, to make it mount automatically you can add a line to your fstab.  To mount it via ssh (assuming you are connected via ssh) do this
```
sudo mount /dev/usb /media/disk
```
you might have to use /dev/hdb1 and you might have to create /media/disk first

---

### Post by TMcKSmith on 2008-07-24
how do I "create" /media/disk

when I startx and login it mounts to /media/Venus/ automatically


but when remotely I type

root@xxxx:~# sudo mount /dev/usb /media/Venus
mount: mount point /media/Venus does not exist

---

### Post by iDaniel on 2008-07-24
Just a very simple: 

```
mkdir /media/Venus/
```

Which will make the directory.

---

### Post by TMcKSmith on 2008-07-24
> **iDaniel said:**
> Just a very simple: 

```
mkdir /media/Venus/
```

Which will make the directory.

root@bxxxxx:~# sudo mount /dev/usb /media/Venus
mount: special device /dev/usb does not exist

---

### Post by SeanHodges on 2008-07-24
If you are trying to mount the external drive the same way as when you normally log in through the graphical interface (e.g. it only mounts when plugged in) you can use:

gnome-mount -n

It won't look like it's done much, but this should detect your external drive and mount it to something like /media/usbdisk (check the /media directory afterwards).

The "-n" basically tells it not to try and pop up a graphical dialog if theres a problem, which is a good idea if you've SSH'd remotely.

I've had reports that this hasn't worked for some people, I'm not sure why but it's worked for me every time.

---

### Post by TMcKSmith on 2008-07-25
that gives me:

root@xxxxx:~# gnome-mount -n
X11 connection rejected because of wrong authentication.
Use --hal-udi, --device or --pseudonym to specify volume


I won't be home (where the server is) for a few days, and I'd really like to get this mounted so I can access certain files that are on the drive.  Thanks for all the help thus far.

---

### Post by PinkFloyd102489 on 2008-07-25
Run

```
fdisk -l
```

As in lowercase L. This will show you all of the available drives attached to the machine. Assuming you only have one HD and the external, the external would probably be /dev/sdb1. So here's how the command would work.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/Venus
```

Assuming that the filesystem type is NTFS. If it's FAT32, swap out ntfs-3g for vfat.

To get it to start automatically, enter this into /etc/fstab.

```
/dev/sdb1 /media/Venus ntfs 0 1
```


Again swap out ntfs with vfat if the filesystem is FAT.

---

### Post by TMcKSmith on 2008-07-25
thanks.  here's what's happening now:

root@xxxxx:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        9483    66404677+  83  Linux
/dev/sda3            9484        9726     1951897+   5  Extended
/dev/sda5            9484        9726     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7259143f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001    7  HPFS/NTFS



looks like you were right about /dev/sdb1 (thanks), but now when I go onto the next step:

root@xxxxx:~# sudo mount -t ntfs-3g /dev/sdb1 /media/Venus
fuse: failed to access mountpoint /media/Venus: No such file or directory


any suggestions?

---

### Post by TMcKSmith on 2008-07-25
nevermind!  figured it out through common sense - just had to 

mkdir /media/Venus/

thanks for all your help - much appreciated.

---

### Post by PinkFloyd102489 on 2008-07-25
> **iDaniel said:**
> Just a very simple: 

```
mkdir /media/Venus/
```

Which will make the directory.


*slaps TMcKSmith in the forehead*

---

