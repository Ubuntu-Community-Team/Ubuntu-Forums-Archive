---
title: "(L)ubuntu 12.10 Which hard drive partitition/file system needed?"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by Locus Kiesselbachi on 2013-04-09
Hello!

I want to install Linux OS on new hard drive.

Problem:
Lubuntu installation CD cant find hard drive.

In win7 with "Computer management" tool, made "MBR -master boot record", added NTFS file system.

1. HD 128Gb, win7
2. HD 256Gb - want to add lubuntu here, but cant (*sry, its 240GB)

BIOS seems to find 2.HD, win7 also.

Lubuntu install offers to add Linux aside win7, but if remove 1.st HD it cant find nothing. :(
*In live CD, it manages to find 2. hard drive in "file manager". :S

What do I do wrong?

---

### Post by Bashing-om on 2013-04-09
Locus Kiesselbachi;

How 'bout this; In order for a disk/partition to be recognized there must exist a format on the device to be recognized.

From the liveCD,( try ubuntu mode)  activate ubuntu's partition editor "GParted", choose the correct hard drive (upper right of screen),devices -> new and make a new partition table (format as "ext4" for 'buntu [NTFS = Windows]). Read and heed the help file's documentation.
Decide on how you want for partitions or let the install wizard decide for you.
Exit back to the desktop;
Click on the install icon, make sure you are installing on the correct drive.
a) use entire drive gives you the install wizard, will automagically set things up with a minimum amount of intercession on your part.
b) Something else -> says you know what you want and You will handle how to set up your partitions and what is installed on which partition. That means you have done your home work or have had experience ![INDENT=3]
hope this helps

[/INDENT]

---

### Post by Locus Kiesselbachi on 2013-04-09
Thank you for advice!

I run live CD, found "GParted", it found 2. hard drive. It made partitition ext4.
....
but installer still dont see the 2. HD. It offers installing Lubuntu alongside Win7 on 1. HD.:confused:

*I want to add images ...im in live CD, but cant make "print screen".

