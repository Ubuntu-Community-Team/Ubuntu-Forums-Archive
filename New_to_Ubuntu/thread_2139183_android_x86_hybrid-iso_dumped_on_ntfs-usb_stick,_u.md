---
title: "android x86 hybrid-iso dumped on ntfs-usb stick, unable to remove image / files"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by rootfairy on 2013-04-26
hi guys,

today something very stupid happened to me. i bought a new usb stick, 32 gb. i then downloaded and dumped the hybrid iso on the usb-stick's ntfs file system. when i got onto the stick, it only showed cryptic stuff. i dded it on sdb & sdb1, e.g.:[SIZE=3][SIZE=3][SIZE=3]

[/SIZE][/SIZE][/SIZE]```
dd if=android-x86-4.2-20130228.iso of=/dev/sdb
dd if=android-x86-4.2-20130228.iso of=/dev/sdb1
```[SIZE=3][SIZE=3][SIZE=3]
[/SIZE][/SIZE][/SIZE]
ok, i dont know what happened next. i formatted the stick or something or deleted the partition. i can create a new partition though and it shows correct size.the weird thing is that, the usb-stick is not becoming bootable.
[SIZE=3][SIZE=3] 
[/SIZE][/SIZE]> 

Released FileSince the jb-x86 branch we try to create a universal image for most x86 platforms. The plan is still in an early stage. Please report bugs to the android-x86 forum with detailed specs of your machine and error logs.android-x86-4.2-20130228.iso sha1sum: d9843bbccf29d64ae0cb4d6b30d1fad7e29f6cddThe iso file ishybrid format. That means you can dump the iso into a usb drive and get a bootable usb stick, like$ dd if=android-x86-4.2-20130228.iso of=/dev/sdXwhere /dev/sdX is the device name of your usb drive.[SIZE=3][SIZE=3]
[/SIZE][/SIZE]
the other very weird thing is that, although i deleted and created a few new partitions and filesystems already (ntfs, ext4, fat32), the usb-stick is still named "Android-x86 LiveCD", but it doesnt show the files BUT when i remove the filesystem from the usb-stick it shows the files, but i cant remove them, coz the filesystem is only read. when the usb-stick has NO filesystem BUT ONLY a partition-table set, it shows the image:

```

biatch@biatchXFCE:/media/biatch/Android-x86 LiveCD$ ls
initrd.img  install.img  isolinux  kernel  ramdisk.img  system.sfs  TRANS.TBL
biatch@biatchXFCE:/media/biatch/Android-x86 LiveCD$ rm -rf *.*
rm: cannot remove `initrd.img': Read-only file system
rm: cannot remove `install.img': Read-only file system
rm: cannot remove `ramdisk.img': Read-only file system
rm: cannot remove `system.sfs': Read-only file system
rm: cannot remove `TRANS.TBL': Read-only file system

```

gparted tells me "recursive partition".

so how can i remove these files and restore the sanity of my usb-stick? this is so weird!

related: 

[https://bbs.archlinux.org/viewtopic.php?id=149001](https://bbs.archlinux.org/viewtopic.php?id=149001)

---

### Post by rootfairy on 2013-04-26
i just ran it over with unetbootin. what did i do now? :D it seems to work, though i enabled usb-legacy in bios. whats going on here? are the files from dd still there or not? i dont understand this.

---

### Post by rootfairy on 2013-04-26
after i ran it over with unetbootin and the same image i think the stick was normal again. still im trying to kill it at the moment with

```

dd if=/dev/zero of=/dev/sda

