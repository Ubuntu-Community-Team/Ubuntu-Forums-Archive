---
title: "Will my USB drive work in Ubuntu?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by esbo on 2008-07-11
It says PC and Mac on the box, will it work in Ubuntu?
It does not really matter as it is a Wubi instalation so I can back it up
from windows, I suppose?

---

### Post by aktiwers on 2008-07-11
I am pretty sure it will work. I have yet not tried an USB drive not working.
Edit: and I have tested a few(I guess more than 10)

---

### Post by Opensource-student on 2008-07-11
By all means if it should work
I recomend that you format it into fat32 or a windows format if you intend to use it on all 3 (or whatever you choose) 
The usb should work however any software may not.
You shouold be able just to plug, mount and play:):popcorn:

---

### Post by hyper_ch on 2008-07-11
boot from the live CD, plug the usb drive in, see whether it works ;)

---

### Post by esbo on 2008-07-11
> **Opensource-student said:**
> By all means if it should work
I recomend that you format it into fat32 or a windows format if you intend to use it on all 3 (or whatever you choose) 
The usb should work however any software may not.
You shouold be able just to plug, mount and play:):popcorn:

Well it came preformatted, so I guess it is in the windowsXP format NTFS.
I am not sure what file format I will use for my final Ubuntu installation yet,
it is Wubi at the moment so thats NTFS, but I might change to the other 
'proper' installation type. Not decided yet.

---

### Post by esbo on 2008-07-11
> **hyper_ch said:**
> boot from the live CD, plug the usb drive in, see whether it works ;)

I will try it from my Wubi installation when I am feeling brave!!
Worst that can happen is that it won't work (I hope!).

---

### Post by aktiwers on 2008-07-11
Ubuntu cant run on NTFS. 

Remember Wubi actually just creates a virtual hardrive inside your Windows install, then create an EXT3 filesystem on that virtualdrive and installs ubuntu on it.

Thats how it works, so you will be using a "proper" format :)

And yeah it should work fine. but I suggest you test it your self, either with a liveCD or one of the install methods. Let us know if it works

---

### Post by Bucky Ball on 2008-07-11
My external USB drive mounted no questions asked and appeared on the desktop, ready to go. I am running Ubuntu from the hard drive though, not Wubi, and the drive is fat32 format.

Will try SATA next ... and yea, the worst that can happen is it won't see your drive. If that is the case, search for how to mount it because your system may not be set to mount USB automatically or some such. Probably a simple tweak. If it sees a dongle, it will see your drive, put it that way ...

* Update - and as mentioned correctly in the last post, forget NTFS for installing linux. EXT3. That is why I mentioned my external drive is Fat32 format, but it shouldn't make a difference if you just want to read the data ... but then again ...!

---

### Post by Opensource-student on 2008-07-11
> Well it came preformatted, so I guess it is in the windowsXP format NTFS.
I am not sure what file format I will use for my final Ubuntu installation yet,
it is Wubi at the moment so thats NTFS, but I might change to the other 
'proper' installation type. Not decided yet.
Sorry To my knowlege Ubuntu can read most formats.
There is no need to boot w/ a live CD just start up ubuntu normally stick it in and it should auto mount and appear on the desktop. This has happened with the many That I go through.

EDIT: Sorry Scratch that I forgot it was Wubi I dont know how that changes things

Worst Case is ...... Nothing happens and it wont mount (force mount cammand could be useful)
Other Case ..... It works

Have no fear, nothing will go wrong 


I wonder if there is anything that couild go wrong when you stick it into ubuntu (New Thread approching)

---

### Post by Opensource-student on 2008-07-11
I cant believe it !!
Before I can type one reply two more answers appear!!
This is the only forum this could happen on Keep on up the great work!!!

---

### Post by ChameleonDave on 2008-07-11
We're talking about an external hard-drive, right?

If it is FAT, no problem at all.  If it is NTFS, Ubuntu will be able to use it, but there may be the occasional hiccup (if it is plugged into Windows and improperly removed, it will no longer automount in Ubuntu).

At the first opportunity, move the data off the drive and reformat it.  NTFS is only preferable for drives that will be used only on Windows.  If it will be used on various systems, FAT is the best.  If it will be used mainly on Linux, Ext2 or Ext3 may be a good choice (to make Windows able to use such a drive, you have to install Linux drivers on it).

I have two USB pen drives that I use.  One is FAT, and the other is Ext3.

Since this is probably a large drive, which possibly already has multiple partitions, there is nothing stopping you having more than one sort of filesystem on there.

---

### Post by Opensource-student on 2008-07-11
> **ChameleonDave said:**
>   If it will be used mainly on Linux, Ext2 or Ext3 may be a good choice (to make Windows able to use such a drive, you have to install Linux drivers on it).

I didn't know you could get Ext drivers for windows What are they? It would be a great help if you could point me in the right direction.
Thanks!

---

### Post by hyper_ch on 2008-07-11
> **Opensource-student said:**
> I didn't know you could get Ext drivers for windows What are they? It would be a great help if you could point me in the right direction.
Thanks!

