---
title: "Need help with dual boot Ubuntu/XP install"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Aldyrin on 2008-11-02
Last night I tried to install Ubuntu on my system, and when I restarted after the install, I got "Error 22" when Grub was loading.  

After a lot of digging around, I used the super grub disk to regain access to my xp installation.  This is my first time messing with boot loader stuff, so I wasn't sure exactly what all the options in the SGD signified.

Here's my current setup:
-Two 35 gig SATA drives in RAID 0 (This is where my XP installation is at.  The motherboard has on-board sata raid controller that I am using.)
-One 180 gig disk for general storage
-One 700 gig disk for more general storage.  Using the Live CD install, I resized this partition to leave 100 gigs for Ununtu.

I was planning on putting the ubuntu install on the RAID 0 drives, but I didn't see a way to change the hard drive being installed to AND be able to resize the partition.  Also, it looked like while I was using the Live CD, my RAID 0 was being seen as two separate drives, but I might be mistaken.

Any suggestions as to how I should proceed?  

Thanks!

---

### Post by caljohnsmith on 2008-11-02
Your RAID array is most likely the problem that Grub didn't quite get installed properly. How about booting your Live CD, open a terminal (applications > accessories > terminal), and post:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by dracayr on 2008-11-02
if you have any external harddisks plugged in, unplug them and try again. Make sure your ubuntu disk is primary master

dracayr

---

### Post by Aldyrin on 2008-11-02
Well, here's the text from the commands you wanted me to run.  Just so you aren't confused, I tried installing ubuntu again after I got the Grub error, hence the two sets of partitions.

ubuntu@ubuntu:~$ sudo fdisk -lu
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x25e0 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdc35dc35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30716279    15358108+   7  HPFS/NTFS
/dev/sda2        30716280   144584999    56934360    f  W95 Ext'd (LBA)
/dev/sda5   ?  3439628501   457337645   656338220+  59  Unknown

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x64e7383e

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xefa5e7b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1044257129   522128533+   7  HPFS/NTFS
/dev/sdc2      1044257130  1465144064   210443467+   5  Extended
/dev/sdc5      1254596238  1456501094   100952428+  83  Linux
/dev/sdc6      1456501158  1465144064     4321453+  82  Linux swap / Solaris
/dev/sdc7      1044257256  1245953204   100847974+  83  Linux
/dev/sdc8      1245953268  1254596174     4321453+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6609cb8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   390716864   195358401    7  HPFS/NTFS


---------------------------------------------------------------

ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
ubuntu@ubuntu:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
ubuntu@ubuntu:~$ sudo dd if=/dev/sdd count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system

----------------------------------------------------------------

ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 8206                                   
0000002

I would like to install ubuntu on 10-15 gigs on the raid 0 drive (where my windows installation is at, but I didn't see this option in the install.

Thanks for the help.

---

### Post by Aldyrin on 2008-11-02
Did some digging around, and read that Ubuntu doesn't support fake RAID, which sounds like what I am using for my windows install.  

If I can't put ubuntu on the RAID0 drives, that is fine.  I'd still like to be able to boot windows, though.

Edit: Oh, and I don't have any external drives.  Not sure which is the primary master.  I'll check.

Edit: Ok, the 750 gig drive is the primary master and the 200 gig drive is the secondary master.  

In addition, the hard drive boot priority is the raid controller, the 750 gig, and the 200 gig.

---

### Post by caljohnsmith on 2008-11-02
As I expected, Grub was installed to the MBR (Master Boot Record) of sda, your Windows drive in the RAID array. Can you set your BIOS to boot the Ubuntu sdc drive first on start up? If so, you could install Grub to the MBR of sdc, and you should be able to boot it just fine. 

So if you can set your BIOS to boot the sdc drive, I would recommend first restoring the Windows MBR to the sda drive so you can boot directly into Windows when you boot that drive. If you have your Windows Install CD, just go to the "recovery console" and run:
```
fixmbr
```
Or if you don't have a Windows Install CD, you can download and use the [Super Grub Disk]("http://www.supergrubdisk.org") instead to do the same thing.

Let me know if you can change your BIOS to boot the sdc drive on start up, and I can give you further instructions of how to install Grub to its MBR and take care of other details necessary to boot it.

---

### Post by Aldyrin on 2008-11-02
I already fixed the MBR on the windows drive using the super grub disk.  

And I can change the 750 gig drive (the one with the ubuntu installs) to boot before the raid controller.  

I'm not sure how to put grub on the 750 gig drive though.

Also, is there an easy way to remove one of the two ubuntu installs?  I only really need one.

---

### Post by caljohnsmith on 2008-11-02
You can use Ubuntu's partition editor gparted from the Live CD to delete one of your two Ubuntu partitions. Also I would recommend deleting one of your swap partitions since you only need one swap partition anyway. Just go to System > Admin > Partition Editor in the Live CD, select the sdc drive, right-click the two swap partitions, and select "swapoff" to make sure the Live CD doesn't use either of them. Then you can delete a Ubuntu partition and a swap partitions; after that you could create a data partition to use that space.

---

### Post by Aldyrin on 2008-11-02
Got it.  I assume it doesn't make any difference which swap partition I delete?

Also, I'm a little unclear on how to get GRUB installed on the 750 gig drive, as you mentioned in your previous post.

Thanks for the help!

---

### Post by caljohnsmith on 2008-11-02
OK, to install Grub to your sdc drive, do the following:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd3,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of those commands.

The next issue is that none of your partitions on the sdc drive are marked as bootable, and some BIOSes will refuse to boot a drive that doesn't have one partition marked as bootable; to correct that do:
```
sudo fdisk /dev/sdc
```
Enter "a", "1" for the partition, and then "w" to write the change to sdc. Go ahead and reboot, set your BIOS to boot the sdc drive, and you should get the Grub menu on start up; however, choosing Ubuntu in the Grub menu will most likely result in a Grub error. So to boot Ubuntu, select the first Ubuntu entry in the Grub menu, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. That should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. 

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to use whichever (hd0,Y) worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set, at least about booting Ubuntu. If you run into any problems, please post:
```
sudo fdisk -lu
```
Or let me know how it goes. :)

