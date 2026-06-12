---
title: "how to access 2nd hard drive"
date: 2022-06-04
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2022-06-04
I have my primary hard drive with Ubuntu 22.04 /dev/sb. I have a second hard /de/sdb1 also installed as shown below
```
Filesystem     1K-blocks      Used Available Use% Mounted on
tmpfs             390848     11904    378944   4% /run
/dev/sdb2      959863856 111352260 799683388  13% /
tmpfs            1954236     67268   1886968   4% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
/dev/sdb1         523248      6612    516636   2% /boot/efi
tmpfs             390844       160    390684   1% /run/user/1000
```
How can I access the second drive and also return to main hard drive. Thx for help

---

### Post by oldfred on 2022-06-04
Your sdb1 and sdb2 are just two partitions on sdb? Both partitions are required to boot in UEFI mode.

Do you have a sda drive that you want to mount?
Post this in code tags:
sudo parted -l

---

### Post by deadflowr on 2022-06-04
Not a second hard drive, it's all one drive, you have two partitions both already mounted.
The main is mounted at / root and the second is mounted at /boot/efi.

Ninja'd, oldfred has got this.

---

### Post by TheFu on 2022-06-04
Dude, accurate details matter if you want accurate answers. Please fix the clear typos in the post able.

 /dev/sb is wrong.
 /de/sdb1  is wrong.

And be certain you understand the difference between a "hard drive" and a "partition".  Everyone except MS-Windows uses the correct terms. Microsoft warped far too many minds by calling a "partition" a "drive" much of the time.  

Please post (and edit the first post above) to have all terminal output wrapped in forum code tags.  This is how: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)  It makes the columns line up correctly so dumb mistakes aren't made by you or us.

Thanks.

So, we need to know
1) drive information
2) partition information
3) file system information
Each of those 100% accurate - no typos.

the commands to provide that information are:
```
sudo parted -l
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
```
I've used code-tags above. _If your posts don't look like that, please fix it._

---

### Post by tuesdaybarrett on 2022-06-05
Model: ATA SanDisk SD6SB1M1 (scsi)                                        
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 


Model: ATA WDC WD10EZEX-60Z (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1000GB  1000GB  ext4




NAME     SIZE TYPE FSTYPE MOUNTPOINT
sda    119.2G disk        
sdb    931.5G disk        
&#9500;&#9472;sdb1   512M part vfat   /boot/efi
&#9492;&#9472;sdb2   931G part ext4   /run/timeshift/backup
sr0     1024M rom         
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdb2      ext4  916G  107G  763G  13% /
/dev/sdb1      vfat  511M  6.5M  505M   2% /boot/efi

---

### Post by tea for one on 2022-06-05
Is this the same question as your thread from March 20th 2021?
[https://ubuntuforums.org/showthread.php?t=2459524](https://ubuntuforums.org/showthread.php?t=2459524)

Anyway, [COLOR="#0000FF"]Model: ATA SanDisk SD6SB1M1 (scsi[/COLOR]) has [COLOR="#0000FF"]Partition Table: unknown[/COLOR]

Are you unable to create a partition table and subsequent partitions on this device?

---

### Post by oldfred on 2022-06-05
If gparted does not show drive, you may need to update firmware for SSD.
In upper left corner of gparted is a combo box to select which drive you are partitioning.

---