[http://www.fs-driver.org](http://www.fs-driver.org) (works also on ext3)

---

### Post by cmulford on 2008-07-11
Hi everyone. I have a Thermaltake Muse A2293 external drive enclosure that I popped a western digital 250GB IDE drive in last night. Before I did this I formatted the whole drive as a single FAT32 partition using gparted.  I did all of this in hopes of transferring videos and music to it so I can share between my Ubuntu box and my xbox 360.  All of the research I did beforehand stated I would not have any problems on either side as long as I formatted using FAT32.  The problem is neither Ubuntu or the 360 sees the drive.  I did plug it into my wifes vista laptop (without installing the windows driver) and it recognized an unknown usb device, so I think it's actually working.  If I plug the drive into the Ubuntu box internally, all is well.

Do I need a special driver even though I have read that I shouldn't?  Could anyone shed some light on what I need to do to get this working - at least on the Linux side?

Thanks,

Skip

---

### Post by ChameleonDave on 2008-07-11
> **cmulford said:**
> 

Do I need a special driver even though I have read that I shouldn't?  Could anyone shed some light on what I need to do to get this working - at least on the Linux side?

So neither Ubuntu, the XBox 360 or Windows Vista can read this drive?  That doesn't give me high hopes!

Putting a hard drive into an external case connected via USB doesn't usually cause any problems, but perhaps your one is different, doing something in some non-standard way.  Does it come with instructions or a CD?

Plug it in and do this on the command line:

```

lsusb
sudo blkid

```

---

### Post by TexZen on 2008-07-12
I'm having a similar problem.  I have an acomdata enclosure that I have formatted as FAT32.  Plugged it in and turned it on, nothing.  Tried an XP machine and it worked fine.

Doing:
```
sudo fdisk -l 
```
returns the following:
```
/dev/sdb1   *           1        1868    15004678+   c  W95 FAT32 (LBA)
```

so I created a mount point and tried to mount:
```
sudo mkdir /mnt/usbdrive
sudo mount -t vfat /dev/sdb1 /mnt/usbdriv
```

gives the following error:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
tried dmesg | tail and got the following result:
[  239.647676] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  239.652648] sd 2:0:0:0: [sdb] 30015216 512-byte hardware sectors (15368 MB)
[  239.657690] sd 2:0:0:0: [sdb] Write Protect is off
[  239.657700] sd 2:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  239.657705] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  239.657717]  sdb: sdb1
[  239.680820] sd 2:0:0:0: [sdb] Attached SCSI disk
[  239.680901] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 4408.548481] FAT: bogus logical sector size 516
[ 4408.548494] VFS: Can't find a valid FAT filesystem on dev sdb1.

This is where I got bogged down.  Any insight into how to get this working would be appreciated.

---

### Post by ChameleonDave on 2008-07-12
> **TexZen said:**
> 
```

[ 4408.548481] FAT: bogus logical sector size 516
[ 4408.548494] VFS: Can't find a valid FAT filesystem on dev sdb1.
```

This is where I got bogged down.  Any insight into how to get this working would be appreciated.
Your problem seems different.  The device is recognised, but Ubuntu reports that the filesystem is corrupt.  It seems to me that it would be best to open up GParted and format the drive (as vfat, ext2 or ext3).  You could use Windows to retrieve any important files from it first.

---

### Post by TexZen on 2008-07-12
> **ChameleonDave said:**
> Your problem seems different.  The device is recognised, but Ubuntu reports that the filesystem is corrupt.  It seems to me that it would be best to open up GParted and format the drive (as vfat, ext2 or ext3).  You could use Windows to retrieve any important files from it first.

I continued to play around a bit with this.  Tried another HD with NTFS and it mounted by it's self no worries.  Took the old drive back to XP to copy off the data and it's no longer working there.  Getting I/O error.  I think I can recover, but is there something that I may have done when I tried it in Ubuntu that would have corrupted the file system?  If so I would like to avoid repeating that mistake.  At any rate, thanks for the info.

---

### Post by ChameleonDave on 2008-07-12
> **TexZen said:**
> is there something that I may have done when I tried it in Ubuntu that would have corrupted the file system?
Well, as far as I know, all you did was plug it in and type "sudo fdisk -l".  That shouldn't have done anything at all to the drive.  Only you know if you did something else!

The corruption may be to do with not safely removing, or it could be physical.

Is the data on there backed up?

---

### Post by TexZen on 2008-07-20
Looks like the partition table was corrupted some how.

Ran the following:
```
 sudo fsck.vfat -vatw /dev/sdb1
```

And got the following result:

```
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
File system has -155 clusters but only space for 264190 FAT entries.

```

In response to your previous question, no the drive was not backed up.  I pulled it out of an old machine that was gathering dust.  The intent was to pull the data and put it on a backup drive.  There is stuff on there that I absolutely have to get.  I've seen a couple of utilities that I can purchase, but if there is a way to work around it, I would like to do so.

Thanks again.

---

### Post by hansdown on 2008-07-20
> **hyper_ch said:**
> [http://www.fs-driver.org](http://www.fs-driver.org) (works also on ext3)

Thanks for that hyper_ch. I know I'm glad You,re here... If only the masses would listen.

---

### Post by Bucky Ball on 2008-07-22
Maybe stick it in a windoze box and remove it correctly, then give it another go in Ubuntu. Could be that; strange things happen when disks or drives aren't unmounted in windoze correctly. I couldn't access my windows drive from Ubuntu one day but windoze hadn't been closed properly. Went back to windoze, shut down correcly and all fine.

---

