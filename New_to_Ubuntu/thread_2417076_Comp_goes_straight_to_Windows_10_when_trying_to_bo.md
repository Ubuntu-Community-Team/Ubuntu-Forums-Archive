---
title: "Comp goes straight to Windows 10 when trying to boot up Lubuntu 18.04 from UEFI menu"
date: 2019-04-20
forum: New to Ubuntu
---

### Post by de3ik on 2019-04-20
Hi. Sorry if this has been asked before. I do appreciate any help you can provide. I've used Lubuntu since 2015 but, I'm not very technical with computers and my knowledge is very limited so I ask that you please do use laymens terms so I can better understand you. 


I have an older computer (HP Compaq 8200 Elite CMT, Intel Core i5-2400, 3.10GHz) that I used to run Windows 7 pro on. In system information it says it has a legacy BIOS, but when I go to the startup menu as the computer boots up and tap F9 for the boot menu it says UEFI if this helpful in helping you to help me solve the problem. I installed Lubuntu 18.04 from a iso burned to DVD on a 64gb flash drive and with the intent of being able to boot to Lubuntu on this computer and others I would use from the flash drive. When I booted up and had the option to go to Linux from my boot menu it showed 1 Windows entry and for some odd reason, 4 boot entries for ubuntu. I thought it strange, but when I clicked any entry they would still work and the system would boot up Lubuntu. 


I didn't question it anymore until yesterday when I tried to boot to Lubuntu after having installed Windows 10 Pro on my computer. I reformatted the hard drive using gparted and installed Win 10 Pro and it was running fine. My Lubuntu flash drive was acting buggy so I reformatted it and reinstalled Lubuntu 18.04 on it. I went thru all the usual steps to install Lubuntu on a flash drive and the disc prompted me to restart to continue using the new opsys. When I restarted I still saw the 4 ubuntu entries below the Windows boot entry in the boot menu. I selected ubuntu to boot to my flash drive and for some reason every time I tried it wouldn't boot Lubuntu from my pen drive, but would take me to Windows. No matter which of the 4 ubuntu entries I selected they all did the same thing going to the Windows startup screen and not booting to Lubuntu. This never happened in Windows 7.


I tried the Linux Boot Repair Disc and it said it repaired the boot up problem successfully, but it wouldn't let me connect to the other computer drives to save the log it made. And the problem wasn't fixed by the repair disc. After using it the computer still boots to Win 10 even when I select ubuntu in the menu. 


Does anyone know how I can fix this problem where I can once again boot to linux from my boot menu like before? And can anyone explain why there would be 4 ubuntu entries in the boot menu? If it helps to know this I can still boot from my dvd or cd roms (ie the aforementioned Linux Boot Repair Disc) as they don't go to Windows. Thanks for any help you can provide. ;)

---

### Post by westie457 on 2019-04-20
Welcome to the Forum.

We could make some guesses to what is wrong however that is all they will be.
Much better to see details for more informed suggestions.

Boot using the Repair disc and only click the option to create a 'Boot Info Report'.
A link will be generated which you can post here so we can check the situation.

---

### Post by de3ik on 2019-04-20
[                                                      ]("https://ubuntuforums.org/member.php?u=970779")
Thanks westie457 for replying and I appreciate the welcome to the forum. :)

