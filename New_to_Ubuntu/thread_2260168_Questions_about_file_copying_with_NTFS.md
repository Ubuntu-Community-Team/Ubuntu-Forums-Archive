---
title: "Questions about file copying with NTFS"
date: 2015-01-09
forum: New to Ubuntu
---

### Post by DBDigital on 2015-01-09
I am new to Ubuntu and I am looking to file copy one NTFS windows install to another HD (also NTFS)  of the same size using the Live CD with the installed file manager (Nautilus I think it is called?).  The reason being I know there is possible bad block (per S.M.A.R.T) and I want to find out which file it pertains to.  Nothing is corrupted and the install is working fine.    If I use Nautilus to file copy the drive, will it copy everything?  Will it preserve all the security settings etc and the second drive actually boot (provided I have the partition already set to bootable of course and other aspects set).  Or will data be lost in the transfer?  Anyone ever try this?  Like I said I am really new so bear with me.  Not to computers or hardware, just Linux/Ubuntu :)

---

### Post by Mark Phelps on 2015-01-09
> Will it preserve all the security settings etc 

Probably not.  Nautilus understands Linux filesystems, but NTFS is a Windows filesystem -- the security settings of the different filesystems are very different from each other.  It's unlikely that Nautilus will be able to preserve those.

If you really want to "migrate" a Windows install to another drive (same size or larger), you would do better using a Windows filesystem utility.  Minitool Partition Wizard Boot CD will do that -- migrate entire partitions from one drive to another.  You could also do the same by doing an image backup and a restore.  That can be done using Macrium Reflect.

---

### Post by Yellow Pasque on 2015-01-10
Probably the closest thing under Linux to do what you want is ntfsclone and ntfscmp commands. I don't have any personal experience with them, so this is the best I can recommend.
```
sudo apt-get install ntfs-3g
man ntfsclone
man ntfscmp
```

---

### Post by DBDigital on 2015-01-10
First thank you for replying.  I do know about imaging and cloning.  I have done it several times with different drives.  As I said there is a bad block on this disk and I am trying to determine what file is on this block.  File copying is the only way I know of to find this out.  Granted to just learn which file contains the block does not require copying of security descriptors etc, but I was wondering if that was possible.  Also while I know Linux does not use NTFS by natively, I thought that Ubuntu had a tool/driver by default installed to make full use of NTFS file system?  I think I read the ntfs-3g is the driver (and mentioned above) in question?  Isn't that already installed?  I read several tutorials mentioning how to copy/recover files from NTFS drives using Ubuntu Live.  It was never mentioned that ntfs-3g had to be installed/grabbed?  Like I said while my main goal is to just find out what file has been corrupted, and if it has, the block is marked as PENDING in S.M.A.R.T.  But I was wondering if a full file copy of the entire drive was possible making a working bootable drive or if image was the only way.  In my case I have used Clonezilla (among other tools) in the past so I know how that works.  Just researching all the options and see what is possible.  ntfsclone I have heard of, ntfscmp I will check into thank you Temüjin.

---

### Post by coffeecat on 2015-01-10
You cannot copy a Windows installation from one HD to another and have a working copy by means of a file copy - not even by using Windows for the file copy. You need to clone as the previous posters have said. If you wish to clone a Windows installation, it is best to use a Windows cloning tool. I'll give a +1 to Mark Phelps' suggestion of Macrium Reflect for which there is a free edition. 

Ubuntu can read-write NTFS out of the box with the ntfs-3g driver which is installed by default. That is not the issue here. Recovering files from a Windows system is one thing for which Ubuntu can be used. If you want to end up with a working and bootable copy of your Windows system, that is quite a different matter for which you need to use a cloning tool.

---

### Post by DBDigital on 2015-01-10
Of course one cannot under windows, but I was wondering if it was possible under linux/ubuntu.  As I said, I am very familiar with cloning, although no Macrium Reflect.  I have used clonezilla several times.  Before that Norton Ghost (long long ago lol).    Anyway thank you for the assistance and confirm that I can do file copies out of the box.  This will at least let me track down where the bad block (If it is bad) is with relative ease.

---

### Post by efflandt on 2015-01-10
If you have a Western Digital or Seagate/Maxtor drive somewhere on your system (even if external USB) you could use a free version of Acronis from wdc.com or seagate.com respectively. Instead of imagining sector by sector it has another mode to image file by file, so you are not trying to copy bad sectors or lock out what were bad sectors on the previous drive and also makes smaller image file if imaging instead of cloning directly.

I used Acronis when the Linux partition at the far end of my drive began failing more frequently (automatically remounting read-only) even after locking out badblocks more than once. But I also needed more room for Linux since getting into Linux Steam, so I used Windows' own Disk Management to shrink its partition, cloned Windows mbr (I normally boot from grub on sdb) and Windows partitions to a new drive using eSATA drive caddie, swapped drives, fresh installed Ubuntu, then copied home from old drive to new. Only a few Steam game files were corrupted due to the failing drive, but verifying integrity of game cache in Steam replaced those.

I also used Acronis to image a failing Windows laptop drive. It was a replacement PATA (not SATA) drive that failed under warranty. So I put the drive in a USB enclosure, ran chkdsk /f on it to make sure files were intact, then imaged it to a file using file by file instead of sector by sector. Then I wrote the image to the warranty replacement drive, and the new drive booted and ran fine in the laptop.

I tried using clonezilla on a failing drive once, but it was only capable of imaging or cloning sector by sector and would grind to a halt when it got to a sector it could not read.

---

