---
title: "Partitions Corrupted .. Urgent Help needed !"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Dark Star on 2008-05-25
Hi
I recently installed Ubuntu 8.04 dual boot with Mandriva 2008.1 .. Now Ubuntu has some problem with my system so I formatted the HDD partition of the same using Mandriva inbuilt Disk Manager in Mandriva Control Center.. After I formattedi mounted it at /media/hd1 .. I restated so that everything work fine.. Now it detects only one of the NTFS partition and Filesystem, when I open Mandriva Drive Manager it says the following error..

[IMG]http://www.imgx.org/files/17397_r0wxn/Desktop2.png[/IMG]  [IMG]http://www.imgx.org/files/17398_zu8bx/Desktop3.png[/IMG]


Now I has some valuable data . how can I recover that ? Any help would be appreciated !

**fdisk -l**

```

        [root@localhost shashwat]# fdisk -l
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dd6c6bd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/hda2            3188        8287    40965687    f  W95 Ext'd (LBA)
/dev/hda3            8288        9607    10602900   83  Linux
/dev/hda4            9608        9729      979965   82  Linux swap / Solaris
/dev/hda5   ?        3597      122978   958924038+  70  DiskSecure Multi-Boot 
```
**/etc/fstab**

   ```

# Entry for /dev/hda3 :
UUID=3235544d-f8bf-459d-966b-de3e541f3d12 / ext3 defaults 1 1
# Entry for /dev/hda1 :
UUID=CCE44E48E44E354C /media/hd ntfs-3g defaults 0 0
# Entry for /dev/hda7 :
UUID=0873F1E02F80CB85 /media/hd1 ntfs-3g defaults 0 0
# Entry for /dev/hda5 :
UUID=15BEB5322F467B42 /media/hd2 ntfs-3g defaults 0 0
# Entry for /dev/hda6 :
UUID=0BCF489D1C56ABAA /media/hd3 ntfs-3g defaults 0 0
none /proc proc defaults 0 0
# Entry for /dev/hda4 :
UUID=8bd4d2de-165a-46d0-a3da-85e9db62a11c swap swap defaults 0 0
```

Also how do I mount NTFS partitions automatically in Ubuntu. It mounts my partitions as disk .. Not as partitions :@

Regards

Somebody help me .. Cause if I loose the data my sis will kill me

---

### Post by Dark Star on 2008-05-25
C'mon guys help me :(

---

### Post by Raccoon1400 on 2008-05-25
> Now Ubuntu has some problem with my system so I formatted the HDD partition of the same

What partition did you format? The ubuntu one?

---

### Post by phoenix_abhi on 2008-05-25
This is not help. But I had dual boot of Ubuntu and Vista. I tired a triple boot with Madriva 2008, it totally made my system non ops. Now only keeping Ubuntu and Vista only. May be with a new PC I will try Fedora and Mandriva. Sorry

---

### Post by deepclutch on 2008-05-25
again what is the output of "fdisk -l" ?
do u have 2 harddisks?

also,install this utility called "testdisk" .it will come handy.
dont delete the partition in despair and panic.

I am completely clueless reg something with winblows :(
still,look what I found:
> 
**[COLOR=#ffb099]DISKSECURE[/COLOR] &#8212; Protects basic disk files from Viruses.**
 unrated
 [added 1998-10-25]
 *Reviewed by Howard Schwartz (10-06-98)*
DISKSECURE: There are three critical files (well, not actually files) at the beginning of your hard disk that perhaps up to 1/3 of the viruses in the wild like to hide in, or like to attack and corrupt: 
[LIST=1]
[*]The "Master Boot Record" contains basic software that your computer executes every time you start up and boot your computer. If they hide here, "stealth" and/or "boot sector" viruses can get executed each time you start your computer, and then hide in ram.
[*]The "Partition Table" describes how many partitions you have on your disk, what type they are, and where they are.
[*]The "File Allocation Table" probably should be called the directory allocation table. It describes where to find all the directories on each partition, and, where to go on the disk, to find out which files are in each directory.
[/LIST]
 By corrupting or destroying any one of these three items, a virus can make a disk completely unusable. DISKSECURE protects items #1 and #2 from viruses: 
[LIST]
[*]Moving the Partition Table to a secret hiding place and replacing it with its own code.
[*]Preventing **any** program from writing data to these parts of the disk.
[*]Saving a good copy of #1 and #2 offline (e.g., on a floppy), so you can restore them, if the ones on the hard disk are deleted or corrupted.
[*]Preventing any accidental booting of your computer from a floppy disk. Most viruses still enter a computer from a floppy disk, or other removable media.
[*]If desired, requiring a password before your computer will boot to and access your hard disk.
[/LIST]
 DISKSECURE also includes a program that bypasses its defenses if you want a program to be able to access your hard disk's beginning sectors directly. DISKSECURE cannot protect your File Allocation Table in this way because it is constantly being written to and changed as new files are created, old ones deleted, etc. To protect this critical table, use a utility like [STF.COM]("http://short.stop.home.att.net/freesoft/disk1.htm#stbfp") (save the FAT) to back it up each time you start your computer.

[http://short.stop.home.att.net/freesoft/antivir.htm#disksecure](http://short.stop.home.att.net/freesoft/antivir.htm#disksecure)

So,it will be some small file crapped by winblows? or freedos :?

---

### Post by Dark Star on 2008-05-25
> **Raccoon1400 said:**
> What partition did you format? The ubuntu one?

Yep I did the same..

I have one HDD with no WIndows !

---

### Post by konungursvia on 2008-05-25
Can you boot into Mandriva at all, or into any OS? If so, google "gparted" and download the ISO or disk image, then burn the disk image to a CD, and boot into that CD, and try using gparted to do the partitioning again. It is better than the built-in Mandriva partition manager.

---

### Post by Dark Star on 2008-05-25
Yes .. .. I said 2 partitions are getting detected . i.e My music 26 Gb and The Mandriva / partitions.. 

About Gparted ..I tried to see if I can reformat the defective one to fix it.. But Gparted doesn't list any of 'em

[[IMG]http://www.imgx.org/pthumbs/large/8156/Screenshot.jpg[/IMG]]("http://www.imgx.org/public/view/full/8156")

---

### Post by Raccoon1400 on 2008-05-25
What partition is the data you want to save on?

---

### Post by Dark Star on 2008-05-25
/dev/hda1

---

