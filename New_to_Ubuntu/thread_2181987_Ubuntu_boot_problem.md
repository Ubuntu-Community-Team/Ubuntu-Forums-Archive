---
title: "Ubuntu boot problem"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by NMrpHzy on 2013-10-19
I've had ubuntu running for a month or so, but now it won't boot. Upon using a live cd to get onto the computer when I open gparted I reveive the following messages:
"Libparted Bug Found! end of file while reading invalid argument"
then
"Libparted Bug Found! The primary GPT table is corrupt, but the backup appears OK, so that will be used."

Within the information of each partition of the main drive is a warning saying (using the first partition as an example): "Can't open /dev/sda1: No such file or directory"

Any advice?

---

### Post by fantab on 2013-10-20
Boot with Live DVD/USB, Open Terminal [Ctrl+Alt+T] and post the output of the following commands:

```
sudo parted -l
sudo fdisk -l
```

---

### Post by NMrpHzy on 2013-10-20
Here is the output from the 2 requested commands:
ubuntu@ubuntu:~$ sudo parted -l
Error: end of file while reading No such file or directory                
Retry/Ignore/Cancel? Retry                                                
Error: end of file while reading Success                                  
Retry/Ignore/Cancel? Retry                                                
Error: end of file while reading Success                                  
Retry/Ignore/Cancel? Ignore
Error: The primary GPT table is corrupt, but the backup appears OK, so that will
be used.
OK/Cancel? OK                                                             
Model: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  99.6MB  98.6MB  fat32                 boot
 2      99.6MB  111GB   111GB   ext4
 3      111GB   120GB   8552MB  linux-swap(v1)


Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4         boot


Model: SanDisk Cruzer Micro (scsi)
Disk /dev/sdc: 2018MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      66.0kB  2000MB  2000MB  primary  fat16        boot


ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0005e1e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  3907028991  1953513472   83  Linux

Disk /dev/sdc: 2017 MB, 2017525248 bytes
64 heads, 63 sectors/track, 977 cylinders, total 3940479 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *         129     3907007     1953439+   6  FAT16

---

### Post by NMrpHzy on 2013-10-22
Does anyone have any advice on this?

I'm just checking before I try to re-install from scratch. I don't have any idea how to proceed otherwise (I searched on-line and tried various things but with no success) so I see this as the best option to try to get the system working again.

Thanks

---

### Post by fantab on 2013-10-23
Is that 120Gb disk SSD?
Are you dual booting with Windows8? it doesn't look like it but I am confirming. Did Win8 come pre-installed at some point and you removed it?
Are you booting in UEFI?

It is unlikely that just re-installing ubuntu "from scratch' will solve this. We need to fix that GPT error on your /dev/sda first. We need more information about above questions.

---

### Post by NMrpHzy on 2013-10-23
Yes, the 120GB is an SSD drive, and it contained the operating system.

The system is not running as a dual boot,    and has never had windows 8 (or any other OS) installed. The 13.04 installation of Ubuntu, was the first use of the drive.

I do not fully understand the UEFI question. I'm not sure if this should be any sort of setting with regards the OS. The BIOS setting on this is set to UEFI or legacy (I tried changing to legacy only but it didn't help so I put it back). This was the setting that ubuntu had been operating on up until the point of not working.

---

### Post by fantab on 2013-10-23
I suggest you reformat your SSD, this means you will loose all data. So BACKUP all important DATA first.

Boot with Ubuntu Live DVD/USB and using Gparted delete all the partitions. You will have to apply changes.
Now you will have to create a new partition table, Gparted- Devices- create new partition table- choose 'Advanced' to select GPT.
UEFI boot will only happen with GPT table. So if you want to boot with UEFI then create GPT table or use 'msdos' if you want to boot in 'Legacy' mode. I recommend you use UEFI with GPT, if possible also change your HDD to GPT.

After creating the partition create your partitions as you deem fit. Heres' what I'd do:
300MB FAT32 EFI partition and put a 'boot' flag.
30GB EXT4 Ubuntu /
30GB EXt4 free (If in future you want to install another Distro or Ubuntu flavor or version)
4GB SWAP
All the remaing GB EXT4 /home or plain DATA.

Reinstall Ubuntu.

EDIT: I suggest you give [FIXPARTS]("http://www.rodsbooks.com/fixparts/") a try before you proceed with the above... its a simple utility and might prove useful. BACK UP your DATA first.
I did not suggest it earlier because generally if fixes stray GPT data that is left over when we change the partition table from GPT to 'msdos'. But since your SSD is already GPT, I am not sure how it will help. Nevertheless its worth a try.

Also check in your BIOS/UEFI for '[Intel SRT]("http://www.hardwaresecrets.com/printpage/Intel-Smart-Response-Technology-Explained/1292")' if you find it then DISABLE it. It uses some sort of RAID for cacheing in Windows8.

---

### Post by NMrpHzy on 2013-10-23
Thank you for your advice. I will try this when I get home from work, and I will update you.

---

### Post by oldfred on 2013-10-23
You mention dual boot. Is that Windows? 
Windows only boots from gpt partitioned drives with UEFI.
Ubuntu can boot from gpt drives with BIOS or UEFI modes.
Both Windows & Ubuntu can only boot from MBR partitioned drives with BIOS.

I have several drives and kept my old XP install on MBR partitioned drive, but now use gpt with a bios_grub partition to boot in BIOS mode as my system does not have UEFI. 

I also suggest keeping Windows & Ubuntu on separate drives, but when you have an SSD you often want both on it. 
But you must have both systems booting in same boot mode, either both UEFI or both BIOS to easily dual boot. Otherwise you have to go into UEFI/BIOS and turn on or off UEFI to boot on or the other system. Some will auto switch but you still have to boot from UEFI menu every time as you cannot change boot mode after grub loads, so you cannot use it to dual boot.

