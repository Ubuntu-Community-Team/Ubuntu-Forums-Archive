---
title: "permission problem with External HDD"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by tuskpc on 2008-05-16
External HDD: Western Digitals' "**My Book**" <500 GB>
Filetype: **msdos**

I am having a problem getting permission adding and deleting files to my external HDD.  It keeps telling me `My Book/': **Read-only file system**.

This is what I've tried, but it does not work.  *Any suggestions?*

Terminal:
> 
**$ sudo chmod 0777 My\ Book/**
chmod: changing permissions of `My Book/': Read-only file system
**$ ls -l**
total 72
lrwxrwxrwx   1 root    999     6 2008-05-06 18:12 cdrom -> cdrom0
drwxr-xr-x   2 root    999  4096 2008-05-06 18:12 cdrom0
drwxr-xr-x   2 root    999  4096 2008-05-06 18:12 cdrom1
drwx------ 133 tuskpc root 65536 1969-12-31 18:00 My Book
**$ sudo chmod 777 My\ Book/**
chmod: changing permissions of `My Book/': Read-only file system
**$ sudo chmod ugo+rwx My\ Book/**
chmod: changing permissions of `My Book/': Read-only file system



---

### Post by logos34 on 2008-05-16
ntfs is read-only (although if you're running gutsy or hardy ntfs-3g driver should be installed by defualt)

try using ntfs-config:
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

---

### Post by Aearenda on 2008-05-16
NTFS is read-write in Gutsy and Hardy. I think you need to unmount the drive to be able to change permissions on the mount point.

Anyway, see post 4 in this thread: [http://ubuntuforums.org/showthread.php?t=763752](http://ubuntuforums.org/showthread.php?t=763752) for how to make it usable by more users.

EDIT: Rereading the original post, I see the filetype is msdos - so this volume isn't NTFS at all!
Try post 16 in [http://ubuntuforums.org/showthread.php?t=789406](http://ubuntuforums.org/showthread.php?t=789406).

---

### Post by PinkFloyd102489 on 2008-05-16
You have to umount any drive to change its mountpoint permissions.

---

### Post by tuskpc on 2008-05-24
I'm sorry I'm took so long to reply - along with working 19 days straight, I messed up the configuration on my other Ubuntu system and was to tired to fix it... actually I still am.:rolleyes:

I tried what was suggested on another thread, here is what I got out of the terminal:

> 
**$ dmesg**
*to much info to cut & paste...*


**$ sudo fdisk -l**
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe211a2bc

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06


**$ ls -l /media**
total 68
lrwxrwxrwx   1 root   root     6 2007-10-30 11:57 cdrom -> cdrom0
drwxr-xr-x   2 root   root  4096 2007-10-30 11:57 cdrom0
drwx------ 133 tuskpc root 65536 1969-12-31 18:00 My Book


[B]$ sudo umount /dev/sdb1
$ sudo mount -t vfat /dev/sdb1 -o umask=000,uid=1000[/B]
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
For many more details, say  man 8 mount 



What do you think I did wrong?

---

### Post by Ptero-4 on 2008-05-24
The mount point itself is missing from your mount command.
It should be:
```
sudo mount -t vfat /dev/sdb1 -o umask=000,uid=1000 **/media/USBHDD**
```

---

### Post by Steve413z on 2008-05-24
```
**$ sudo chmod a+rw -R **** /media/My\ Book/**
```case sensitive capital R


-R (CAPITAL) makes it recursive

lowercase "a" means all users and groups, "+rw" means add read and write permissions

---

### Post by tuskpc on 2008-05-24
**$ sudo mount -t vfat /dev/sdb1 -o umask=000,uid=1000 /media/USBHDD**
[sudo] password for tuskpc: 
mount: mount point /media/USBHDD does not exist


$ **sudo chmod a+rw -R  /media/My\ Book/**
chmod: cannot access `/media/My Book/': No such file or directory


**$ sudo mount -t vfat /dev/sdb1 -o umask=000,uid=1000 /media/My\ Book/**
mount: mount point /media/My Book/ does not exist


**$ sudo mount -t vfat /dev/sdb1 -o umask=000,uid=1000 /media/My\ Book**
mount: mount point /media/My Book does not exist


**$ sudo mount -t vfat /dev/sdb  /dev/sdb -o umask=000,uid=1000**
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Steve413z on 2008-05-24
> **tuskpc said:**
> **$ sudo mount -t vfat /dev/sdb1 -o umask=000,uid=1000 /media/USBHDD**
[sudo] password for tuskpc: 
mount: mount point /media/USBHDD does not exist


$ **sudo chmod a+rw -R  /media/My\ Book/**
chmod: cannot access `/media/My Book/': No such file or directory


**$ sudo mount -t vfat /dev/sdb1 -o umask=000,uid=1000 /media/My\ Book/**
mount: mount point /media/My Book/ does not exist


**$ sudo mount -t vfat /dev/sdb1 -o umask=000,uid=1000 /media/My\ Book**
mount: mount point /media/My Book does not exist


**$ sudo mount -t vfat /dev/sdb  /dev/sdb -o umask=000,uid=1000**
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


unplug the HDD, reboot, plug it back in, hopefully it will recognize it
then try this again:

```
$ **sudo chmod a+rw -R  /media/My\ Book/**
```

---

### Post by chrisccoulson on 2008-05-24
Please see my replies in this thread: [http://ubuntuforums.org/showthread.php?p=4942422]("http://ubuntuforums.org/showthread.php?p=4942422")

You shouldn't need to play around with mount options for your external drive. It is very likely you have the same problem (corrupt filesystem). This issue crops up very frequently on these forums.

---

### Post by chrisccoulson on 2008-05-24
> **Steve413z said:**
> unplug the HDD, reboot, plug it back in, hopefully it will recognize it
then try this again:

```
$ **sudo chmod a+rw -R  /media/My\ Book/**
```

Won't work with FAT volumes!! They don't understand Unix file permissions, and all permissions on these filesystems are determined by mount options

---

### Post by tuskpc on 2008-05-24
> **Steve413z said:**
> unplug the HDD, reboot, plug it back in, hopefully it will recognize it
then try this again:

```
$ **sudo chmod a+rw -R  /media/My\ Book/**
```

Tried it and got the following:

> 
**$ ls -l** 
ls: cannot access audiobook: Input/output error
ls: cannot access videos: Input/output error
ls: cannot access misc chm, pdf and ps: Input/output error
... *these are folders I cannot access anymore*



It looks as if most of my backup files are now corrupted.  So much for backup.  ](*,)

---

### Post by Steve413z on 2008-05-24
> **tuskpc said:**
> Tried it and got the following:



It looks as if most of my backup files are now corrupted.  So much for backup.  ](*,)


did you create those folders while you were in ubuntu?

---

### Post by tuskpc on 2008-05-24
> **chrisccoulson said:**
> Yes, the above solutions won't work as your filesystem is broken. **Making sure the volume is unmounted first**, do the following in a terminal:
```
sudo dosfsck -a -v /dev/sdb1
```
...where /dev/sdb1 is your broken vfat volume.

just typed this in the terminal and got this:

> 
**$ sudo dosfsck -a -v /dev/sdb1   **
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00, 67:4a/54, 68:1d/1f, 69:41/fb, 70:30/16
  Not automatically fixing this.
Boot sector contents:
System ID "MSWIN4.1"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
     32768 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
  61040640 bytes per FAT (= 119220 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 122097664 (sector 238472)
  15258273 data clusters (499983089664 bytes)
63 sectors/track, 255 heads
        63 hidden sectors
 976768002 sectors total
/audiobook
  Contains a free cluster (5766443). Assuming EOF.
/videos
  Contains a free cluster (5182434). Assuming EOF.
/misc chm, pdf and ps
  Contains a free cluster (5577489). Assuming EOF.
.... *so on, and so forth*

Reclaiming unconnected clusters.
....
*two hours later*



---

### Post by Steve413z on 2008-05-24
theres a chance your hard drive might be dieing, better backup if you can

---

### Post by Steve413z on 2008-05-25
does this drive work ok in windows???

---

### Post by tuskpc on 2008-05-25
> **Steve413z said:**
> does this drive work ok in windows???

Yes, but I had to click a few folders for it to recognize the rest of the folders. 

 Also I had bought another My Book - that one was called a World Edition and... it was a huge piece of crap.  I will never buy another hardware part from Western Digital, at least until they wise up and support Free Software.

---

### Post by Steve413z on 2008-05-25
> **tuskpc said:**
> Yes, but I had to click a few folders for it to recognize the rest of the folders. 

 Also I had bought another My Book - that one was called a World Edition and... it was a huge piece of crap.  I will never buy another hardware part from Western Digital, at least until they wise up and support Free Software.


I've never had any problem with western digital, infact most of my external drives are "My Book"s

---

### Post by tuskpc on 2008-05-25
> **Steve413z said:**
> did you create those folders while you were in ubuntu?


Actually the hardware is around a year old, and was used to backup my window files before installing Ubuntu on another hard drive,

---

### Post by chrisccoulson on 2008-05-25
What did you see in your syslog when you followed my instructions in the thread I linked to?

---

### Post by tuskpc on 2008-05-25
> **chrisccoulson said:**
> What did you see in your syslog when you followed my instructions in the thread I linked to?



```

$ tail -f /var/log/syslog
May 25 11:01:59 tuskpc-laptop NetworkManager: <debug> [1211731319.568369] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_5000AAK_External_574341505732363036333536_0_0'). 
May 25 11:01:59 tuskpc-laptop NetworkManager: <debug> [1211731319.617812] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3041_1D4A'). 
May 25 11:01:59 tuskpc-laptop hald: mounted /dev/sdb1 on behalf of uid 1000
May 25 11:02:06 tuskpc-laptop ntpd[6301]: synchronized to 91.189.94.4, stratum 2
May 25 11:02:06 tuskpc-laptop ntpd[6301]: time reset +0.271154 s
May 25 11:02:06 tuskpc-laptop ntpd[6301]: kernel time sync status change 0001
May 25 11:03:55 tuskpc-laptop kernel: [  444.512962] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
May 25 11:03:55 tuskpc-laptop kernel: [  444.512976] Info fld=0x0
May 25 11:03:55 tuskpc-laptop kernel: [  444.512979] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
May 25 11:06:59 tuskpc-laptop ntpd[6301]: synchronized to 91.189.94.4, stratum 2
May 25 11:08:32 tuskpc-laptop kernel: [  720.914854] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
May 25 11:08:32 tuskpc-laptop kernel: [  720.914864] Info fld=0x0
May 25 11:08:32 tuskpc-laptop kernel: [  720.914866] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information


```

---