I use a boot repair disc called Boot-Repair-Disk at this link here: [https://sourceforge.net/p/boot-repair-cd/home/Home/](https://sourceforge.net/p/boot-repair-cd/home/Home/). I use the 64 bit version. Are you referring to another boot repair disk? I'm asking because when I checked only the option for Boot Info it didn't call it 'Boot Info Report' and it didn't generate a link, but only a text log of what it found called Boot-Info_2019-04-20__16h50.txt. Sorry that I have no link to post, but just this from the log.

 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.
 => Windows 7/8/2012 is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       1565495295 sectors, but according to the info from 
                       fdisk, it has 2639237119 sectors.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sde1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

sde2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  According to the info in the boot sector, sde2 has 
                       2742886399 sectors, but according to the info from 
                       fdisk, it has 5964111871 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,026,047     1,024,000   7 NTFS / exFAT / HPFS
/dev/sda2           1,026,048   976,771,071   975,745,024   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3000.6 GB, 3000558944256 bytes
255 heads, 63 sectors/track, 364797 cylinders, total 5860466688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048 2,639,239,167 2,639,237,120 Data partition (Windows/Linux)

Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 63.5 GB, 63518539776 bytes
255 heads, 63 sectors/track, 7722 cylinders, total 124059648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048   124,057,599   124,055,552  83 Linux


Drive: sde _____________________________________________________________________

Disk /dev/sde: 8001.6 GB, 8001563221504 bytes
256 heads, 63 sectors/track, 969001 cylinders, total 15628053167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sde1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sde2         264,192 5,964,376,063 5,964,111,872 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        70EE0AEBEE0AAA04                       ntfs       System Reserved
/dev/sda2        0CAE164FAE1631A6                       ntfs       
/dev/sdb1        AE4809BB48098377                       ntfs       WD MPP 3TB
/dev/sdd1        9ea198e9-02cd-4652-bb31-b8afe0103a8e   ext4       
/dev/sde2        848C75C68C75B372                       ntfs       SGB 8TB
/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit
/dev/zram0       b06d25d6-1b53-435a-a8d3-e63288822c84   swap       
/dev/zram1       f0f521e7-d549-40ee-9ff9-406cb9a1439d   swap       
/dev/zram2       4d8399ef-bc83-4cc7-b154-f4a3402194cf   swap       
/dev/zram3       8a11dcea-e7c7-47d3-aa02-6c2932385f98   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Apr 20 16:51 ata-Hitachi_HDS721050CLA362_JP1570HJ1SPBKK -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 20 16:52 ata-Hitachi_HDS721050CLA362_JP1570HJ1SPBKK-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 20 16:52 ata-Hitachi_HDS721050CLA362_JP1570HJ1SPBKK-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Apr 20 16:51 ata-ST8000DM004-2CX188_WCT01G5T -> ../../sde
lrwxrwxrwx 1 root root 10 Apr 20 16:49 ata-ST8000DM004-2CX188_WCT01G5T-part1 -> ../../sde1
lrwxrwxrwx 1 root root 10 Apr 20 16:52 ata-ST8000DM004-2CX188_WCT01G5T-part2 -> ../../sde2
lrwxrwxrwx 1 root root  9 Apr 20 16:49 ata-hp_DVD_RW_AD-7250H5_1476371L11 -> ../../sr0
lrwxrwxrwx 1 root root  9 Apr 20 16:49 usb-Generic_ATA_ATAPI_Device_20170421-0:0 -> ../../sdc
lrwxrwxrwx 1 root root  9 Apr 20 16:49 usb-HL-DT-ST_DVDRAM_GP50NB40_KX3Z9NJ4413-0:0 -> ../../sr1
lrwxrwxrwx 1 root root  9 Apr 20 16:51 usb-WD_My_Passport_25E2_57583331443735485A555444-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Apr 20 16:52 usb-WD_My_Passport_25E2_57583331443735485A555444-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Apr 20 16:51 usb-Walgreen_Infinitive_4C530001200427112273-0:0 -> ../../sdd
lrwxrwxrwx 1 root root 10 Apr 20 16:49 usb-Walgreen_Infinitive_4C530001200427112273-0:0-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 Apr 20 16:51 wwn-0x5000c500aa1da0bf -> ../../sde
lrwxrwxrwx 1 root root 10 Apr 20 16:49 wwn-0x5000c500aa1da0bf-part1 -> ../../sde1
lrwxrwxrwx 1 root root 10 Apr 20 16:52 wwn-0x5000c500aa1da0bf-part2 -> ../../sde2
lrwxrwxrwx 1 root root  9 Apr 20 16:51 wwn-0x5000cca377d8dc45 -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 20 16:52 wwn-0x5000cca377d8dc45-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 20 16:52 wwn-0x5000cca377d8dc45-part2 -> ../../sda2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/2978/mounts) leaked on lvs invocation. Parent PID 10851: bash
File descriptor 63 (pipe:[26491]) leaked on lvs invocation. Parent PID 10851: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2019-04-20__16h50 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/2978/mounts) leaked on lvs invocation. Parent PID 4637: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
Unmount sdb1 from /media/lubuntu/WD MPP 3TB to avoid space incompatibilities
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

mount /dev/sdd1 : Error code 32
mount -r /dev/sdd1 /mnt/boot-sav/sdd1
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