```

though im not really sure that is what i want, but i guess so.

related topic:
[http://www.linuxquestions.org/questions/linux-newbie-8/using-dd-to-zero-the-mbr-query-606489/](http://www.linuxquestions.org/questions/linux-newbie-8/using-dd-to-zero-the-mbr-query-606489/)

[URL="http://ubuntuforums.org/archive/index.php/t-1912501.html"]http://ubuntuforums.org/archive/index.php/t-1912501.html

[/URL][https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

[http://askubuntu.com/questions/17640/how-can-i-securely-erase-a-hard-drive](http://askubuntu.com/questions/17640/how-can-i-securely-erase-a-hard-drive)

---

### Post by oldfred on 2013-04-26
Is Android a hybrid ISO? Only those designed to be dd'd to a flash work.

 The daily ISOs for the Ubuntu Oneiric 11.10 development cycle (and all official Ubuntu CD releases going forward)
for i386 and x86_64 platforms will be now spun as hybrid ISOs. Or you can use dd.
[http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid](http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid)

You dd to an entire flash drive, but that only writes the size of the ISO or about 700MB. But that would include the partition table. When you did it to a partition you had a full install inside a partition, so I would expect it to be confused as a drive is not a partition.

---

### Post by rootfairy on 2013-04-26
yes, the latest release is a hybrid iso. you can read that here: [http://www.android-x86.org/releases/build-20130228](http://www.android-x86.org/releases/build-20130228) the thing is after i formatted and repartioned the usb-stick multiple times, the hybrid-iso and its files i pushed with dd would still show up on the usb-stick _if_ i removed all partitions _and_ file systems and then set _only_ a partition (e.g. partition _without_ filesystem) as if i they were never deleted or anything. thats what was making me wonder. so there would still be around ~230mb files on the usb-stick even after i partitioned and formatted it multiple times. and that was weird. and thats why im dding it now with zero. i suppose the dd command i issued will also erase the mbr? like pointed out in this thread, who is only trying to erase the mbr only [http://www.linuxquestions.org/questions/linux-newbie-8/using-dd-to-zero-the-mbr-query-606489/](http://www.linuxquestions.org/questions/linux-newbie-8/using-dd-to-zero-the-mbr-query-606489/).

related:

[URL="http://ubuntuforums.org/showthread.php?t=2084514"]http://ubuntuforums.org/showthread.php?t=2084514
[/URL]
and this is whats giving me the chills:
> 
ubuntuforums.org/showthread.php?t=2139183I don't think it is that simple. USB and SD flash disks use a different cylinders, heads, sectors count scheme than normal hard disks. You need to find an identical, working USB flash drive and determine the CHS count. Then use a command line tool to format it with the correct CHS count. Works the same with SD cards, although it's easier to put it in a digital camera and format it with the camera. Windows may format a USB stick correctly.As a general rule: Don't use gparted or parted or fdisk to format SD cards and USB thumb drives. They will mess them up. It is correctable, but you have to find the correct CHS count from an identical drive. 


---

### Post by oldfred on 2013-04-26
All my flash drives are partitioned & formatted with gparted. Never had an issue.

Last couple of larger flash drives, I even used gpt instead of MBR(msdos) and put full installs of Ubuntu on them without any issue.

Flash drives do use different CHS values, but drives do not use CHS anymore but LBA. Testdisk still shows CHS if interested. When hard drives went over 8GB, they converted to LBA or over 15 years ago. Back then I did have to go into BIOS and manually set CHS values for BIOS to see hard drive.

---

### Post by rootfairy on 2013-04-26
so it seems my thread is solved after i dd`ed this stick? and i can be rest assured everything is fine, nice and clean so as to allowing me to sleep well? :)

related:

[http://ubuntuforums.org/archive/index.php/t-1752402.html](http://ubuntuforums.org/archive/index.php/t-1752402.html)

---

### Post by oldfred on 2013-04-26
All drives fail and flash drives are not yet as reliable as other drives, but some have had good sucess.

If you really want to sleep at night do not read above sentence. :)
Or have good backups.

---

### Post by squakie on 2013-04-26
I love that post oldfred! ;) ;)

---

### Post by rootfairy on 2013-04-26
[SOLVED] xD i hope these 3 liters of beer can make me sleep well xD btw :geektalk: im running android x86 on a samsung slate 7 pc, and ubuntu 12.10, and maybe 13.04 and of course ubuntu tablet and for all that im using an usb keyboard from an imac g3 omg... this is so cool, btw the stick is fine, im just tossing it hard

*wow this 13.04 is running so damn good in this tablet i must be dreaming

---

