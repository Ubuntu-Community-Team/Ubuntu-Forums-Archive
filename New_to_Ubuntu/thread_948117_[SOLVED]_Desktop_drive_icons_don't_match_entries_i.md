---
title: "[SOLVED] Desktop drive icons don't match entries in fstab"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by akelsall on 2008-10-14
This is just an annoyance, but I'd still like to know why it's happening. What's happening is I've got a slave SATA drive that has my old Windows setup (and it has three partitions). I created mount points named winC, winD, and winE that correspond to my old Windows partitions. They automount just fine during boot, but on the desktop, the drive names are DRV3_VOL1, DRV3_VOL2, and DRV3_VOL3. My question is why don't the desktop icon names match what's in /etc/fstab? Here's a partial output from the mount command, and my fstab. I thought maybe changing the symlink under /dev/disk/ would do the trick, but after deleting the old symlink (which had DRV3_VOL1 pointing to ../../sdb1) and creating a new one with the name winC, I unmounted and remounted the drive, and it STILL shows up as DRV3_VOL1. Any ideas?

Thanks,

Andy

----------------------------------------------
 mount | grep sdb
/dev/sdb5 on /media/winD type fuseblk (rw,nosuid,nodev,noatime,allow_other,allow_other,blksize=4096)
/dev/sdb6 on /media/winE type fuseblk (rw,nosuid,nodev,noatime,allow_other,allow_other,blksize=4096)
/dev/sdb1 on /media/winC type fuseblk (rw,nosuid,nodev,noatime,allow_other,allow_other,blksize=4096)

$ls -l /dev/disk/by-label
total 0
lrwxrwxrwx 1 root root 10 2008-10-14 17:49 DRV3_VOL2 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2008-10-14 17:49 DRV3_VOL3 -> ../../sdb6
lrwxrwxrwx 1 root root  9 2008-10-14 22:26 WinC -> /dev/sdb1

---

### Post by Patb on 2008-10-14
Akelsall, you can set the partition label to whatever you want with:
```
sudo tune2fs -L your_label /dev/sdX
```
where /dev/sdX is the device name of the partition you wish to label.  

You can also use the label to identify your partitions in fstab if you wish. See Bodhi.Zazen's [How-to fstab]("http://ubuntuforums.org/showthread.php?&t=283131"). 

Hope this helps. Cheers, Pat.

---

### Post by akelsall on 2008-10-15
Thanks for the info Pat. One thing I forgot to mention was that I'm trying to mount an NTFS fs. From what I read in the man page for the tune2fs command, it only applies to ext2/ext3 filesystems. Is that correct. Guess that's why I'm getting the following error when using it:

Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

Do you know of a way to change the name of the label that appears for an icon on the desktop when an NTFS filesystem is mounted? 

One thing I DID learn is that if you mount a fs under /media and mount it, it appears as an icon on the Desktop. If mounted under any other directory, it will NOT appear on the Desktop. Is that the nature of Linux (i.e. if you mount a fs under /media, it automatically creates an icon on the Desktop)?

Thanks,

Andy

---

### Post by wannadumpwindows on 2008-10-15
Have a look at this link. It offers solutions for a bunch of different file systems. I just used it two days ago for a USB flash drive, and it worked perfectly.

[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by drs305 on 2008-10-15
For NTFS, install ntfsprogs and then to label:
```
ntfslabel <device> <label>
```

---

### Post by Patb on 2008-10-15
> **akelsall said:**
> From what I read in the man page for the tune2fs command, it only applies to ext2/ext3 filesystems.
Yes, that's right Andy. The link given by Wannadump seems quite comprehensive.  
> Do you know of a way to change the name of the label that appears for an icon on the desktop when an NTFS filesystem is mounted? 
Covered by that link I think. 
> One thing I DID learn is that if you mount a fs under /media and mount it, it appears as an icon on the Desktop. If mounted under any other directory, it will NOT appear on the Desktop. Is that the nature of Linux (i.e. if you mount a fs under /media, it automatically creates an icon on the Desktop)?
Not so much Linux as Gnome I think, or perhaps Debian/Ubuntu. I remember another distribution used to mount 'other' file systems under /mnt/.

Good luck, Pat.

---

### Post by akelsall on 2008-10-16
Well, it turns out the ntfslabel command did the trick. However (at least in my case), I had to reboot for it to take effect. When I used ntfslabel and remounted my drives, they still came up with the DRV3_VOLX label under their icons. After rebooting, they came up with the label I wanted. 

If anyone needs this, just use the syntax "**[COLOR="Blue"]sudo apt-get install ntfsprogs[/COLOR]**". That will install ntfsprogs, which is actually a collection of "tools" for NTFS filesystems (including ntfslabel). See the developer's website for more info:

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

The other info provided will be useful in the future. Thanks much.

Andy

---