Or bottom line, I recommend gpt partitioning unless you have or may want Windows in BIOS boot mode on same drive.

 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

---

### Post by NMrpHzy on 2013-10-23
Many thanks for your advice, I have managed to get the system to start-up again. I started trying to follow your instructions for gparted, however the program came up with errors when I tried to delete the partitions and then hung. I then noticed your edit and had a look at fixparts. This didn't work directly (didn't seem to work with GPT), but it led me to gdisk. I made a few guesses in that (didn't feel like there was much to loose) and used the backup partition table to overwrite the main one. This resolved the boot problem without having to re-install ubuntu.

I just wanted to ask the following question before closing the thread:
It is operational at the moment, is there any reason for it not to stay this way? 
Or is there anything that I should do in order try to improve the stability/stop recurrence of the problem?



In case it is of use to anyone else who has a similar issue I've copied below the terminal lines that resolved the issue:
buntu@ubuntu:~$ fixparts /dev/sda
The program 'fixparts' is currently not installed. You can install it by typing:
sudo apt-get install gdisk
You will have to enable the component called 'universe'
ubuntu@ubuntu:~$ sudo apt-get install gdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gdisk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 328 kB of archives.
After this operation, 755 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main gdisk amd64 0.8.5-1ubuntu2 [328 kB]
Fetched 328 kB in 1s (325 kB/s)
Selecting previously unselected package gdisk.
(Reading database ... 161462 files and directories currently installed.)
Unpacking gdisk (from .../gdisk_0.8.5-1ubuntu2_amd64.deb) ...
Processing triggers for doc-base ...
Processing 32 changed doc-base files, 1 added doc-base file...
Processing triggers for man-db ...
Setting up gdisk (0.8.5-1ubuntu2) ...
ubuntu@ubuntu:~$ fixparts /dev/sda
FixParts 0.8.5

Loading MBR data from /dev/sda
Problem opening /dev/sda for reading! Error is 13.
You must run this program as root or use sudo!

Unable to read MBR data from '/dev/sda'! Exiting!

ubuntu@ubuntu:~$ sudo fixparts /dev/sda
FixParts 0.8.5

Loading MBR data from /dev/sda

This disk appears to be a GPT disk. Use GNU Parted or GPT fdisk on it!
Exiting!

ubuntu@ubuntu:~$ gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.5

Problem opening /dev/sda for reading! Error is 13.
You must run this program as root or use sudo!
ubuntu@ubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.5

Caution: invalid main GPT header, but valid backup; regenerating main header
from backup!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Command (? for help): ?
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): v

No problems found. 2925 free sectors (1.4 MiB) available in 2
segments, the largest of which is 2014 (1007.0 KiB) in size.

Command (? for help): r

Recovery/transformation command (? for help): ?
b    use backup GPT header (rebuilding main)
c    load backup partition table from disk (rebuilding main)
d    use main GPT header (rebuilding backup)
e    load main partition table from disk (rebuilding backup)
f    load MBR and build fresh GPT from it
g    convert GPT into MBR and exit
h    make hybrid MBR
i    show detailed information on a partition
l    load partition data from a backup file
m    return to main menu
o    print protective MBR data
p    print the partition table
q    quit without saving changes
t    transform BSD disklabel partition
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Recovery/transformation command (? for help): b

Recovery/transformation command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sda.
The operation has completed successfully.
ubuntu@ubuntu:~$

---

### Post by oldfred on 2013-10-23
I am not sure why it said hybrid. That may mean you did have more than the one partition in the MBR partition table. The protective MBR table exists only to show drive is fully partitioned with gpt and old MBR tools should not then try to modify it.

Hybrid is often used with Mac as they boot with an older UEFI, so Windows is installed in MBR partitions within the gpt partition table.  Not seen it elsewhere and it is not recommended.

       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

### Post by NMrpHzy on 2013-10-24
It would appear that I spoke too soon. Less than 24hrs after getting the system to operate the problem has re-occurred. Exactly as before, with the GPT partition table on the boot drive but the backup okay. I have the system operating again, but having to live boot and use gdisk to replace the GPT table with the backup every day hardly seems feasible long term. I should clarify that the system shut down and re-booted about 4 times before the GPT failed. The most recent of which was approximately 3 hours before the failure case. 

Here is some more information with regards the build. It was a new build, on a brand new ssd drive. So no windows, on it now or ever, and no dual boot. The partition table and table format is exactly how ubuntu chose to make it during an installation from a live usb session.

I don't know much about how SSD drives work, is the GPT always stored in the same position on the drive? Would there be any way to automatically tell the computer to use the back-up GPT instead of the main?
Any advice would be much appreciated.

---

### Post by oldfred on 2013-10-24
I have been using gpt on a hard drive since 10.10 and on my SSD for amost two years with out issue.

Post this, but change to ssd drive if not sda:

       sudo gdisk -l /dev/sda

---

### Post by NMrpHzy on 2013-10-25
Thanks for your input, as requested:

sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 234441648 sectors, 111.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): F1FA6518-6E46-460F-A46D-40FC0EF94711
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 2048-sector boundaries
Total free space is 2925 sectors (1.4 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          194559   94.0 MiB    EF00  
   2          194560       217737215   103.7 GiB   0700  
   3       217737216       234440703   8.0 GiB     8200

---

### Post by oldfred on 2013-10-25
Gdisk seems to see drive correctly. Beyond that I do not know why there would be issues unless something else like Windows is writing MBR info into drive. Typical Windows install will convert a gpt drive to MBR, but leave backup gpt drive creating issues. But you are only showing three partitions.

---