mount -r /dev/sdd1 : Error code 32
Unmount sde2 from /media/lubuntu/SGB 8TB to avoid space incompatibilities

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda1:Windows Recovery Environment (loader):Windows:chain
/dev/sdd1:Ubuntu 18.04.1 LTS (18.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="System Reserved" UUID="70EE0AEBEE0AAA04" TYPE="ntfs"
/dev/sda2: UUID="0CAE164FAE1631A6" TYPE="ntfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sdb1: LABEL="WD MPP 3TB" UUID="AE4809BB48098377" TYPE="ntfs"
/dev/sdd1: UUID="9ea198e9-02cd-4652-bb31-b8afe0103a8e" TYPE="ext4"
/dev/sde2: LABEL="SGB 8TB" UUID="848C75C68C75B372" TYPE="ntfs"
/dev/zram0: UUID="b06d25d6-1b53-435a-a8d3-e63288822c84" TYPE="swap"
/dev/zram1: UUID="f0f521e7-d549-40ee-9ff9-406cb9a1439d" TYPE="swap"
/dev/zram2: UUID="4d8399ef-bc83-4cc7-b154-f4a3402194cf" TYPE="swap"
/dev/zram3: UUID="8a11dcea-e7c7-47d3-aa02-6c2932385f98" TYPE="swap"


2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

mount /dev/sdd1 : Error code 32
mount -r /dev/sdd1 /mnt/boot-sav/sdd1
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

mount -r /dev/sdd1 : Error code 32
Windows not detected by os-prober on sda2.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.

=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb1.
sdd1    : sdd,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdd1.
sde2    : sde,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sde2.

sda    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdb    : GPT,    no-BIOS_boot,    has-no-EFIpart,     usb-disk,    no-os,    2048 sectors * 512 bytes
sdd    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     usb-disk,    has-os,    2048 sectors * 512 bytes
sde    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    no-os,    34 sectors * 512 bytes


=================== parted -l:

                                                                            Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Model: ATA Hitachi HDS72105 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Model: WD My Passport 25E2 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name         Flags
1      1049kB  3001GB  3001GB  ntfs         My Passport  msftdata


Model: Walgreen Infinitive (scsi)
Disk /dev/sdd: 63.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  63.5GB  63.5GB  primary  ext4         boot


Model: Seagate Backup+ Hub BK (scsi)
Disk /dev/sde: 8002GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
2      135MB   8002GB  8001GB  ntfs         Basic data partition          msftdata


                                                                            Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
                                                                            Error: /dev/sr0: unrecognised disk label

                                                                            Error: /dev/zram0: unrecognised disk label

                                                                            Error: /dev/zram1: unrecognised disk label

                                                                            Error: /dev/zram2: unrecognised disk label

                                                                            Error: /dev/zram3: unrecognised disk label

=================== parted -lm:

                                                                            Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
BYT;
/dev/sda:500GB:scsi:512:512:gpt:ATA Hitachi HDS72105;

BYT;
/dev/sdb:3001GB:scsi:512:4096:gpt:WD My Passport 25E2;
1:1049kB:3001GB:3001GB:ntfs:My Passport:msftdata;

BYT;
/dev/sdd:63.5GB:scsi:512:512:msdos:Walgreen Infinitive;
1:1049kB:63.5GB:63.5GB:ext4::boot;

BYT;
/dev/sde:8002GB:scsi:512:4096:gpt:Seagate Backup+ Hub BK;
1:17.4kB:134MB:134MB::Microsoft reserved partition:msftres;
2:135MB:8002GB:8001GB:ntfs:Basic data partition:msftdata;

                                                                            Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
                                                                            Error: /dev/sr0: unrecognised disk label

                                                                            Error: /dev/zram0: unrecognised disk label

                                                                            Error: /dev/zram1: unrecognised disk label

                                                                            Error: /dev/zram2: unrecognised disk label

                                                                            Error: /dev/zram3: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde2 on /mnt/boot-sav/sde2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sde1 sde2 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sdc sdd sdd1 sde sde1 sde2 sg0 sg1 sg2 sg3 sg4 sg5 sg6 sg7 shm snapshot snd sr0 sr1 stderr stdin stdout tpm0 uhid uinput urandom vga_arbiter vhci vhost-net watchdog watchdog0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 9f 0f 00 00 00 00 00  |................|
00000030  aa a6 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  04 aa 0a ee eb 0a ee 70  |...............p|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 0f 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff af 28 3a 00 00 00 00  |..........(:....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  a6 31 16 ae 4f 16 ae 0c  |.........1..O...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 8f 4f 5d 01 00 00 00  |..........O]....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  77 83 09 48 bb 09 48 ae  |........w..H..H.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sde2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 04 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 1f 7d a3 03 00 00 00  |..........}.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  72 b3 75 8c c6 75 8c 84  |........r.u..u..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.4G  8.3M  3.4G   1% /
udev           devtmpfs   3.4G   12K  3.4G   1% /dev
tmpfs          tmpfs      687M  1.2M  686M   1% /run
/dev/sr0       iso9660    614M  614M     0 100% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.4G  8.0K  3.4G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.4G     0  3.4G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1      fuseblk    500M  323M  178M  65% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    466G   31G  435G   7% /mnt/boot-sav/sda2
/dev/sdb1      fuseblk    2.8T  657G  2.1T  24% /mnt/boot-sav/sdb1
/dev/sde2      fuseblk    7.3T  6.9T  411G  95% /mnt/boot-sav/sde2

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x130af11a

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1026047      512000    7  HPFS/NTFS/exFAT
/dev/sda2         1026048   976771071   487872512    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 3000.6 GB, 3000558944256 bytes
255 heads, 63 sectors/track, 364797 cylinders, total 5860466688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x16f2a91f

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdd: 63.5 GB, 63518539776 bytes
255 heads, 63 sectors/track, 7722 cylinders, total 124059648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8855f0c4

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048   124057599    62027776   83  Linux

Disk /dev/sde: 8001.6 GB, 8001563221504 bytes
256 heads, 63 sectors/track, 969001 cylinders, total 15628053167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9fc33c81

Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.




=================== Default settings of Boot Repair
The default repair of the Boot-Repair utility would restore the [(generic mbr)] MBR in sdd, and make it boot on sdd1.
Additional repair would be performed: unhide-bootmenu-10s repair-filesystems  fix-windows-boot


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2019-04-21
Please use code tags if longer text or terminal output. 
Easy to add with Forum's advanced editor and # icon.

Better to use Ubuntu live installer and add Boot-Repair (Second Option). Note you ran a very old copy. And use Create BootInfo Summary Report which will give you a clickable pastebin link to post.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You are showing Windows in BIOS/MBR boot mode on sda.
But have other drives and the 3TB drive has to be the new gpt partitioning.
The old Boot-Repair has the old fdisk that did not support gpt. 

You show no grub installed to sdd and partitions may be corrupted. Probably easier to reinstall at this point.
But only use Something Else and be sure to install grub bootloader to same drive as you install Ubuntu.
 