...update
Pulled off HD nr1 (win7).
start live CD
file-explorer finds 2.HD
Installation cant find no HD in "Insatallation type" menu - WTF?
I randomly pressed some choise there "+" or "-" or "Change..."
and it gave me an errormessage: "Ubi-partman crashed", Ubi-partman failed with exit code 141
:(
Now it does not let me to acces to 2.HD. After partitition, I remember there was file called lost+found (permission denied - when tried to open) - I guess it just need another restart.

Im tired... Ill look it tomorrow again

---

### Post by Bashing-om on 2013-04-09
Locus Kiesselbachi

Kind of at a loss here . I am "old school" and there are many technological things recently developed I have had little or no exposure to.

As bios, Windows7, and GParted can see the drive, I think that would rule out any type of hard ware problem.

As there was some formatting done on the drive in Windows, I wonder did Windows make up a "efi" partition ? How much of that hard drive can we see with ubuntu's tools ?
Try this - from the liveCD:
```

sudo fdisk -lu 
sudo parted -l 
sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print
```[INDENT=2]
there has to be a cause 

[/INDENT]

---

### Post by nerdtron on 2013-04-10
> **Locus Kiesselbachi said:**
> Hello!

I want to install Linux OS on new hard drive.

Problem:
Lubuntu installation CD cant find hard drive.

In win7 with "Computer management" tool, made "MBR -master boot record", added NTFS file system.

1. HD 128Gb, win7
2. HD 256Gb - want to add lubuntu here, but cant

BIOS seems to find 2.HD, win7 also.

Lubuntu install offers to add Linux aside win7, but if remove 1.st HD it cant find nothing. :(
*In live CD, it manages to find 2. hard drive in "file manager". :S

What do I do wrong?

If you have 2 physical hard drives, this process is easy. Remove the win7 hard drive and then install Ubuntu on the 2nd drive by choosing "Erase and use the entire disk" option in the installer. Then insert the win7 hard drive and make sure that the first boot priority is the Ubuntu drive. Open a terminal window and run
```
sudo update-grub
```
in order for win7 to be added to your boot options in GRUB.

Or if you just want to install Ubuntu in another partition or hard drive without removing the first one, I think what you need to click is the "Do Something Else" option. There you will be presented with all the partitions in your hard drive. You'll see there the 2nd HD for sure since the file manager was able to open it.

Goodluck and keep us posted.

---

### Post by Locus Kiesselbachi on 2013-04-10
@overall
I add that before all this the 2.HD was part of RAID0 system (with another-one, exactly the same HD). Maybe i really screwed up something (RAID0 partitition was made in BIOS).
But it still does not make sense... why liveCD can find it in "file-manager".

@[[COLOR=#000000]Bashing-om[/COLOR]]("http://ubuntuforums.org/member.php?u=1111508")
about EFI partitition. [Wikipedia]("http://en.wikipedia.org/wiki/EFI_System_partition") says that doing MBR partition, it should make the EFI-thingy (but does it, Im not sure). 
In the same article it writes on that ("Microsoft recommends that when partitioning a disk, the EFI System partition be the first partition on the disk"), so I conclude that it does not make EFI-thingy just like that.

But if GParted lets to partition-ate HD, it should make all the necesseties. Strange, isnt it?

> **Bashing-om said:**
> How much of that hard drive can we see with ubuntu's tools ?
file/manager sees 2.HD 240GB - all correct. Also it sees win7-1.HD 128GB - all correct.

**_TERMINAL_**(liveCD):
```
sudo fdisk -lu
```
**gives:**
Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9f76821d


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   468860927   234429440   83  Linux


Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc973dc20


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *      206848   250066943   124930048    7  HPFS/NTFS/exFAT

```
sudo parted -l
```
**gives:**
Model: ATA OCZ-VERTEX3 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  240GB  240GB  primary  ext4




Model: ATA OCZ-VERTEX4 (scsi)
Disk /dev/sdb: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End    Size   Type     File system  Flags
 1      106MB  128GB  128GB  primary  ntfs         boot




Model: TSSTcorp CDDVDW SH-224BB (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac


Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      2788MB  2798MB  9306kB               EFI
```
sudo parted /dev/sda unit s print
```
**gives:**
Model: ATA OCZ-VERTEX3 (scsi)
Disk /dev/sda: 468862128s
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End         Size        Type     File system  Flags
 1      2048s  468860927s  468858880s  primary  ext4
```
sudo parted /dev/sdb unit s print
```
**gives:**
Model: ATA OCZ-VERTEX4 (scsi)
Disk /dev/sdb: 250069680s
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start    End         Size        Type     File system  Flags
 1      206848s  250066943s  249860096s  primary  ntfs         boot





@[[COLOR=#000000]nerdtron[/COLOR]]("http://ubuntuforums.org/member.php?u=895543")
> **nerdtron said:**
> ...this process is easy. Remove the win7 hard drive and then...
Yes, it should be easy - agreed totally. 
But... by some reason it (installer) does not find 2.HD (file manager does, in liveCD). And yes I already pluged-OUT win7(1.st HD). So , it does not help or I didnt understand you correctly.

---

### Post by Locus Kiesselbachi on 2013-04-10
HAAA! found the bug
it seems RAID0 had some leftovers on 2.HD and thus misleading OS installer.

Uncle Google said that [**this site**]("http://www.ubuntubuzz.com/2011/05/install-ubuntu-1104-on-sata-hard-drives.html") might help and it did

```
sudo os-prober
```
**gives:**
ERROR: isw: wrong number of devices in RAID set "isw_ebdhdddbbh_RAID0_VTX3x2" [1/2] on /dev/sda


```
sudo dmraid -rE
```
[B]gives:
[/B]Do you really want to erase "isw" ondisk metadata on /dev/sda ? [y/n] :y

Lubuntu installer now finds 2.nd HD
[B]
Just for check
[/B]```
sudo os-prober
```
[B]now gives:
[/B]nothing... so I guess that means problem is [SOLVED]!
[B]
Thanks for everyone who guided me!

[/B]

---

### Post by docJ on 2013-04-10
> **Locus Kiesselbachi said:**
> 
Problem:
Lubuntu installation CD cant find hard drive.

I recently helped a neigboor who forgot his WindowsXP username/password on a computer that had no valuable data. 
We decided to reinstall XP but got the strange message about windows not finding a hard drive to install to.
Copying the exact error message on Google lead us to a rather simple solution; it was a bios thing about sata drive, something had to be disabled, although I don't quite remember what exactly

Maybe you too could get this fixed by copying the exact install error message on Google (or over here)

I beleive the fix looked something like this:

[h=2][/h] 
[LIST=1]
[*]Enter your BIOS/Setup Utility
[*]Locate the Serial ATA or SATA configuration section
[*]Change the mode of the SATA controller from **AHCI** to **IDE** or **Compatibility**
[*]Save & Exit
[*]Reboot and begin the Linux Setup again.
[*]When Linux setup completes **change the mode back to AHCI in the BIOS**
[/LIST]

---

### Post by Locus Kiesselbachi on 2013-04-10
@docJ
Hello!
I even tried to establish again RAID0 connection with one of this HD-s (2.nd), which included changeing SATA controller to RAID. By some reason, when computer restarted, it just flashed some fast text. Once it was even a mobo-s "RAID setting/up tool" with green text. Unfortunately text it showed was so short time and after that it just showed me blank-screen.
Thats why I decided to re-partitition-ate HD-s, but brought me to this problem (this thread).
Have nice day!

---

### Post by Bashing-om on 2013-04-10
All's well that ends well. Good troubleshooting on your part to isolate and resolve.
Raid's meta data bites again ! Great thing in the right place, but !
[INDENT=3]
proven again, there are no problems, just good solutions

[/INDENT]

---

