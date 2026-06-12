---
title: "HDD Problem with Linux Desktop 13.10"
date: 2013-10-29
forum: New to Ubuntu
---

### Post by jamie_starr2 on 2013-10-29
[INDENT] 					Hey guys, I've only just installed Linux 13.10 today, and I'm brand  new to the OS. I keep getting a problem with my secondary HDD.

 The facts:
 128GB SSD Partition
 Windows on 60GB
 Linux on 30GB
 3GB spare for w/e.

 I then have a 1TB Western Digital Caviar Blue dynamic HDD, partitioned  into 3 main sections (but they're a bit split up due to a repartitioning  issue)

 The 'Stuff' partition I can access from Linux, but the 'Games' and  'Spare' partitions give me this message every time I try and mount:

[COLOR=#003366]Error mounting system-managed device /dev/sdb2:  Command-line `mount "/mnt/622CFFFC2CFFC8D5"' exited with non-zero exit  status 12: Failed to read last sector (590368767): Invalid argument[/COLOR]
[COLOR=#003366]HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,[/COLOR]
[COLOR=#003366]   or it was not setup correctly (e.g. by not using mdadm --build ...),[/COLOR]
[COLOR=#003366]   or a wrong device is tried to be mounted,[/COLOR]
[COLOR=#003366]   or the partition table is corrupt (partition is smaller than NTFS),[/COLOR]
[COLOR=#003366]   or the NTFS boot sector is corrupt (NTFS size is not valid).[/COLOR]
[COLOR=#003366]Failed to mount '/dev/sdb2': Invalid argument[/COLOR]
[COLOR=#003366]The device '/dev/sdb2' doesn't seem to have a valid NTFS.[/COLOR]
[COLOR=#003366]Maybe the wrong device is used? Or the whole disk instead of a[/COLOR]
[COLOR=#003366]partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/COLOR]
 Being a complete newbies, I have no idea what to do, can you help? 				
[/INDENT]

---

### Post by Bashing-om on 2013-10-29
jamie_starr2; Hi !

We can for sure help, but lets see what is going on,
Post back the outputs of terminal codes - between code tags (#) ! :
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print
cat /etc/fstab ##what and how you "want" auto mounted
mount ##to show what is mounted
cat /etc/mtab ##corroboration as to what the system has mounted and where.

```
and was this hard disk ever a part of a raid array ? ,-> are these warnings due to the presence of "meta data" (a desk top install does not understand the server data headers)?

We will see what there is to work with, and then can see what can be done.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by sandyd on 2013-10-29
> **jamie_starr2 said:**
> [INDENT] 					Hey guys, I've only just installed Linux 13.10 today, and I'm brand  new to the OS. I keep getting a problem with my secondary HDD.

 The facts:
 128GB SSD Partition
 Windows on 60GB
 Linux on 30GB
 3GB spare for w/e.

 I then have a 1TB Western Digital Caviar Blue dynamic HDD, partitioned  into 3 main sections (but they're a bit split up due to a repartitioning  issue)

 The 'Stuff' partition I can access from Linux, but the 'Games' and  'Spare' partitions give me this message every time I try and mount:

[COLOR=#003366]Error mounting system-managed device /dev/sdb2:  Command-line `mount "/mnt/622CFFFC2CFFC8D5"' exited with non-zero exit  status 12: Failed to read last sector (590368767): Invalid argument[/COLOR]
[COLOR=#003366]HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,[/COLOR]
[COLOR=#003366]   or it was not setup correctly (e.g. by not using mdadm --build ...),[/COLOR]
[COLOR=#003366]   or a wrong device is tried to be mounted,[/COLOR]
[COLOR=#003366]   or the partition table is corrupt (partition is smaller than NTFS),[/COLOR]
[COLOR=#003366]   or the NTFS boot sector is corrupt (NTFS size is not valid).[/COLOR]
[COLOR=#003366]Failed to mount '/dev/sdb2': Invalid argument[/COLOR]
[COLOR=#003366]The device '/dev/sdb2' doesn't seem to have a valid NTFS.[/COLOR]
[COLOR=#003366]Maybe the wrong device is used? Or the whole disk instead of a[/COLOR]
[COLOR=#003366]partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/COLOR]
 Being a complete newbies, I have no idea what to do, can you help? 				
[/INDENT]
If its a dynamic disk, it wont work in Linux - backup and convert it back into a basic disk and it will work.

---

### Post by fantab on 2013-10-30
If this is a laptop and came with both SSD and HDD with a pre-installed Windows8 then the chances are you have Intel SRT. Intel SRT uses RAID. You have to [disable IntelSRT]("http://superuser.com/questions/476777/properly-disabling-intel-srt").

EDIT: Post a screenshot of your partitions from Windows Disk Management. If you have any 'Dynamic Disks' then they would show only with Windows's tools.

---

