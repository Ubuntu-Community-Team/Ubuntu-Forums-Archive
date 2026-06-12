---
title: "Kubuntu Doesn't Mount non-OS HD"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by Wiking on 2011-09-15
Hi, I installed Kubuntu 11.04 it runs, but it will not mount one of my HD's which is in NTFS format.

It mounts another NTFS HD but not this one.

When booting Kubuntu 11.04 I get the following messages:

1- "Serious errors were found while checking the disk drive for /boot"

and

2- "An error occurred while mounting /boot"

I ignored and skipped those messages.

I took the following screenshot after logging into Kubuntu and attempting to browse the HD.


I also downloaded and installed Disk Utility 2.32.1 and checked the said HD and no sectors are damaged, and appears healthy.

Where it says Mount Point it says: Not Mounted

 Any suggestions?

---

### Post by Elfy on 2011-09-15
If you use the forum attachment system it's easy to see images - as it stands I can't access those.

It's possible that the drive needs checking from a windows system given the error.

[http://ubuntuforums.org/showpost.php?p=4527031&postcount=4](http://ubuntuforums.org/showpost.php?p=4527031&postcount=4)

---

### Post by Wiking on 2011-09-15
I attached the image below.

Also I was searching the forum and I think I might have found the solution in this thread: [http://ubuntuforums.org/showthread.php?t=64632]("http://ubuntuforums.org/showthread.php?t=64632")

I ran ```
sudo kate /etc/fstab
```

and I got the following results: 

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd6 during installation
UUID=bf8384ed-3a1d-4ca8-bc3f-70d6fd8fcda1 /               ext4    errors=remount-ro 0       1
/dev/sdd1       /boot           ext2    defaults        0       2
# /home was on /dev/sdd7 during installation
UUID=e9cc4121-9cce-4f52-961c-02555f88e05f /home           ext4    defaults        0       2
# swap was on /dev/sdd5 during installation
UUID=d795cdd0-853e-4402-92be-ad31e8f8694a none            swap    sw              0       0

```

I'm not sure where to go from here.

When I ran sudo fdisk -l the said HD appeared as /dev/sdd1, but the above code looks like the HD with the Linux Swap.

---

### Post by Wiking on 2011-09-15
Here are the results I got when running sudo fdisk -l: (The drive is the 650 GB one)

```
 Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00046f0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      250880   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       11878    95156225    5  Extended
/dev/sda5              32         275     1951744   82  Linux swap / Solaris
/dev/sda6             275        1491     9764864   83  Linux
/dev/sda7            1491       11878    83437568   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1ebb1ebb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       42560   341863168+   7  HPFS/NTFS

Disk /dev/sdd: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc1d5f56f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       77826   625129472    7  HPFS/NTFS
 
```

---

### Post by Elfy on 2011-09-15
Ok - the error refers to you trying to mount it to /boot - that is owned by root :)

You're right to be looking at fstab - you can do it manually - I do or you can use a gui app - pysdm it's in the repos. 

IF you want to do it manually I would first suggest using UUID's you can get that from 

```
sudo blkid
```

Then use that when you edit fstab (small note best to not use sudo to open a graphical app - in kubuntu you can use kdesudo :- ```
kdesudo kate
``` )

[https://help.ubuntu.com/community/Fstab#ntfs](https://help.ubuntu.com/community/Fstab#ntfs)

Now, that example mounts the drive to /media/windows - you can use whatever you like - but you need to create the folder

```
sudo mkdir /media/windows
```

That will cause the drive to show on your desktop, if you prefer it not to show you can use /mnt instead

```
sudo mkdir /mnt/windows
```

---

### Post by Wiking on 2011-09-15
Wow. Thanks a bunch, that was complex but at least I learned something.

I can see my drive now:D

I entered the UUID syntax wrong a couple of times and got this: 

```
QFileSystemWatcher: failed to add paths: /home/User/.config/ibus/bus
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /root/.config/ibus/bus
kate(3652)/kdeui (kdelibs) KXMLGUIClient::~KXMLGUIClient: 0x17c2de8 deleted without having been removed from the factory first. This will leak standalone popupmenus and could lead to crashes. 
kate(3652)/kdeui (kdelibs) KXMLGUIClient::~KXMLGUIClient: 0x1907f00 deleted without having been removed from the factory first. This will leak standalone popupmenus and could lead to crashes. 
kate(3652)/kdeui (kdelibs) KXMLGUIClient::~KXMLGUIClient: 0x1844788 deleted without having been removed from the factory first. This will leak standalone popupmenus and could lead to crashes.  
```

But I had fstab backed up before, and kept replacing the UUID syntax until I got it to work. 

Regarding the coded message above will I have to worry about my system being unstable or crashing? fstab is the same except for the one UUID line I changed.

Again thanks.

If anybody is having the same problem here is a link that shows you how to write the syntax in the fstab file:

[http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/]("http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/")

---

