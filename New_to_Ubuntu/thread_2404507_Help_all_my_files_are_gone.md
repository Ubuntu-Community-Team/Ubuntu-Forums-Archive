---
title: "Help all my files are gone"
date: 2018-10-24
forum: New to Ubuntu
---

### Post by power-odal on 2018-10-24
just started my comp this day and one of my partitions says 

Error opening   transport endpoint is not connected

it still shows that my partition is 70 % full in diskmanager

i dont want to go back to win 10 but if my stuff just disappear i hafto go back

---

### Post by oldfred on 2018-10-24
Never seen this error before but found this:
[https://stackoverflow.com/questions/16002539/fuse-error-transport-endpoint-is-not-connected](https://stackoverflow.com/questions/16002539/fuse-error-transport-endpoint-is-not-connected)

Are you mounting a Windows file system that is now corrupted from abnormal shutdown?
If NTFS you have to use your Windows to run chkdsk on the NTFS partition. That cannot be done from Linux.

Post these from live installer:
sudo parted -l
lsblk -f
cat /etc/fstab

---

### Post by power-odal on 2018-10-24
```
Model: ATA HFS256G39TNF-N3A (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  274MB   273MB   fat32           EFI system partition          boot, esp
 2      274MB   290MB   16,8MB                  Microsoft reserved partition  msftres
 3      290MB   74,7GB  74,4GB  ntfs            Basic data partition          msftdata
 4      74,7GB  203GB   128GB                   Basic data partition          msftdata
 6      203GB   245GB   42,4GB  ext4
 7      245GB   255GB   10,0GB  linux-swap(v1)
 5      255GB   256GB   1049MB  ntfs            Basic data partition          hidden, diag


Model: Samsung Flash Drive FIT (scsi)
Disk /dev/sdb: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32,8kB  128GB  128GB  primary

Model: ATA HFS256G39TNF-N3A (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  274MB   273MB   fat32           EFI system partition          boot, esp
 2      274MB   290MB   16,8MB                  Microsoft reserved partition  msftres
 3      290MB   74,7GB  74,4GB  ntfs            Basic data partition          msftdata
 4      74,7GB  203GB   128GB                   Basic data partition          msftdata
 6      203GB   245GB   42,4GB  ext4
 7      245GB   255GB   10,0GB  linux-swap(v1)
 5      255GB   256GB   1049MB  ntfs            Basic data partition          hidden, diag


Model: Samsung Flash Drive FIT (scsi)
Disk /dev/sdb: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32,8kB  128GB  128GB  primary

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=b4fc6c46-5d6d-466b-aafa-db3b47640425 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=B0D4-ABAC  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda7 during installation
UUID=a1c2cc37-3b71-459a-a9f5-eae290acc425 none            swap    sw              0       0
```

---

### Post by power-odal on 2018-10-24
my partition is exfat i think

---

### Post by power-odal on 2018-10-24
i booted windows up and used chkdisk and it did not help

in windows it says the drive is 70% full to but all my files are gone all the same

---

### Post by power-odal on 2018-10-24
im tired off w8ing it feels like that bad partition is holding me hostage. i cant use it to download more stuff or use what i had on it. im going to delete it and ad the space to linux.
maby in doing so it may prevent the space from going bad again. (feels like windows and linux dont see eye to eye)

i just hope it wont kill my usb drive that is exfat

---

### Post by QIII on 2018-10-24
If you delete it, you will surely lose anything you have on it.  Don't do that just yet.  Someone may yet come along with an answer for you.

---

### Post by power-odal on 2018-10-25
i think chkdisk in windows made the the problem worse. it wrote 2 files to it.
one 3.1 mb file and 3.2 gb file. 
it feelt like the index off the hardrive was gone and now windows checkdisk wrote 2 random checkfiles right on it .....

i deleted the partition and im making it linux space

---

### Post by oldfred on 2018-10-25
Which partition is it, the Samsung Flash drive?
Did you try testdisk or photorec?

Testdisk may show old partitions and deeper search may show files. If so best to immediately copy them.
       [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by power-odal on 2018-10-25
it was this one 
4      74,7GB  203GB   128GB                   Basic data partition          msftdata

i remade it into linux space, i hope that helps in the future
the development for my 4x5 film is in my head so i dont nead the txt anymore
rest of the stuff il try to download again

i hope it never happens again ...

u can lock this tread or take it away

---

