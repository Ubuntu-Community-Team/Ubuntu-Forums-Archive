---
title: "[SOLVED] Hard disk drives are inaccessible"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by fr.theo on 2008-10-10
Hello,


I have had this problem with both Ubuntu 8.04 hardy 32 bit and 64 bit versions, when I first installed them all drives are accessible but after a few updates and installs i can access most of them and some i cannot?

e.g. I have 4 internal drives and 4 external drives, I can access my external drives at any time, and only 2 of my internal or 3 some times leaving one of them and the most important one inaccessible. 

Here's what gets me it likes to play musical chairs or in this case Musical Hard Drives, with every boot it changes another drive I cannot access and allows me access on the drive i couldn't access before, at this pont i need to shut down and reload to get the drive I want.

i have searched for ways on the internet to mount them but to no avail, all i receive is the message that "i do not have privileges to access this drive". I have tried mount, even altering the fstab to get it to work according to information i sourced from the net, any HELP will be appreciated.

---

### Post by Elfy on 2008-10-10
Could you post the results of these please and we can have a look
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
df -h
```

Please put each inside [noparse]```
 and 
```[/noparse] - makes it easier to read :)

---

### Post by fr.theo on 2008-10-10
Here is the output you requested.

FDISK -l output.

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd29fd29f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38161   306528201   83  Linux
/dev/sda2           38162       38913     6040440    5  Extended
/dev/sda5           38162       38913     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56d34d1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14562   116969233+  83  Linux
/dev/sdb2           14563       30401   127226767+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c159ba2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d306

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdf: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06320631

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      121601   976760001    c  W95 FAT32 (LBA)

Disk /dev/sdh: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       19122   153597433+   7  HPFS/NTFS
/dev/sdh2           19123       38913   158971207+   7  HPFS/NTFS

```

CAT FSTAB output.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a294e0ce-b258-4f1c-99c0-ca197b67aaf3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=53623efb-225f-401a-a35d-bdc31396dad8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1 /media/WD5000 ntfs-3g defaults 0 0

```


BLKID output.

```
sudo: unable to resolve host Theodore
/dev/sda1: UUID="a294e0ce-b258-4f1c-99c0-ca197b67aaf3" TYPE="ext3" 
/dev/sdb1: UUID="f07c7000-f812-46da-a836-84a7b45f498d" TYPE="ext2" 
/dev/sdc1: UUID="68FC75CEFC759752" LABEL="WD5000" TYPE="ntfs" 
/dev/sdd1: UUID="92E84EAFE84E9181" LABEL="LACIE " TYPE="ntfs" 
/dev/sde1: UUID="5CE0D3FAE0D3D7FA" LABEL="NEXTSTAR3" TYPE="ntfs" 
/dev/sdb2: UUID="af8dbf77-611b-4fd8-a85b-5103633dd4b2" TYPE="ext2" 
/dev/sdf1: UUID="06005D36005D2DC5" LABEL="LACIE " TYPE="ntfs" 
/dev/sdg1: LABEL="My Book" UUID="7F17-B427" TYPE="vfat" 
/dev/sdh1: UUID="5890F7C890F7AAA0" LABEL="Application" TYPE="ntfs" 
/dev/sdh2: UUID="9EBC39AABC397E39" LABEL="Media" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="53623efb-225f-401a-a35d-bdc31396dad8" 
```

DF -H output.

```
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             291G   14G  262G   5% /
varrun               1008M  232K 1007M   1% /var/run
varlock              1008M  4.0K 1008M   1% /var/lock
udev                 1008M  148K 1008M   1% /dev
devshm               1008M   12K 1008M   1% /dev/shm
lrm                  1008M   44M  964M   5% /lib/modules/2.6.24-19-generic/volatile
/dev/sdc1             466G  285G  182G  62% /media/WD5000
/dev/scd0             4.8G  4.8G     0 100% /media/cdrom0
/dev/sdf1              75G   74G  1.1G  99% /media/LACIE 
/dev/sdh2             152G  137G   15G  91% /media/Media
/dev/sdh1             147G   61G   86G  42% /media/Application
/dev/sdg1             932G  382M  931G   1% /media/My Book
/dev/sde1             299G  291G  7.9G  98% /media/NEXTSTAR3

```


Here it is and Thank you.

---

### Post by Elfy on 2008-10-10
Are the internal drives - sda to sdd and the externals that don't cause a problem sde to sdh?

Also - do you want the internals to be shown on the desktop or not.

---

### Post by fr.theo on 2008-10-10
these are the externals, one of them are partitioned and yes i want all drive visible and accessible, hope i am not being too unreasonable.

/dev/sdf1              75G   74G  1.1G  99% /media/LACIE 
/dev/sdh2             152G  137G   15G  91% /media/Media
/dev/sdh1             147G   61G   86G  42% /media/Application
/dev/sdg1             932G  382M  931G   1% /media/My Book
/dev/sde1             299G  291G  7.9G  98% /media/NEXTSTAR3


Thank you once again.

---

### Post by Elfy on 2008-10-10
> hope i am not being too unreasonable.Completely unreasonable and I refuse to go further :lol:

To add your internals to fstab and get them to mount on boot - you can change the names of the folders to suit you I'll use simple ones here, make sure that changes to the folder names is reflected in fstab.

```
sudo mkdir /media/drive1 /media/drive2 /media/drive3 /media/drive4
```

Backup and open fstab for editing, add the lines to the bottom

```
sudo cp /etc/fstab /etc/fstab.1010
gksudo gedit /etc/fstab
```

```
#Internal Drives
#dev/sdb1
UUID=f07c7000-f812-46da-a836-84a7b45f498d /media/drive1 relatime 0 2

#dev/sdb2
UUID=af8dbf77-611b-4fd8-a85b-5103633dd4b2 /media/drive2 relatime 0 2

#dev/sdc1
UUID=68FC75CEFC759752 /media/drive3 ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0

#dev/sdd1
UUID=92E84EAFE84E9181 /media/drive4 ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
```

Save and close gedit, run this to mount - if there are errors, stop and post them

```
sudo mount -a
```

For permissions/ownership of the linux drives, replacing user with your username

```
sudo chown user.user /media/drive1
sudo chmod 770 /media/drive1
sudo chown user.user /media/drive2
sudo chmod 770 /media/drive2
```

Check all are mounte ok with ```
df -h
```

Information from [here]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by fr.theo on 2008-10-10
Thanks I'll give it a go, could you bare with me just a little more I assure you I won't ask for any more unreasonable requests, For now. :^o

---

### Post by fr.theo on 2008-10-10
Thanks that got it working, really appreciate it, all the best and Thank you once again.

---

