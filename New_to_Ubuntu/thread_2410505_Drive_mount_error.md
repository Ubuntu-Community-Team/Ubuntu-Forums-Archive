---
title: "Drive mount error"
date: 2019-01-16
forum: New to Ubuntu
---

### Post by clement-2000 on 2019-01-16
Hello, 
I'm totally new new to Ubuntu (moving from Windows 7), so sorry if this question might seem a bit stupid, 
So my problem, is that when I plug USB drive, I can't access the content on it. In fact I cant't even mount any partition of my drives (previously made with Windows) with that cool Linux kind of cmd (yes, I know, it's called the terminal). 
When I do "sudo fdisk -l" it displays all the disks, everyting is right. 
But then when I want to mount the drive using "sudo mount /dev/sdc /mnt", it returns : "mount: /mnt : wrong fs type, bad option, bad superblock on /dev/sdc, missing codepage or helper program, or other error."

It's the same for all drives, 
I don't know what I'm doing wrong. 

Thank you in advance for your help, 
Clement.

---

### Post by TheFu on 2019-01-16
Most storage devices have partitions.  There is a heirarchy for storage devices in all Unix systems.
On Linux, sda is the entire disk.  sda1 is the first primary partition.  Mounts are 99.999% on the partition, not the whole disk.  

Assuming sdc is correct, then **sudo mount /dev/sdc1 /mnt** is probably the command you want to try.

The output from fdisk -l isn't perfectly clear since only the partition numbers are shown in the table, but the disk device is shown above. 

This all assumes you are using simple partitions, not encryption and not LVM or other volume management tools. With those, we have to mount the special devices, not a disk+partition-number.

Flexible. Linux is very flexible.

---

### Post by clement-2000 on 2019-01-17
In fact, 
I checked with Windows and the USB drive was just bad and needed to be reformatted (and I did... with Windows :(). And now it mounts automatically !
And what does /mnt of mount does ?  
But, if I want to format my drive , how am I supposed to do this (with Linux of course), considering that it needs to be formatted because it doesn't work ?
And to mount CDs ?
Thank you !

---

### Post by oldos2er on 2019-01-17
Gparted is the GUI tool of choice for all things partition related. You can install it with ```
sudo apt install gparted  
```

---

### Post by clement-2000 on 2019-01-17
WOW ! This tool is just amazing ! Way better than the Windows one !
Thank you a lot for your help !
I think I'm quickly gonna go from like "Windows is the best OS ever, and Linux eh... no" to "Windows is the worst OS ever, and Linux : nothing better" !

And now how do I do for CDs and DVDs ?

---

### Post by TheFu on 2019-01-17
> **clement-2000 said:**
> In fact, 
I checked with Windows and the USB drive was just bad and needed to be reformatted (and I did... with Windows :(). And now it mounts automatically !

To partition a disk on Linux, you can use parted, fdisk, gparted tools.
To format a partition on Linux, you can use gparted or mkfs.
gparted is a GUI program used on desktop Linux.
mkfs and fdisk are CLI/shell programs used on servers or remote systems or desktops.

There are other GUI tools, but most are known to have issues of one sort or another.  gparted works well and is easy to use.
All these commands require elevated privileges, so using **sudo -H gparted** is the safe way.

> **clement-2000 said:**
> And what does /mnt of mount does ? 
From the manpage for mount ... access this by **man mount**
```
SYNOPSIS
       mount [-l|-h|-V]

       mount -a [-fFnrsvw] [-t fstype] [-O optlist]

       mount [-fnrsvw] [-o options] device|dir

       mount [-fnrsvw] [-t fstype] [-o options] device dir
```
The /mnt is in the last position, so it is the directory where the partition/device is mounted.  After mounting using /mnt as the last parameter, the storage would be available in /mnt on the file system.  Any directory can be a mount point.  It can be /mnt or /home/thefu/some/where/deep/inside/the/directory/system    but the directory must exist.  We can never mount to a directory that doesn't already exist.  Don't worry. You will try to mount to a non-existent directory. That is something we all do.  Also, if you mount onto a directory that already has files and subdirectories inside, what happens?  Try it.

The command to unmount is **umount**, without the 'n'.  No process can be using the storage or the umount will fail. **man umount** has more information.

Normally, only root can mount and umount.  This is because with the mount command, a person can completely replace the OS and gain access to anything on the system.  The point to mount is the total power to own a system.  

> **clement-2000 said:**
>  
But, if I want to format my drive , how am I supposed to do this (with Linux of course), considering that it needs to be formatted because it doesn't work ?
Formatting isn't something do all that often.  Generally, we do it once.  In general, using ext4 as the file system is the best choice, unless you have a specific reason to select something else.  Unlike Windows, there are many different file systems, each with a different purpose.  Further, the underlying organization can be much more flexible if you use an advanced solution like LVM2, ZFS, or Btrfs.  I use LVM because it has been around a very long time. I put ext4 file systems onto the LVM (Logical Volume Manager).

When just starting out, simple is probably best, but know that there are lots of flexible options at the price of added complexity.

> **clement-2000 said:**
> 
And to mount CDs ?
Thank you !

CDs and DVDs can have different formats.  I don't know how to mount an audio CD, but for data CDs and DVDs, you just mount them using the same mount command with a different device.  Might need to specify the file system used, but usually not. You can see the device in the /dev/ directory.  Look for /dev/cdrom0, /dev/dvd0, something like that.  On my system is was /dev/sr0 - know idea where that comes from.  Be careful with all /dev/* stuff.  That is a direct path to all devices on the system .... so all the HDDs, SSDS, audio hardware, video capture stuff, headphones, monitors, video cards, keyboard, mice, and the different ways we access them are all there.  

**Everything on Unix is either a file or a process.**   <---- learn that.  Files are files.  Directories are files.  Keyboards are files. The entire HDD is a file. A specific partition on the HDD is a file.  Everything is  a file which has permissions.  Learn about Unix permissions to avoid frustration. Whatever you do, don't use sudo when it isn't needed.  Bad things can happen.  While it is possible to use sudo with some GUI programs, in general, it is not safe and must be avoided.  Anyways, enough soap boxing.

OTOH, you can grab any data from any device that can be seen, including audio CDs.  This is one of the reasons Unix systems are so powerful.  Once you pull the data from the media, then you can use other tools to deal with any issues preventing it from being read.  Of course, there are audio programs that know how to read an audio CD directly.  I haven't used those since the 1990s, so I'm out of the loop on those.  Sorry.

Nobody can know everything about Linux.  I've been learning for 25+ yrs now, but figure I know about 10%.

---

### Post by clement-2000 on 2019-01-22
Hi,
Thank you very much for your help !
Now it seams like I really love Linux !

---

