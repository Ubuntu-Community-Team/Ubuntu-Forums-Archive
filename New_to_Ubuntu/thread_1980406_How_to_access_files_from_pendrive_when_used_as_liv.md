---
title: "How to access files from pendrive when used as live usb"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by Hanzel Jesheen on 2012-05-15
Hello,

I have recently installed Ubuntu 12.04 on a live pendrive. It works great, but i'm not able to access the files stored in the pendrive while i'm in ubuntu. Please Help.

---

### Post by Hanzel Jesheen on 2012-05-15
Can i proceed as shown in [http://www.pendrivelinux.com/sharing-files-between-ubuntu-flash-drive-and-windows/]("http://www.pendrivelinux.com/sharing-files-between-ubuntu-flash-drive-and-windows/"). I'm using ubuntu 12.04 and article is for upto 11.10.

---

### Post by Lisiano on 2012-05-15
When you use a USB drive as a LiveUSB, you can issue this to remount it as writable then proceed to modify it
```
sudo mount -o rw,remount,umask=000 /cdrom
``` I think that is where it was, just poke in the first level / directories, the one that has the same stuff as the USB is the one you need.

---

### Post by prshah on 2012-05-15
> **Hanzel Jesheen said:**
> I have recently installed Ubuntu 12.04 on a live pendrive. It works great, but i'm not able to access the files stored in the pendrive while i'm in ubuntu. Please Help.

When using a "live pendrive" (with persistance), the files you save are saved into a file called "casper-rw" which is present in the root of the pen drive.

The files you create are present in casper-rw/home/ubuntu/.

To mount casper-rw in LINUX, you can use the following commands```
sudo mount -o loop /media/[color=red]pendrive[/color]/casper-rw  /mnt 
``` (Replace "pendrive" with the mount directory of your pendrive).

This means that files saved your live "desktop" will now be available at /mnt/home/ubuntu/Desktop/

Don't forget to UNMOUNT when done!```
sudo umount /mnt
```

If you want to be able to access these files in WINDOWS, then you cannot save it to the default location in the live session (/home/ubuntu/). Instead, save/copy it to "/cdrom" (though you need elevated priviliges to do so).

Please post back if the information is unclear or if you want more information.

---

### Post by HiImTye on 2012-05-15
the easiest method is just to use gparted and create separate partitions on the disk. here is how I have mine laid out:

1. system - FAT32 (where the liveUSB image is)
2. casper-rw - EXT4 (for persistence)
3. storage - FAT32

partition 1 is the smallest that it can be (with a 1MB buffer, as sometimes gparted complains if you don't leave one when you shrink the partition)
partition 2 is a decent size for a persistence
partition 3 is the remainder of the USB drive, for storage and for sharing files between my home computer and the LiveUSB or simply carting around files from one place to the next or one device to another

---

### Post by C.S.Cameron on 2012-05-15
When booting from a pendrive the files stored on it can be found in filesystem/cdrom.


Edit:
If you are looking for the persistence files in casper-rw use the method in post 4 above.

---

### Post by prshah on 2012-05-15
> **HiImTye said:**
> 
1. system - FAT32 (where the liveUSB image is)
2. casper-rw - EXT4 (for persistence)
3. storage - FAT32


Using ext4 for the persistance file (casper-rw) is a BAD idea. ext4 has journalling features, which are good for filesystems. However, the casper-rw file is a loop-mounted file system, again containing a ext4 filesystem.

You are needlessly doubling the journal writes. This does cause unnecessary and excessive wear on flash memory.

Stick with fat32 for casper-rw as well. since casper-rw is a single file, you can even stuff it into your "system" partition (resize as required), the casper-rw file does not need it's own partition.

However, the idea of a "storage" partition is sound.

---

### Post by C.S.Cameron on 2012-05-15
> **prshah said:**
> Using ext4 for the persistance file (casper-rw) is a BAD idea. ext4 has journalling features, which are good for filesystems. However, the casper-rw file is a loop-mounted file system, again containing a ext4 filesystem.

You are needlessly doubling the journal writes. This does cause unnecessary and excessive wear on flash memory.

Stick with fat32 for casper-rw as well. since casper-rw is a single file, you can even stuff it into your "system" partition (resize as required), the casper-rw file does not need it's own partition.

However, the idea of a "storage" partition is sound.

I have never been able to make a casper-rw partition fat 32 and get persistence to work. Ext2 works pretty good though.

A flash drive, with casper-rw partition in ext4, should last years under normal use.

---

