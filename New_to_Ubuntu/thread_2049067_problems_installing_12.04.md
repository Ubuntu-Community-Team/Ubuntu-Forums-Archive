---
title: "problems installing 12.04"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by djyoung4 on 2012-08-27
I had a box that was running 10.04 with 3 drives.  2X1 TB drives for storage and then 1X2 TB drive that had the OS installed on it.  I got a [refurbished drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152304") that I then planned to install 12.04 on to and get rid of 10.04 and leave the larger drives just for storage.  The problem is I cannot get the drive to show up when I go to install 12.04.  I have tried multiple sata ports and different configurations but cannot get it to work.  I'm not even sure if I have gotten the drive to mount but I can hear it spinning up and it doesn't sound like its having any problems.  If anybody has any input it would be greatly appreciated.  My BIOS recognizes the drive but it takes a little while as well

---

### Post by djyoung4 on 2012-08-28
I figured out that if I boot with my 2 TB drive (where 10.04 is installed) and the 40 GB (Where I intend to install 12.04) both connected then it will just send me to a BusyBox terminal but if I disconnect the 40 GB then it boots perfectly fine into 10.04.  any ideas

---

### Post by mastablasta on 2012-08-28
> **djyoung4 said:**
> I figured out that if I boot with my 2 TB drive (where 10.04 is installed) and the 40 GB (Where I intend to install 12.04) both connected then it will just send me to a BusyBox terminal but if I disconnect the 40 GB then it boots perfectly fine into 10.04. any ideas
 
 
what happens if you boot from 40GB drive and stick only that one inside?
 
it could be that the drive is no good.

---

### Post by djyoung4 on 2012-08-30
> **mastablasta said:**
> what happens if you boot from 40GB drive and stick only that one inside?
 
it could be that the drive is no good.

I just get a black screen with the white cursor blinking.  There is nothing installed or saved on the drive at all.

---

### Post by Bashing-om on 2012-08-30
all:

 Recon this drive is a western digital with windows metadata inscribed on it?

djyoung4;
  does Gparted (in live cd) see this disk ?

[INDENT]BDQ
[/INDENT]

---

### Post by djyoung4 on 2012-08-30
No it does not show up in ubuntu 12.04 live cd.  I have not tried an actual gparted live cd

---

### Post by Bashing-om on 2012-08-30
see if this applies:
[http://www.ehow.com/how_6120791_unlock-western-digital-hard-drive.html](http://www.ehow.com/how_6120791_unlock-western-digital-hard-drive.html)
and here is some passwords to try:
[http://ubuntuforums.org/showthread.php?t=2049360&page=2](http://ubuntuforums.org/showthread.php?t=2049360&page=2)


[INDENT]HTH <==BDQ
[/INDENT]

---

### Post by djyoung4 on 2012-09-02
> **Bashing-om said:**
> see if this applies:
[http://www.ehow.com/how_6120791_unlock-western-digital-hard-drive.html](http://www.ehow.com/how_6120791_unlock-western-digital-hard-drive.html)
and here is some passwords to try:
[http://ubuntuforums.org/showthread.php?t=2049360&page=2](http://ubuntuforums.org/showthread.php?t=2049360&page=2)


[INDENT]HTH <==BDQ
[/INDENT]

Its a samsung drive though.  All my other drives are WD but they work great :confused:

---

### Post by Bashing-om on 2012-09-03
djyoung4; 

  Sheeesh; Is there anyway to determine the linux drive designator ( ie: sdc )?

with the drive pluged in does 
```
sudo fdisk -l
```
give a result for this drive?

I have something to try if the drive id can be determined. I also had a drive recently that was not recognized by my OS. I zeroed out the entire drive with the dd command, was able to format and there after partition it (in use now!).

 I would think that if you pulled one of the good drives, left the booting drive and the "bad" drive in ...the bad drive would be sdb, the boot drive sda ??? Need to run blkid and compare fstab file maybe others to determine the booting drives ID ??

 Anyway, let me know if you want to proceed and take this approach.

[INDENT]regards <==BDQ
[/INDENT]

---

### Post by djyoung4 on 2012-09-11
Sorry for the late response.  Heres my fdisk.  I dont think it shows the drive though.  this is with all my drives plugged in and running 12.04 off a livecd.  I am unable to boot with my 10.04 drive and the "bad" drive plugged in
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b83fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  1953520064   976760001    b  W95 FAT32

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT

```Here it is off the 10.04 after booting and then plugging the drive in.  Not sure if that even works that way
```
home@home-desktop:~$ sudo fdisk -l
[sudo] password for home: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b83fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001    b  W95 FAT32

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   83  Linux

```

---