Also your HP is probably early version UEFI which also had issues. If HP has UEFI update you need to update UEFI whether installing Ubuntu or not.

---

### Post by de3ik on 2019-04-21
Sorry about not using code tags. I didn't know how to do that. I appreciate you informing me.

I'm not clear about this. Do you mean I have to reinstall both my Windows 10 on my C Drive and my Lubuntu on my flash drive? Or do I just reinstall Lubuntu only?

When you say to install grub bootloader to the same drive as ubuntu I selected my flash drive as the drive I wanted to install Lubuntu to. That's all I did and it worked before. I am not clear about how to install grub. Is there another step I need to follow besides selecting my flash drive as the drive to install Lubuntu on?

---

### Post by yancek on 2019-04-21
First off, oldfred is suggesting you get a more current boot repair and run that with the Create BootInfo Summary.  Go to the site at the first link in his post above, use the 2nd option explained on the page.

Install Lubuntu to the sdd drive you should use the Something Else option and select /dev/sdd as the device for bootloader installation during the install.  You need to use the Something Else option so that you can tell the installer what you want, you have too many drives to do any type of auto-install.  That is if the 63.5GB drive show in your output as sdd is the drive you want Lubuntu on.  Boot repair shows Syslinux boot code in the MBR of sdd, right at the top of the bootinfoscript.

---