---

### Post by Aldyrin on 2008-11-02
Should I have Windows as an option in GRUB if I follow those commands?

---

### Post by caljohnsmith on 2008-11-02
> **Aldyrin said:**
> Should I have Windows as an option in GRUB if I follow those commands?
Not yet, those commands will you allow to boot Ubuntu from the Ubuntu drive, and once you get that working, I'll help you add a Grub entry to boot Windows. Just see if you can get as far as my last post and we can work from there.

---

### Post by Aldyrin on 2008-11-02
Alright!  I'm in business.  Didn't have to tweak the menu.lst file either.

Much thanks!

So I assume I have to edit the menu.lst now.

Here's my latest fdisk -lu

----------------

aldyrin@Ra:~$ sudo fdisk -lu
[sudo] password for aldyrin: 
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x25e0 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdc35dc35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30716279    15358108+   7  HPFS/NTFS
/dev/sda2        30716280   144584999    56934360    f  W95 Ext'd (LBA)
/dev/sda5   ?  3439628501   457337645   656338220+  59  Unknown

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x64e7383e

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xefa5e7b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63  1254387329   627193633+   7  HPFS/NTFS
/dev/sdc2      1254596175  1465144064   105273945    5  Extended
/dev/sdc5      1254596238  1456501094   100952428+  83  Linux
/dev/sdc6      1456501158  1465144064     4321453+  82  Linux swap / Solaris

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6609cb8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   390716864   195358401    7  HPFS/NTFS

---

### Post by caljohnsmith on 2008-11-02
That's great news you can at least boot Ubuntu now from the Ubuntu drive. To boot Windows, first open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then add the following three entries at the end of the file:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title	   Windows XP (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```
It's possible that you won't be able to boot Windows with any of the above entries because of your RAID setup; if none of the above entries work, I don't think you'll be able to boot Windows from Grub, unless you change your BIOS settings or something that will change how the RAID setup looks to Grub. 

Also, since we don't know which swap partition you deleted, it would be good to do a quick check to make sure your Ubuntu uses the swap partition that is left:
```
sudo blkid -c /dev/null
cat /etc/fstab
```
Check that your fstab entry for "swap" uses the UUID for sdc6. If it doesn't, you'll need to correct that; also you'll need to fix another file too, so let me know first. Anyway, reboot, and let me know what happens when you try each of the Windows entries from Grub. :)

---

### Post by rMatey on 2008-11-02
Don't mean to butt in, but when I first installed to dual drives on one computer, and a dual-boot on a single drive on another, this site helped me.  Although a little date, it does answer a lot of those problems.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

:-\"

---

### Post by Aldyrin on 2008-11-02
Well, I think this particular problem has been solved!  The first boot option for windows worked like a charm.  

The swap file seems to be configured correctly. 

```

/dev/sdc1: UUID="36C8BAA4C8BA61B3" LABEL="STORAGE2" TYPE="ntfs" 
/dev/sdc5: UUID="88365da4-e592-4793-ab93-8b4e77c51b46" TYPE="ext3" 
/dev/sdc6: UUID="b7d468c4-c518-4563-9168-68aed8c79059" TYPE="swap" 
/dev/sdd1: UUID="9CA8CAC7A8CA9F60" LABEL="STORAGE1" TYPE="ntfs" 


$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc5
UUID=88365da4-e592-4793-ab93-8b4e77c51b46 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc6
UUID=b7d468c4-c518-4563-9168-68aed8c79059 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Thanks for all the help!

---

### Post by caljohnsmith on 2008-11-02
That's great news, glad you can boot Windows from Grub now. Cheers and have fun. :)

---

