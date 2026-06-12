---
title: "Can't find FAT32 disk for shared space"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by rayvuh on 2008-07-31
I just dual booted Ubuntu with Windows XP.  Windows already installed and I used the Ubuntu CD to manually partition my hard drive.  I resized the Windows partition, created a partition for Ubuntu, created a Swap partition and a FAT32 partition for sharing files between Windows and Ubuntu.  Everything went well, I can see the FAT32 disk in Windows but in Ubuntu I don't see it anywhere.  What am I not doing right or what do I have to do to be able to access it in Ubuntu.  I will post my fdisk results.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ea99ea9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        8511    29294527+  83  Linux
/dev/sda3            8512        9729     9783585    5  Extended
/dev/sda5            8512        8635      995998+  82  Linux swap / Solaris
/dev/sda6            8636        9729     8787523+   b  W95 FAT32

Any help would be appreciated as I'm new to Linux.

---

### Post by lordadi on 2008-07-31
Hi,

Right click on a panel and select add to panel then select disk mounter. Drag and drop it somewhere on your panel. Then click on one of the 2 disks you'll see there and see if it says FAT32 or something to that effect. If it does then left click on it and select mount. Else do it to the other disk. After that, the disk should show up on your desktop. Double click it and away you go!

If you're (after that) looking to have the disk be automounted on boot, then you will need to edit your fstab. However, I do not know nearly enough about that and you need somebody else's help for that.

Cheers,



Lordadi.

---

### Post by sstvinc2 on 2008-07-31
I'm pretty sure that Linux doesn't really enjoy handling FAT32 drives.  What I do is make the partition for sharing files between the OSes ext3 and install EXT2IFS for Windows [http://www.fs-driver.org/]("http://www.fs-driver.org/"), which lets Windows see otherwise-invisible ext2/3 drives.  If you want to go this route, I'd use gparted in Ubuntu to reformat the FAT drive to ext3. ```
sudo gparted
```

gparted should let you choose the mount point for this partition as well.

Oh, and obviously, back up any files you have on the FAT drive first.

---

### Post by annda on 2008-07-31
actually, fat drives or partitions are OK for shared storage. 

if you don't like terminal commands, running gparted (Partition Editor in System>Administration), like sstvinc2 suggested, is a fairly easy way to add a mountpoint for a partition (/media/**shared** - the last bit is a name you can freely choose). adding a disklabel, e.g. Shared is a also a good idea, while you're at it. It will be easier to find the partition in Places.

---

### Post by sstvinc2 on 2008-07-31
I didn't know that about FAT drives.  I've always just been told to steer clear of them in Linux.

---

### Post by annda on 2008-07-31
> **sstvinc2 said:**
> I didn't know that about FAT drives.  I've always just been told to steer clear of them in Linux.

a little off-topic, but FAT is only bad for "real" linux files - mostly because it does not understand files' permissions and ownership. if you just want to share some photos and mp3s between systems, FAT is all right. read and write access are supported by windows and linux, probably even picky macs.

---

### Post by lavinog on 2008-07-31
ext2ifs is my favorite option, but why not just make a ntfs partition?
FAT32 has too many issues like file size limits, permissions, recoverability

---

### Post by YaroMan86 on 2008-07-31
> **lavinog said:**
> ext2ifs is my favorite option, but why not just make a ntfs partition?
FAT32 has too many issues like file size limits, permissions, recoverability

The ext2ifs driver is what I do for shared partitions. Linux partitions are just so much better than Windows partitions.

---

### Post by ajgreeny on 2008-07-31
However I have heard from some that the ext2ifs driver in windows can sometimes corrupt an ext3 partition.  maybe the driver has grown up now and doesn't do that anymore.  I have never used it myself, but am just passing on what I've read.

---

### Post by lavinog on 2008-07-31
> **ajgreeny said:**
> However I have heard from some that the ext2ifs driver in windows can sometimes corrupt an ext3 partition.  maybe the driver has grown up now and doesn't do that anymore.  I have never used it myself, but am just passing on what I've read.

I haven't had any problems with it. Since ext3 has an open specification I would gather that the ext2ifs driver would better support ext3 than linux supports the ntfs file system.
I have far less problems with ext3 and ntfs than FAT

---

### Post by sstvinc2 on 2008-07-31
> **ajgreeny said:**
> However I have heard from some that the ext2ifs driver in windows can sometimes corrupt an ext3 partition.  maybe the driver has grown up now and doesn't do that anymore.  I have never used it myself, but am just passing on what I've read.

I think that's true, to a certain extent.  Ext3 is a journaling filesystem, which means that a smooth shutdown is important to maintain proper disk state (which is why Ubuntu does disk checks if you do just yank the power).  And, as we all know, sometimes Windows just can't be shut down nicely.  That being said, I've never had any problems with it.

I have however had an issue with an external NTFS drive, where if I don't do a clean shutdown with the drive mounted in Windows, Ubuntu can't mount it until I go back into Windows and remount and properly unmount the drive.

I guess the moral of my very boring story is that none of these solutions is perfect, but I think pretty much any of them work extremely well.

---