### Post by de3ik on 2019-04-22
Here is the link from the Bootinfo Summary: [http://paste.ubuntu.com/p/pMPF2CJcFM/](http://paste.ubuntu.com/p/pMPF2CJcFM/)

I reinstalled Windows 10 and Lubuntu, but Gparted gave a message a message about something being wrong with the GPT table or said it was missing. I can't remember the message, but I was wondering if maybe that also had something to do with Lubuntu not booting up on my flash drive. In Gparted my C drive with windows on it is just all grey and unallocated. This wasn't the case when I had Windows 7 pro on this computer in the past. Windows 10 is definitely on the computer and I can use it so I can't understand why it would show as unallocated.

---

### Post by oldrocker99 on 2019-04-22
Although others have had no trouble with UEFI, my own experience has been that booting a USB in UEFI mode will result in grub not being installed, leaving an unbootable computer. Installing in Legacy mode always works for me.

---

### Post by de3ik on 2019-04-22
> **oldrocker99 said:**
> Although others have had no trouble with UEFI, my own experience has been that booting a USB in UEFI mode will result in grub not being installed, leaving an unbootable computer. Installing in Legacy mode always works for me.

How do you install in Legacy mode? The computer always had this UEFI mode from what I remember even when I had Windows 7 pro on it in the past. And the usb did boot during that time. It's only when just installed Win 10 pro recently that this happened. Do you think it's more about the partition being corrupted? Gparted did say there was problem with the GPT.

EDIT:

To the moderator oldfred who commented about updating the UEFI bios, I checked this link which said they were making a Bios update: [https://support.hp.com/sg-en/document/c02872146](https://support.hp.com/sg-en/document/c02872146). It mentioned J01 vs 2.06. When I boot up my computer it says 2.06 at the bottom of the screen so am I correct to believe the Bios may  have already been updated? Just in case this wasn't correct I went to HP's support site for my computer and it has no software and drivers listed for my Windows 10 pro operating system. [https://support.hp.com/us-en/drivers/selfservice/hp-compaq-8200-elite-convertible-minitower-pc/5037949](https://support.hp.com/us-en/drivers/selfservice/hp-compaq-8200-elite-convertible-minitower-pc/5037949)  When I input Windows 8 64 bit it listed [TABLE="class: table, width: 100%"]
[TR="class: first-row"]
[TD="class: col-lg-7"]**Business Desktops BIOS Utilities**

[/TD]
[TD="class: col-lg-3 version"]5.03 Rev.B[/TD]
[TD="class: col-lg-3 size"]0.4 MB[/TD]
[TD="class: col-lg-3 date"]Jun 5, 2014 for the computer.


[/TD]
[/TR]
[/TABLE]
I don't run Windows 8 or even Windows 7 anymore on this computer so should I be hesitant to try this Bios? I've heard Bios issues can make a computer not turn on if there are problems with it.

---

### Post by yancek on 2019-04-22
Your boot repair shows you have 5 physical drives of varying sizes attached with sda being windows and sdf being Lubuntu.  The others are just data drives???

> How do you install in Legacy mode? 

The way you actually did the install.  Both windows and Lubuntu are in Legacy mode.  One problem might be that you have multiple Legacy drives and multiple GPT drives.  Shouldn't affect booting.  If you had windows installed on one of the GPT drives (which according to boot repair you do NOT) you would need UEFI.

> The computer always had this UEFI mode]

Just because it has UEFI capability doesn't mean you must install UEFI so seeing that in the BIOS doesn't mean anything. 
Having multiple boot entries for Lubuntu in Grub is pretty standard, also for any Ubuntu and most Linux systems.
Have you set the  Lubuntu drive (64GB drive listed as sdf) to first boot priority in the BIOS setup.  Boot repair shows you have Grub installed to the MBR of that drive and you have a grub.cfg file on the first partition (sdf1) where Lubuntu is installed with correct entries for Lubuntu and windows on sda1.  What, if anything works now?  Setting sdf to first boot priority should allow booting both.

---

### Post by de3ik on 2019-04-22
> [COLOR=#000000]Your boot repair shows you have 5 physical drives of varying sizes attached with sda being windows and sdf being Lubuntu. The others are just data drives???[/COLOR]


I have these drives currently connected to my computer. The 500 gb C drive Windows is on, The 64 gb flash drive lubuntu is on, A 3tb portable drive, An 8tb Seagate drive I use to store my files and another 8tb seagate drive I use to back those same files up. 

I tried your suggestion to make the lubuntu flash drive first boot priority in the Bios. In the bios it showed the UEFI as having a USB hard drive option which I put first, followed by a USB floppy/CD. I didn't see an exact option for the flash drive. The legacy had an option for USB floppy/CD which was first. This didn't work when I tried to boot from my flash drive. It still went straight to Windows.

However I remember on a forum somewhere someone saying they couldn't boot from their USB stick and had to toggle the Bios settings, one of which was disabling the UEFI boot in the Bios. I went back to the bios and disabled the UEFI and when I rebooted I tried to select my flash drive called Walgreens Infinitive from the boot menu under Legacy settings. It worked! Instead of going to Windows it finally went to Lubuntu on my flash drive. I'm glad it worked, but does anyone know why this would be? Is that just the way Linux works on some Windows 10 computers? Or is it some kind of quirk with this Bios do you think? 

I'm still concerned about my C drive having the GPT issue mentioned in GParted as it never had this before. Oldfred mentioned corruption and I don't want that to harm me down the road on my C Drive. Is this something concern myself with since the computer seems to working ok? Would getting that issue fixed allow me to reset the BIOS settings to their defaults (like they were with Windows 7 pro before on my computer) and allow me to boot to Lubuntu normally?

---

### Post by oldrocker99 on 2019-04-22
```
How do you install in Legacy mode? The computer always had this UEFI mode from what I remember even when I had Windows 7 pro on it in the past. 
And the usb did boot during that time. It's only when just installed Win 10 pro recently that this happened. Do you think it's more about the partition being corrupted? 
Gparted did say there was problem with the GPT.
```

Every mobo I have used (4 in the past 5 years) with UEFI also have a legacy mode. It is in there, almost certainly.

---

### Post by yancek on 2019-04-23
> but does anyone know why this would be? Is that just the way Linux works on some Windows 10 computers? Or is it some kind of quirk with this Bios do you think?

It's the motherboard manufacturer.  If you had a number of computers from various manufacturers, you would go into the BIOS and see there is very little consistency and options that are available on some computers are not available on others.  On my laptop, I can see no option to disable EFI but can enable/disable Legacy and boot/install a Legacy system on a Legacy drive.

Setting the USB (Lubuntu drive sdf) to first boot priority under the UEFI option would not have any effect as it is not installed in UEFI mode.

Your windows is installed in Legacy mode rather than UEFI.  With GPT partitioning, for windows you need an EFI install but your install is not on a GPT partition so the question is what problems (if any) will you have from a Legacy/MBR system with your windows OS trying to access data on a GPT system?  If you have specific errors, you might post them here but the best source would probably be the support forums for microsoft or a windows forum as this is a limitation with the windows OS.

---

### Post by oldfred on 2019-04-23
You typically want the newest UEFI/BIOS that the vendor offers. Not really related to which operating system you have but new versions support newer features or correct issues. 

Typically it is UEFI on/off or Legacy on/off.
My old BIOS system booted flash drives as another hard drive, not as any USB device.
My UEFI system only booted in BIOS mode, even with UEFI or BIOS settings. Only setting that worked for UEFI boot was UEFI only.
So every vendor implements UEFI somewhat differently.

You have to have gpt for any drive over two TiB.
Windows install in BIOS boot mode to a gpt drive incorrectly converts drive to MBR. It leaves backup gpt partition table which Windows then does not see, but Linux tools then see both MBR & gpt and get confused and typically want to totally redo drive.
Windows only installs in BIOS boot mode to MBR partitioned drives or only in UEFI boot mode from gpt partitioned drives. Ubuntu can be in either mode with either partitioning, but UEFI really wants & recommends gpt for UEFI boot.

---

### Post by de3ik on 2019-04-23
I'm trying to understand, but I think I may be unclear. Sorry for my limited knowledge as I am a novice. Perhaps if anyone can answer this question it might help me to better know what to do next. 

If it helps you to know when I had Windows 7 pro on the computer I went into the gparted tool and deleted everything on the c drive (I guess that means I deleted the partitions or something) before installing Windows 10 pro on this computer. I did that because another computer I had Windows 10 home on had an issue with not being able to boot Windows 10 and I couldn't reinstall Windows. The only thing that worked to reinstall Windows was to delete the whole C drive in gparted on that computer and install on the empty space on the hard drive after that area had been deleted. I didn't want anything to happen on my current computer so I thought deleting the C drive in gparted would be a solution. 

Do you think I accidentally deleted this gpt partition in Gparted?  oldfred said there is a backup gpt partition table. Does this need to be restored or something? I'm asking because since  I can finally boot to Lubuntu on my usb via disabling the uefi in the bios I guess I won't have to worry about reenabling it since I can boot to both Windows and Linux now as I wanted to even though in a different way than I expected. I don't want this corruption or deleted gpt backup partition issue to be a problem that could damage the computer. Will it do any harm to the computer, operating systems or files in anyway where I would need to fix this? Will it lessen the life of the computer? I don't have a problem with leaving the computer as is if this issue won't be a problem in the future. But if it is I would like to fix it. Please let me know what to do. Yancek said if I have specific errors in the system to post them here or to a Windows/microsoft forum but I can't think of any errors I've had since I installed Windows 10 and didn't even know there was any issue with partition corruption until oldfred addressed it originally. Does this mean the system is fine and I don't have to worry about this partition gpt mbr issue?

---

### Post by oldfred on 2019-04-23
Since UEFI system, how you boot install media UEFI or BIOS is then how it installs.
Most but not all Windows 7 installs were BIOS/MBR, but a few were UEFI.
So when you booted Windows 10 installer and it did not want to install, may have been because you booted in a mode that did not match drive partitioning.
And if drive was gpt (Maybe Windows 7 was UEFI?) then trying to install Windows 10 in BIOS boot mode may complain. And then if you removed the Windows install, it would install but convert gpt drive (required with Windows in UEFI) to MBR. 
If you want to keep Windows in BIOS mode, but have backup gpt partition it is ok for Windows it seems, except your Linux tools will complain. You can remove backup gpt table if desired. If you want gpt, you have to reinstall Windows in UEFI boot mode. There are some advantages to gpt & UEFI over the now 35 year old BIOS & MBR, but if system works ok, no need to change.

---

### Post by de3ik on 2019-04-24
So that I understand for my future reference...

1. How do I remove the backup gpt table?

2. How do I reinstall Windows in UEFI boot mode to get the gpt back? The only way I knew to reinstall is from my disc by booting up going to the start menu and booting from the dvd rom there.

3. What are the advantages to having gpt and UEFI over bios and mbr? Would these advantages be needed or worth it for a user like myself? I don't consider myself a power user as all I do is browse the internet/email, download files, make word docs and notepads and burn DVDs with ConvertXtoDVD. I also watch videos on my media player and youtube, occasionally boot to Lubuntu to do what I do in Windows except I don't use convertxtodvd there (I use Xfburn) and copy files to my hard drives. This is my mother's computer and she lets me use it. She does the same things I do with the exception of using ConvertXtoDVD and using Lubuntu.

---

### Post by oldfred on 2019-04-24
If you have Windows installed, it probably is not worth reinstalling. Windows takes forever to install.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

I have been using gpt since about 2010 for BIOS boot and then every new or totally reformatted drive including larger flash drives was gpt partitioned.
The only reason for MBR is if you have Windows in BIOS boot mode as it has to be MBR partitioned.

How you boot install media UEFI or BIOS is then how it installs for both Windows & Ubuntu. The old Windows 7 DVD was BIOS only but could be converted by copying to a flash drive & some files moved/renamed. Newer Windows 7 update & all later versions will boot how you specify from UEFI boot menu.
You may have to turn on/off Secure Boot, or a setting on allow USB boot. BIOS only boots if Secure boot is off. UEFI can be either on/off.
Most UEFI show "UEFI:flash" or "flash"  which then is the BIOS boot, where flash is name or label of flash drive. Mine says pmap which is not name of flash drive.
 
      
 Remove old parts of gpt, gdisk now standard with live installer & actual installs.
[http://ubuntuforums.org/showpost.php?p=10022223&postcount=34](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34)

---

### Post by de3ik on 2019-04-25
I'm sorry that I am not understanding this properly. You said: 

> [COLOR=#000000]How you boot install media UEFI or BIOS is then how it installs for both Windows & Ubuntu.[/COLOR]

I am still not clear on how to boot UEFI to reinstall this GPT partition back on my drive. When I booted up my computer and went to the startup menu (Turn on the comp and then tap F9 to get to that menu) under UEFI it says Windows boot manager and Ubuntu (it says ubuntu 4 times there) only. There is no option to boot from a flash drive or DVD drive which is how I booted to install my Windows 7 USB drive and my Windows 10 DVD. Then for Legacy it gives several other options which include SATA 2 which is my computer's built in DVD drive where I booted my Windows 10 disc and one option for my Flash drive. So how do I boot from my DVD drive or flash drive in this UEFI mode when it's not listed under the UeFI menu? I appreciate you posting the benefits of UEFI and GPT and think it might be helpful for the future so I would like to see if I can reinstall the GPT if possible. Is there a step by step guide I can follow for that? Since my knowledge is limited it helps me to fix what I need to on the computer.

> Y[COLOR=#000000]ou may have to turn on/off Secure Boot, or a setting on allow USB boot. BIOS only boots if Secure boot is off. UEFI can be either on/off.[/COLOR]

For some reason on my computer there is nothing showing to turn off the Secure boot or turn it on. I followed the steps here at these links for my HP desktop: 

[https://support.hp.com/us-en/document/c04784866](https://support.hp.com/us-en/document/c04784866)

[https://www.appgeeker.com/recovery/disable-uefi-secure-boot-in-windows-10.html](https://www.appgeeker.com/recovery/disable-uefi-secure-boot-in-windows-10.html)


There was no UEFI Firmware Settings option in the Troubleshoot, Advanced Settings when I followed the appgeeker guide. When following the hp guide there is no Secure Boot Configuration listed in the bios at all. So how would you suggest turning on/off secure boot?

I appreciate everyone's help on this. I may be coming along slowly but it's helping me to learn. Thanks for all who are chiming in on this thread.

---

### Post by oldfred on 2019-04-25
Your HP support link shows the Secure boot setting on the System configuration setting screen.
My system has "Windows" and "Other" but says if Windows 7 you must use "Other". Windows 7 does not support Secure Boot.

My systems all show UEFI boot of USB devices under UEFI. But I have to turn on full entablement of USB devices. Otherwise they are just data drives.
But if flash drive not correctly configured, then UEFI will not see it to boot it.

---

### Post by de3ik on 2019-04-26
> Your HP support link shows the Secure boot setting on the System configuration setting screen.
My system has "Windows" and "Other" but says if Windows 7 you must use "Other". Windows 7 does not support Secure Boot.


I am not currently using Windows 7 anymore. I am using Windows 10 pro now. I thought Win 10 supported Secure Boot.  In my bios in the boot order area you can disable or enable either the UEFI or Legacy boot menu. Disabling UEFI at the time allowed me to boot my lubuntu flash drive. Is this option how this computer disables or enables secure boot? Or does this mean something else?

> My systems all show UEFI boot of USB devices under UEFI. But I have to  turn on full entablement of USB devices. Otherwise they are just data  drives.
But if flash drive not correctly configured, then UEFI will not see it to boot it.                  

How do I configure the flash drive properly so that UEFI will see it and boot ?

Maybe this info will help other people having a similar problem and especially if they are newbies. After reading what you posted about the GPT and UEFI I did some investigating and then tried to reinstall Win10 pro as in UEFI mode with GPT partition. I reenabled UEFI in the bios and put in my Win10 disk. I booted up the startup menu by repeatedly clicking F9 and saw my DVD player (it was named HP ****** in the UEFI menu) and booted the disk from it. I followed the instructions at this vid to convert my C drive to GPT before installing Win10: [https://www.youtube.com/watch?v=nBl3aGgkVJU](https://www.youtube.com/watch?v=nBl3aGgkVJU) (Please note to backup your files before following that vid since the process wipes your hard drive.

Then I installed Win10 on my now clean newly GPT partitioned C drive. There were no install errors and once I got to Windows I opened command prompt as an administrator and typed diskpart and then hit enter. Then I typed list disk and hit enter. The C drive showed as being GPT with an asterisk whereas before it wasn't showing that confirmation. Gparted no longer complained about the GPT issue on the C drive or showed that drive as being unallocated like I mentioned in my earlier posts.

However with Lubuntu when I reinstalled it, I formatted my 64 gb flash drive with gparted while in the Lubuntu live disk and then created a new partition table that was gpt for that disk. In the Lubuntu program called "Disks" my flash drive went from being MBR to GPT. I had booted from my Lubuntu disc the same way I did for Windows in what I thought was UEFI mode, by selecting my DVD player from under the UEFI menu option in the bios startup menu. But after my reinstall when I checked my flash drive in the Disks program again it now shows as MBR again. The other disks I have all showed as GPT including my Win 10 C drive that formerly had the corruption issue. What did I do wrong? I thought the Lubuntu Usb drive would now be a GPT disc created in UEFI. Is this normal or do I have to fix this to get the GPT onto the Lubuntu drive?

EDIT: After my aforementioned reinstall of Lubuntu I no longer have to disable the UEFI in the bios and boot from my flash drive in Legacy as I mentioned in prior posts. When  booting into the bios startup menu and seeing Ubuntu under the UEFI menu I can boot my flash drive from there as I could before when I used Win 7 pro earlier as I mentioned in my original post. In fact I don't even have to go to the bios startup menu and boot there. The computer no longer goes straight to Windows but at startup shows a grub menu with Ubuntu and Windows boot manager listed where I can choose to boot either Win 10 pro or Lubuntu. Does this mean I did the reinstall correctly and how can I stop the grub menu from starting with the bootup? I preferred when Windows would boot up when I started the computer and the only way I could boot up Lubuntu was to go the bios startup menu and select Ubuntu from the UEFI menu.

---

### Post by yancek on 2019-04-26
> ow can I stop the grub menu from starting with the bootup? I preferred  when Windows would boot up when I started the computer and the only way I  could boot up Lubuntu was to go the bios startup menu and select Ubuntu  from the UEFI menu. 		

You can edit the /etc/default/grub file manually as root (using sudo) to set the windows entry in the boot menu first.  THis is explained in detail at the link below.  It is generally a good idea to have a timeout of several seconds so you have the option to change the system to boot from the menu.

The other option is to go into the BIOS Boot Options and change the priority from Ubuntu to windows boot manager.  THis must be done in the BIOS boot options and not from the Boot Options you generally see with the F9 key as that is only a one time change whereas the BIOS change is permanent, at least until manually changed again.

---

### Post by de3ik on 2019-04-26
> [COLOR=#000000]You can edit the /etc/default/grub file manually as root (using sudo) to set the windows entry in the boot menu first. THis is explained in detail at the link below. It is generally a good idea to have a timeout of several seconds so you have the option to change the system to boot from the menu.[/COLOR]


Thanks for letting me know but you forgot to put the link in your response. Could you post the link please?

> [COLOR=#000000]The other option is to go into the BIOS Boot Options and change the priority from Ubuntu to windows boot manager. THis must be done in the BIOS boot options and not from the Boot Options you generally see with the F9 key as that is only a one time change whereas the BIOS change is permanent, at least until manually changed again.[/COLOR]

It isn't allowing me to change the priority from Ubuntu to Windows boot manager for some reason. The boot order is only thing that shows anything about booting and that is just for the devices I can boot from (usb, dvd/cd, etc). Is there another setting I must change to access this? I really just wanted to get rid of the grub booting up and giving the option to boot either windows or lubuntu at the very beginning. This didn't happen when I had my flash drive created in Windows 7 pro a while back and only happened when I was dual booting Windows and lubuntu on another machine. I prefer just to go the bios startup menu after tapping F9 and select ubuntu from the Uefi menu. Is that possible to do or must I rely on grub booting up with the computer?

---

### Post by oldfred on 2019-04-26
You should always be able to select either Windows or Ubuntu from UEFI boot menu.  Grub only boots working Windows, and Windows sometimes will turn fast start up back on with updates and then grub will not boot it. Then you have to use UEFI boot menu to boot.

You also should be able to change boot order in UEFI settings, but sometimes it is a sub-menu under hard drive or UEFI settings. Try clicking on whatever your system shows, it may have a > or similar icon to show there is a sub-menu.

---

### Post by yancek on 2019-04-26
> Thanks for letting me know but you forgot to put the link in your response. Could you post the link please? 

[https://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/](https://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/)

Google it and you will find countless sites with the same info.

Not sure why you can't change the boot order in the BIOS.  On my HP notebook on boot, hit Esc key and get several options, F9 for boot options (this is a one time change) and F10 to access the BIOS and there go to System Configuration and there is a Boot Options entry on that page.  It should have a small arrow on the left, highlight Boot Options and hit the Enter key.  If you don't have these options on your HP you will just have to explore the BIOS or try googling for the manual online specifying your particular computer.

This is shown in the link you posted above(post 19) to the HP site

---

### Post by de3ik on 2019-04-27
> [COLOR=#000000]Google it and you will find countless sites with the same info.[/COLOR]

Thanks for the link. The reason why I ask here is because with my limited knowledge I have asked questions on Google that have returned sites that didn't even answer the question I was asking making me feel that I may not be explaining the question properly or understand my issue enough. I came to the forum hoping that people more experienced could help me since to be honest I really don't know what I'm doing and don't want to damage the computer by making a mistake.

> [COLOR=#000000]Not sure why you can't change the boot order in the BIOS. On my HP notebook on boot, hit Esc key and get several options, F9 for boot options (this is a one time change) and F10 to access the BIOS and there go to System Configuration and there is a Boot Options entry on that page. It should have a small arrow on the left, highlight Boot Options and hit the Enter key. If you don't have these options on your HP you will just have to explore the BIOS or try googling for the manual online specifying your particular computer.[/COLOR]

[COLOR=#000000]This is shown in the link you posted above(post 19) to the HP site[/COLOR]

Maybe I wasn't explaining it correctly. I can change the boot order in the Bios one time by clicking F9 or going straight to the main bios by clicking F10. I have explored the Bios thoroughly and ubuntu isn't listed there at all or in my boot order tab. It just gives me devices I can boot from listed under the UEFI and Legacy. Windows Boot manager is listed there, but not Ubuntu. What I really wanted to do was to stop the Grub from booting up at all when I started up my computer and only be able to select Lubuntu to from by clicking F9 and going to the boot options that you can change one time. Since no one knows how to do this and I couldn't find it on google I just used grub customizer which I found out about after you mentioned editing the grub file. Now windows comes before Ubuntu in the boot order on grub.


I tried to look on Google but didn't find the answer to my question as I had queried earlier in my post #21. I had asked:

[COLOR=#000000]However with Lubuntu when I reinstalled it, I formatted my 64 gb flash drive with gparted while in the Lubuntu live disk and then created a new partition table that was gpt for that disk. In the Lubuntu program called "Disks" my flash drive went from being MBR to GPT. I had booted from my Lubuntu disc the same way I did for Windows in what I thought was UEFI mode, by selecting my DVD player from under the UEFI menu option in the bios startup menu. But after my reinstall when I checked my flash drive in the Disks program again it now shows as MBR again. The other disks I have all showed as GPT including my Win 10 C drive that formerly had the corruption issue. What did I do wrong? I thought the Lubuntu Usb drive would now be a GPT disc created in UEFI. Is this normal or do I have to fix this to get the GPT onto the Lubuntu drive?

I am still not sure what to do with this issue. Lubuntu is running fine, but I will try to fix it if someone can kindly recommend a solution.[/COLOR]

---

