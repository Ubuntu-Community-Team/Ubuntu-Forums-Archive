---
title: "[SOLVED] Cannot mount 2nd hard drive"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by worlestone on 2008-05-20
I have Hardy running fine on my PC.  It originally ran on a Western Digital 80Gb disk which I swapped over for a Hitachi 250Gb disk and ran a data dump to transfer everything.  I then ran a 40Gb disk as a second disk for a while and now want to run the 80Gb disk again, but I cannot see it in the 'places' drop down.

I can see it when the PC boots in the BIOS text which appears and I can see it in Gparted, but cannot get to it.  I have run fdisk in terminal and found the following:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37f1a851

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda3           26061       30401    34869082+  83  Linux
/dev/sda4            9730       26060   131178757+  83  Linux
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37f1a851

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9541    76638051   83  Linux
/dev/sdb2            9542        9729     1510110    5  Extended
/dev/sdb5            9542        9729     1510078+  82  Linux swap / Solaris

Not sure what this means.

Can someone help?

Thanks

Adrian

---

### Post by forestpixie on 2008-05-20
Can you post results of these please from a terminal

```
cat /etc/fstab
ls /media
```

---

### Post by worlestone on 2008-05-20
Hi,

Thanks, it returns the following:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ac2544df-61cb-4d36-b2b1-1fff23cc9146 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3eb849f9-6ede-4017-90ba-d6f759a7ce4e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by vanadium on 2008-05-20
You most likely will need to update your /etc/fstab. Nowadays, hard drives are mounted using their UUID, which is unique identifier for a partition.

You can see the UUID of the various partitions running the command

sudo blkid

Load your /etc/fstab in an editor and change the UUID by the "UUID="..." from the above command.

Afterwards, check wether the edit was succesfull with the command

sudo mount -a

There should not be any output. If there is, post here. If there is not, your drive will be accessible through the mount point which is specified on the line for your drive in /etc/fstab.

If in doubt, post your fstab here, and the output of the above command. Then we can detail the changes.

---

### Post by forestpixie on 2008-05-20
You nedd to add them to fstab and make folders forthem to mount in - quite easy. Also you have an extra swap partition on the 80Gb drive, if the 80Gb drive used to have the install on it I would suggest using gparted to delete both partitions and creating a new clean ext3 - obviously iif it's got stuff you want don't :)

For each of the partitions you want to mount at boot do this - change the partition numbers to suit - pick names that you want for each of the mounted drive

```
sudo mkdir /media/nameofpartition
```
creates a folder for the partition to mount into, then

add a line to fstab

```
gksudo gedit /etc/fstab
```

to the end of the file add - example

#/dev/sdb1
/dev/sdb1 /media/nameofpartition ext3 defaults 0 2

once complete for each partition you wish to mount 

```
sudo mount -a
```

Edit - if you want mount them all you'll need to do so for 
sda2
sda4
sdb1

---

### Post by worlestone on 2008-05-20
Thanks.  I'm a bit confused here though as the UUID seems to be the same for sda1 and sdb1.  I ran sudo blkid and the result was:

/dev/sda1: UUID="ac2544df-61cb-4d36-b2b1-1fff23cc9146" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="3eb849f9-6ede-4017-90ba-d6f759a7ce4e" 
/dev/sdb1: UUID="ac2544df-61cb-4d36-b2b1-1fff23cc9146" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="562e0a22-0c07-4cc9-8d4d-dd11996b3588" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="25bf8152-d3b0-403d-9d07-2584346c0597" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="3eb849f9-6ede-4017-90ba-d6f759a7ce4e" 

Adrian

---

### Post by forestpixie on 2008-05-20
If as I suspect sdb1 is the old install and sdb5 the swap for that install - deleting the partitions and creating one new one would generate a new UUID.

Or do it the /dev/sda way without UUID

---

### Post by worlestone on 2008-05-20
Thank you.  This was it.  I ran Ubuntu from a lice CD and managed to use Gparted to delete and reformat sdb1.  I can now 'see' the drive on boot.  Next problem is that there appears to be just one folder which is 'lost + found'  I'll investigate.

Thanks again

---

### Post by forestpixie on 2008-05-20
If the drive had been newly created there will be nothing else yet - Lost and Found is the folder fsck creates when it checks a drive I believe.

You'll still need to edit fstab and mkdir for the drives to get tme to mount if you only want to mount sdb1

```
sudo mkdir /media/nameffordrive
```

add to fstab
```
gksudo gedit /etc/fstab
```

> #dev/sdb1
/dev/sdb1 /media/namefordrive ext3 defaults 0 2

change namefordrive to something you want

---

