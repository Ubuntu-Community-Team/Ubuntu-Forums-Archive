---
title: "Can not boot into Ubuntu 11.04 due to not proper shutdown"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by Tetramailbox on 2012-11-09
Hello all. 

I'm newbie Ubuntu 11.04 user 

I already using Ubuntu 11.04 (that is installed using WUBI), and some how I don't shutdown it properly so I can not boot into Ubuntu again and 
I got the following message    

[I]"GNU GRUB ver 1.99 v rc1-13ubuntu3 Minimal bash-like editing is supported..............etc"

[/I] I already try to fix it using "Boot-Repair" and have not succeed  I got the Boot Info script as follows: 

*************************************************************************

```
      Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info September 18th 2012]   ============================= Boot Info Summary: ===============================   =>  is installed in the MBR of /dev/sda.  sda1: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files:        /bootmgr /Boot/BCD  sda2: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows 7     Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr  sda3: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files:          sda4: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr                         /ubuntu/disks/root.disk /ubuntu/disks/swap.disk  sda4/Wubi: _____________________________________________________________________      File system:            Boot sector type:  Unknown     Boot sector info:      Mounting failed:   mount: unknown filesystem type ''  ============================ Drive/Partition Info: =============================  Drive: sda _____________________________________________________________________  Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS /dev/sda2             206,848   204,802,047   204,595,200   7 NTFS / exFAT / HPFS /dev/sda3         204,802,048   593,922,047   389,120,000   7 NTFS / exFAT / HPFS /dev/sda4         593,922,048   976,771,071   382,849,024   7 NTFS / exFAT / HPFS   "blkid" output: ________________________________________________________________  Device           UUID                                   TYPE       LABEL  /dev/loop0                                              squashfs    /dev/sda1        A490A4B290A48C7C                       ntfs       System Reserved /dev/sda2        E894B6C394B69412                       ntfs        /dev/sda3        FE40B4BE40B47F49                       ntfs        /dev/sda4        8608C3EE08C3DAF7                       ntfs         ================================ Mount points: =================================  Device           Mount_Point              Type       Options  /dev/sr0         /live/image              iso9660    (ro,noatime)   ======================== Unknown MBRs/Boot Sectors/etc: ========================  Unknown BootLoader on sda4/Wubi  00000000  7f 45 4c 46 01 01 01 00  00 00 00 00 00 00 00 00  |.ELF............| 00000010  01 00 03 00 01 00 00 00  00 00 00 00 00 00 00 00  |................| 00000020  88 03 00 00 00 00 00 00  34 00 00 00 00 00 28 00  |........4.....(.| 00000030  0b 00 08 00 55 ba c0 00  00 00 89 e5 83 ec 10 6a  |....U..........j| 00000040  00 b9 00 00 00 00 68 0f  00 00 00 b8 05 00 00 00  |......h.........| 00000050  e8 fc ff ff ff a3 00 00  00 00 58 5a c9 c3 55 31  |..........XZ..U1| 00000060  c0 89 e5 83 ec 08 c9 eb  cb 55 89 e5 57 56 53 83  |.........U..WVS.| 00000070  ec 1c 8b 41 08 8b 5d 08  8b 75 0c 8b 7d 14 8d 50  |...A..]..u..}..P| 00000080  01 85 c0 89 51 08 74 16  83 ec 0c 68 23 00 00 00  |....Q.t....h#...| 00000090  89 4d e4 e8 fc ff ff ff  8b 4d e4 83 c4 10 50 2b  |.M.......M....P+| 000000a0  19 1b 71 04 56 53 68 25  00 00 00 e8 fc ff ff ff  |..q.VSh%........| 000000b0  83 c4 10 83 7d 10 00 74  12 53 53 ff 75 10 68 2a  |....}..t.SS.u.h*| 000000c0  00 00 00 e8 fc ff ff ff  83 c4 10 83 7d 18 00 75  |............}..u| 000000d0  04 85 ff 74 15 8b 45 18  51 01 f8 50 57 68 2e 00  |...t..E.Q..PWh..| 000000e0  00 00 e8 fc ff ff ff 83  c4 10 8d 65 f4 5b 5e 5f  |...........e.[^_| 000000f0  5d c2 14 00 55 b8 c4 01  00 00 89 e5 56 53 8d 75  |]...U.......VS.u| 00000100  f8 81 ec 20 02 00 00 29  f0 85 d2 8d 5d d8 c6 45  |... ...)....]..E| 00000110  ec b9 89 5d ed c6 45 f1  e9 89 45 f2 c7 45 e4 00  |...]..E...E..E..| 00000120  00 00 00 c7 45 e8 00 00  00 00 c7 45 e0 00 00 00  |....E......E....| 00000130  00 c7 45 d8 00 00 00 00  c7 45 dc 00 00 00 00 7f  |..E......E......| 00000140  0b 51 51 68 36 00 00 00  6a 12 eb 32 8b 01 c7 05  |.QQh6...j..2....| 00000150  00 00 00 00 00 00 00 00  c7 05 04 00 00 00 00 00  |................| 00000160  00 00 e8 fc ff ff ff 85  c0 89 c3 74 7d 8b 00 8b  |...........t}...| 00000170  00 85 c0 75 13 52 52 68  48 00 00 00 6a 0d e8 fc  |...u.RRhH...j...| 00000180  ff ff ff 83 c4 10 eb 67  8b 40 14 31 d2 31 c9 eb  |.......g.@.1.1..| 00000190  09 03 50 04 13 48 08 8b  40 20 85 c0 75 f3 8d 45  |..P..H..@ ..u..E| 000001a0  ec 89 55 d8 8d b5 d8 fd  ff ff 89 4d dc 89 43 20  |..U........M..C | 000001b0  b9 00 02 00 00 89 f2 89  d8 e8 fc ff ff ff 85 c0  |................| 000001c0  7f ee 8b 45 e8 85 c0 74  1a 83 ec 0c 31 d2 6a 00  |...E...t....1.j.| 000001d0  6a 00 50 8b 45 e4 52 8d  4d d8 50 e8 89 fe ff ff  |j.P.E.R.M.P.....| 000001e0  83 c4 0c 89 d8 e8 fc ff  ff ff a1 00 00 00 00 8d  |................| 000001f0  65 f8 5b 5e 5d c3 55 89  e5 57 56 53 89 cb 83 ec  |e.[^].U..WVS....| 00000200   =============================== StdErr Messages: ===============================    No volume groups found mdadm: No arrays found in config file or automatically  ADDITIONAL INFORMATION : =================== log of boot-repair 2012-11-09__23h06 =================== boot-repair version : 3.193-0ppa22~lucid boot-sav version : 3.193-0ppa39~lucid glade2script-gtk2 version : 0.0.1-0ppa4~lucid boot-sav-nonfree version : No volume groups found boot-repair is executed in live-session (Boot-Repair-Disk 18.07.2012, squeeze, Debian, i686) CPU op-mode(s):        32-bit, 64-bit initrd=/live/initrd.img boot=live config   quiet BOOT_IMAGE=/live/vmlinuz  =================== os-prober: /dev/sda1:Windows 7 (loader):Windows:chain  =================== blkid: /dev/sda1: LABEL="System Reserved" UUID="A490A4B290A48C7C" TYPE="ntfs" /dev/sda2: UUID="E894B6C394B69412" TYPE="ntfs" /dev/sda3: UUID="FE40B4BE40B47F49" TYPE="ntfs" /dev/sda4: UUID="8608C3EE08C3DAF7" TYPE="ntfs" /dev/loop0: TYPE="squashfs"   1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.  Windows not detected by os-prober on sda2. =================== No kernel in /mnt/boot-sav/sda4/boot: grub   There is Wubi inside sda4 =================== dmesg | grep EFI : This live-session is not EFI-compatible.   =================== PARTITIONS & DISKS: sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1. sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2. sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda3. sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda4.  sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes   =================== parted -l:  Model: ATA WDC WD5000BEVT-8 (scsi) Disk /dev/sda: 500GB Sector size (logical/physical): 512B/512B Partition Table: msdos  Number  Start   End    Size   Type     File system  Flags 1      1049kB  106MB  105MB  primary  ntfs         boot 2      106MB   105GB  105GB  primary  ntfs 3      105GB   304GB  199GB  primary  ntfs 4      304GB   500GB  196GB  primary  ntfs                                                                               Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.                                                                             Error: /dev/sr0: unrecognised disk label  =================== parted -lm:  BYT; /dev/sda:500GB:scsi:512:512:msdos:ATA WDC WD5000BEVT-8; 1:1049kB:106MB:105MB:ntfs::boot; 2:106MB:105GB:105GB:ntfs::; 3:105GB:304GB:199GB:ntfs::; 4:304GB:500GB:196GB:ntfs::;                                                                              Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.                                                                             Error: /dev/sr0: unrecognised disk label   =================== mount: aufs on / type aufs (rw) tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755) proc on /proc type proc (rw,noexec,nosuid,nodev) sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) udev on /dev type tmpfs (rw,mode=0755) tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev) devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620) /dev/sr0 on /live/image type iso9660 (ro,noatime) tmpfs on /live/cow type tmpfs (rw,noatime,mode=755) tmpfs on /live type tmpfs (rw,relatime) tmpfs on /tmp type tmpfs (rw,nosuid,nodev) fusectl on /sys/fs/fuse/connections type fusectl (rw) /dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096) /dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,allow_other,blksize=4096) /dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096) /dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,allow_other,blksize=4096)   =================== ls: /sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 size slaves stat subsystem trace uevent /sys/block/sr0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent /dev (filtered):  block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dvd dvdrw fd full fuse hpet initctl input kmsg log MAKEDEV md mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda3 sda4 sg0 sg1 shm snapshot snd sndstat sr0 stderr stdin stdout urandom v4l vga_arbiter video0 xconsole zero ls /dev/md: ls /mnt/boot-sav/sda2: YServer.txt wubildr.mbr wubildr Windows VideoOutput USetup.iss Users user.js unetbtin.exe tmp Information Volume System setup.log RHDSetup.log $Recycle.Bin Recovery Files Program ProgramData PerfLogs PDFZilla pagefile.sys output Intel hiberfil.sys eSupport error.log Settings and Documents config.sys BJPrinter autoexec.bat ASUS.DAT  =================== df -Th:  Filesystem    Type    Size  Used Avail Use% Mounted on aufs          aufs    968M  8.2M  959M   1% / tmpfs        tmpfs    968M     0  968M   0% /lib/init/rw udev         tmpfs    962M  164K  962M   1% /dev tmpfs        tmpfs    968M     0  968M   0% /dev/shm /dev/sr0   iso9660    339M  339M     0 100% /live/image tmpfs        tmpfs    968M  8.2M  959M   1% /live/cow tmpfs        tmpfs    968M     0  968M   0% /live tmpfs        tmpfs    968M  8.0K  968M   1% /tmp /dev/sda1  fuseblk    100M   25M   76M  25% /mnt/boot-sav/sda1 /dev/sda2  fuseblk     98G   38G   60G  39% /mnt/boot-sav/sda2 /dev/sda3  fuseblk    186G  103G   84G  56% /mnt/boot-sav/sda3 /dev/sda4  fuseblk    183G   18G  166G  10% /mnt/boot-sav/sda4  =================== fdisk -l:  Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x66e483c6  Device Boot      Start         End      Blocks   Id  System /dev/sda1   *           1          13      102400    7  HPFS/NTFS Partition 1 does not end on cylinder boundary. /dev/sda2              13       12749   102297600    7  HPFS/NTFS /dev/sda3           12749       36970   194560000    7  HPFS/NTFS /dev/sda4           36970       60802   191424512    7  HPFS/NTFS    =================== Default settings Recommended-Repair This setting would restore the [(generic mbr)] MBR in sda, and make it boot on sda1. Additional repair would be performed: unhide-bootmenu-10s  repair-wubi fix-windows-boot  =================== Settings chosen by the user Boot-Info This setting will not act on the MBR.  No change has been performed on your computer. See you soon! Please connect internet. Then close this window.  
```**********************************************************************


I'm sorry if the CODE display is not so convenient, so I  attached the doc file again.


Because I have some important document in this Ubuntu 11.04 partition, that I have not backup 

What should I do now to fix this problem?  

Many thanks in advance

---

### Post by bcbc on 2012-11-09
It looks like you might need to fsck the root.disk. To do this, boot from the Ubuntu CD/USB, select "Try Ubuntu", then drop to a terminal and run:
```
sudo mount /dev/sda4 /mnt
sudo fsck /mnt/ubuntu/disks/root.disk
sudo umount /mnt
```


```

     Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info September 18th 2012]


============================= Boot Info Summary: ===============================

 =>  is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda4/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   204,802,047   204,595,200   7 NTFS / exFAT / HPFS
/dev/sda3         204,802,048   593,922,047   389,120,000   7 NTFS / exFAT / HPFS
/dev/sda4         593,922,048   976,771,071   382,849,024   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A490A4B290A48C7C                       ntfs       System Reserved
/dev/sda2        E894B6C394B69412                       ntfs       
/dev/sda3        FE40B4BE40B47F49                       ntfs       
/dev/sda4        8608C3EE08C3DAF7                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr0         /live/image              iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4/Wubi

00000000  7f 45 4c 46 01 01 01 00  00 00 00 00 00 00 00 00  |.ELF............|
00000010  01 00 03 00 01 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  88 03 00 00 00 00 00 00  34 00 00 00 00 00 28 00  |........4.....(.|
00000030  0b 00 08 00 55 ba c0 00  00 00 89 e5 83 ec 10 6a  |....U..........j|
00000040  00 b9 00 00 00 00 68 0f  00 00 00 b8 05 00 00 00  |......h.........|
00000050  e8 fc ff ff ff a3 00 00  00 00 58 5a c9 c3 55 31  |..........XZ..U1|
00000060  c0 89 e5 83 ec 08 c9 eb  cb 55 89 e5 57 56 53 83  |.........U..WVS.|
00000070  ec 1c 8b 41 08 8b 5d 08  8b 75 0c 8b 7d 14 8d 50  |...A..]..u..}..P|
00000080  01 85 c0 89 51 08 74 16  83 ec 0c 68 23 00 00 00  |....Q.t....h#...|
00000090  89 4d e4 e8 fc ff ff ff  8b 4d e4 83 c4 10 50 2b  |.M.......M....P+|
000000a0  19 1b 71 04 56 53 68 25  00 00 00 e8 fc ff ff ff  |..q.VSh%........|
000000b0  83 c4 10 83 7d 10 00 74  12 53 53 ff 75 10 68 2a  |....}..t.SS.u.h*|
000000c0  00 00 00 e8 fc ff ff ff  83 c4 10 83 7d 18 00 75  |............}..u|
000000d0  04 85 ff 74 15 8b 45 18  51 01 f8 50 57 68 2e 00  |...t..E.Q..PWh..|
000000e0  00 00 e8 fc ff ff ff 83  c4 10 8d 65 f4 5b 5e 5f  |...........e.[^_|
000000f0  5d c2 14 00 55 b8 c4 01  00 00 89 e5 56 53 8d 75  |]...U.......VS.u|
00000100  f8 81 ec 20 02 00 00 29  f0 85 d2 8d 5d d8 c6 45  |... ...)....]..E|
00000110  ec b9 89 5d ed c6 45 f1  e9 89 45 f2 c7 45 e4 00  |...]..E...E..E..|
00000120  00 00 00 c7 45 e8 00 00  00 00 c7 45 e0 00 00 00  |....E......E....|
00000130  00 c7 45 d8 00 00 00 00  c7 45 dc 00 00 00 00 7f  |..E......E......|
00000140  0b 51 51 68 36 00 00 00  6a 12 eb 32 8b 01 c7 05  |.QQh6...j..2....|
00000150  00 00 00 00 00 00 00 00  c7 05 04 00 00 00 00 00  |................|
00000160  00 00 e8 fc ff ff ff 85  c0 89 c3 74 7d 8b 00 8b  |...........t}...|
00000170  00 85 c0 75 13 52 52 68  48 00 00 00 6a 0d e8 fc  |...u.RRhH...j...|
00000180  ff ff ff 83 c4 10 eb 67  8b 40 14 31 d2 31 c9 eb  |.......g.@.1.1..|
00000190  09 03 50 04 13 48 08 8b  40 20 85 c0 75 f3 8d 45  |..P..H..@ ..u..E|
000001a0  ec 89 55 d8 8d b5 d8 fd  ff ff 89 4d dc 89 43 20  |..U........M..C |
000001b0  b9 00 02 00 00 89 f2 89  d8 e8 fc ff ff ff 85 c0  |................|
000001c0  7f ee 8b 45 e8 85 c0 74  1a 83 ec 0c 31 d2 6a 00  |...E...t....1.j.|
000001d0  6a 00 50 8b 45 e4 52 8d  4d d8 50 e8 89 fe ff ff  |j.P.E.R.M.P.....|
000001e0  83 c4 0c 89 d8 e8 fc ff  ff ff a1 00 00 00 00 8d  |................|
000001f0  65 f8 5b 5e 5d c3 55 89  e5 57 56 53 89 cb 83 ec  |e.[^].U..WVS....|
00000200


=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-11-09__23h06 ===================
boot-repair version : 3.193-0ppa22~lucid
boot-sav version : 3.193-0ppa39~lucid
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
boot-sav-nonfree version :
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 18.07.2012, squeeze, Debian, i686)
CPU op-mode(s):        32-bit, 64-bit
initrd=/live/initrd.img boot=live config   quiet BOOT_IMAGE=/live/vmlinuz

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain

=================== blkid:
/dev/sda1: LABEL="System Reserved" UUID="A490A4B290A48C7C" TYPE="ntfs"
/dev/sda2: UUID="E894B6C394B69412" TYPE="ntfs"
/dev/sda3: UUID="FE40B4BE40B47F49" TYPE="ntfs"
/dev/sda4: UUID="8608C3EE08C3DAF7" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda2.
=================== No kernel in /mnt/boot-sav/sda4/boot:
grub


There is Wubi inside sda4
=================== dmesg | grep EFI :
This live-session is not EFI-compatible.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda2.
sda3	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda3.
sda4	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-kernel,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda4.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD5000BEVT-8 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  106MB  105MB  primary  ntfs         boot
2      106MB   105GB  105GB  primary  ntfs
3      105GB   304GB  199GB  primary  ntfs
4      304GB   500GB  196GB  primary  ntfs



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:msdos:ATA WDC WD5000BEVT-8;
1:1049kB:106MB:105MB:ntfs::boot;
2:106MB:105GB:105GB:ntfs::;
3:105GB:304GB:199GB:ntfs::;
4:304GB:500GB:196GB:ntfs::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


=================== mount:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sr0 on /live/image type iso9660 (ro,noatime)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dvd dvdrw fd full fuse hpet initctl input kmsg log MAKEDEV md mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda3 sda4 sg0 sg1 shm snapshot snd sndstat sr0 stderr stdin stdout urandom v4l vga_arbiter video0 xconsole zero
ls /dev/md:
ls /mnt/boot-sav/sda2: YServer.txt wubildr.mbr wubildr Windows VideoOutput USetup.iss Users user.js unetbtin.exe tmp Information Volume System setup.log RHDSetup.log $Recycle.Bin Recovery Files Program ProgramData PerfLogs PDFZilla pagefile.sys output Intel hiberfil.sys eSupport error.log Settings and Documents config.sys BJPrinter autoexec.bat ASUS.DAT

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    968M  8.2M  959M   1% /
tmpfs        tmpfs    968M     0  968M   0% /lib/init/rw
udev         tmpfs    962M  164K  962M   1% /dev
tmpfs        tmpfs    968M     0  968M   0% /dev/shm
/dev/sr0   iso9660    339M  339M     0 100% /live/image
tmpfs        tmpfs    968M  8.2M  959M   1% /live/cow
tmpfs        tmpfs    968M     0  968M   0% /live
tmpfs        tmpfs    968M  8.0K  968M   1% /tmp
/dev/sda1  fuseblk    100M   25M   76M  25% /mnt/boot-sav/sda1
/dev/sda2  fuseblk     98G   38G   60G  39% /mnt/boot-sav/sda2
/dev/sda3  fuseblk    186G  103G   84G  56% /mnt/boot-sav/sda3
/dev/sda4  fuseblk    183G   18G  166G  10% /mnt/boot-sav/sda4

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x66e483c6

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       12749   102297600    7  HPFS/NTFS
/dev/sda3           12749       36970   194560000    7  HPFS/NTFS
/dev/sda4           36970       60802   191424512    7  HPFS/NTFS



=================== Default settings
Recommended-Repair
This setting would restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair would be performed: unhide-bootmenu-10s  repair-wubi fix-windows-boot

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer. See you soon!
Please connect internet. Then close this window.


```

---

### Post by Tetramailbox on 2012-11-09
Hello bcbc 

Thanks for your prompt reply.
I'll try it and back to you again.
Thanks

---

### Post by Tetramailbox on 2012-11-09
Hello bcbc

I get the message as follows 

```

[COLOR=#8b0000]fsck from util-linux-ng 2.17.2[/COLOR]
  [COLOR=#8b0000]e2fsck 1.41.14 (22-Dec-2010)[/COLOR]
  [COLOR=#8b0000]fsck.ext2: Superblock invalid, trying backup blocks...[/COLOR]
  [COLOR=#8b0000]
[/COLOR]
[COLOR=#8b0000]fsck.ext2: Bad magic number in super-block while trying to open /mnt/ubuntu/disks/root.disk[/COLOR]
 [COLOR=#8b0000]
The superblock could not be read or does not describe a correct ext2[/COLOR]  [COLOR=#8b0000]filesystem.  If the device is valid and it really contains an ext2[/COLOR]
  [COLOR=#8b0000]filesystem (and not swap or ufs or something else), then the superblock[/COLOR]
  [COLOR=#8b0000]is corrupt, and you might try running e2fsck with an alternate superblock:[/COLOR]
  [COLOR=#8b0000]    e2fsck -b 8193 <device>[/COLOR]
 
```The problem is still the same

---

### Post by bcbc on 2012-11-09
That doesn't look good.

Why don't you boot windows and run chkdsk /r on that partition. Use [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html) as a guide, making sure the root.disk is there afterwards. After that try the fsck again.

---

### Post by Tetramailbox on 2012-11-10
Trying... ... ...

---

### Post by HiImTye on 2012-11-10
reading the bootinfo file you attached, it appears that you have a WUBI install.

                          ```
sda4: __________________________________________________________________________ 
File system:       ntfs
Boot sector type:  Windows Vista/7: NTFS     
Boot sector info:  No errors found in the Boot Parameter Block.     
Operating System:       
Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr                         
/ubuntu/disks/root.disk /ubuntu/disks/swap.disk  
```you need to boot into Windows to fix your errors. a simple boot to windows then regular shutdown or restart should fix the problem.

---

### Post by Tetramailbox on 2012-11-10
Hello HiImTye

Yes, I have WUBI install.

For booting into Windows is normal.
But booting into Ubuntu, only getting the GRUB> prompt.



I tried according to bcbc's advice:
[I]"Why don't you boot windows and run chkdsk /r on that partition. Use [http://ubuntu-with-wubi.blogspot.ca/...-rootdisk.html]("http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html") as a guide, making sure the root.disk is there afterwards"
[/I]
I already check the root.disk in \ubuntu\disks  directory, it  is missing completely. :confused:

So, I tried to CHKDSK as Admin, 
and try to seach  \found.000 folder and *dir0000.chk* directory but also missing completely.    
:confused:

Actually where is those folder and directory placed in Windows? 

Any idea ?

---

### Post by HiImTye on 2012-11-10
I would give these a try:
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

---

### Post by bcbc on 2012-11-10
The \found.000 directories are hidden. If you look at that link I posted it shows the code you need ([http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)). First make sure you ran chkdsk on the drive that holds the \ubuntu directory.
Then run CMD.EXE as an administrator.

Then look for the hidden directories.

so e.g. if your \ubuntu is on drive G:, run chkdsk on G:
Then from the cmd prompt:
>G:
>dir /a:h

Then you should see the \found.??? directories.

---

### Post by Tetramailbox on 2012-11-10
Yes bcbc, 
I already done exactly as you said. 

Please kindly, see the attached result in JPG after CHKDSK as Admin 

After dir /a:h command, 
The result is giving 2 hidden directory:
[B]$RECYCLE BIN and System Volume information
[/B]that's all

---

### Post by westie457 on 2012-11-10
For Windows chkdsk command to repair the file sysytem there has to be an option specified at the end of the command (either /f or /r), in your screenshot no option has been specified so it is being run in check only mode. To the best of my knowledge this does not always report the errors.

Run ```
chkdsk /r
``` as recommended in the link posted earlier.
If memory serves me correctly Windows will then warn you that the drive must be unmounted to continue. Press Y and let it do its thing.
After that follow the routine also posted in the link from earlier.

---

### Post by Tetramailbox on 2012-11-10
Hi westie457

I have done it before for "chkdsk /r" 
and I can not find  \found.000 folder and *dir0000.chk* directory 

I already done "chkdsk /r" again,
 still can not find  \found.000 folder and *dir0000.chk* directory 
:confused::confused:

Please see the attached JPG file



***
And According to [HiImTye]("http://ubuntuforums.org/member.php?u=843901") 's advice to try                
[https://wiki.ubuntu.com/WubiGuide#Ca...ot_into_Ubuntu]("https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu")

I also done "chkdsk /r" to drive C: (to check if there is any error due in NTFS partition)
There is *wmloc.DLL* that is replaced due to error

and still \found.000 folder and *dir0000.chk* directory still missing completely
:confused:


Is there any possibility that my Windows 7 System Setting  
that prevent "chkdsk /r" 
to make \found.000 folder and *dir0000.chk* directory ?
:(

***


I have an idea, as follows:

I boot via Ubuntu LIVE USB Flash disk, 
Can I copy the root.disk file/any file or folder  to Ubuntu directory in my harddisk , which is necessary to have normal Ubuntu boot ?
If this idea possible, please kindly guide me this process. 

Thanks in advanced

---

### Post by bcbc on 2012-11-10
There is something odd going on, because your first set of jpgs showed about 5GB used space and the second showed about 1GB. So something changed.

Not all corruption is recoverable - while many have successfully repaired a root.disk using chkdsk it's not a guarantee.

I'm not sure what your recovery options are at this point. You could run something like photorec on /dev/sda4 and hope that it can extract important data.

---

### Post by Tetramailbox on 2012-11-10
Thanks bcbc

:( :( :(
OK, It's better for me to try recover important data by using PhotoRec.
and next step is to re-install the Ubuntu using WUBI again.

By the way, 
I observe that when my laptop booting into Ubuntu, 
it's stated that there is some kind of **NTFS error **
and then come into  GRUB> prompt.

Is there anything that I can do for getting the solution?

---

### Post by bcbc on 2012-11-10
The message looking for wubildr and the grub prompt are normal if there is no root.disk. I don't think there's any additional problem. If you uninstall Wubi (entry "Ubuntu" in Control panel/add-remove programs) then the option to boot ubuntu and the grub prompt will go away.

You might want to try a normal dual boot instead of a new Wubi install. With a normal dual boot, if something goes wrong you will be able to find your data - but with wubi it's all on the root.disk.

---

### Post by Tetramailbox on 2012-11-11
Thanks bcbc

I tried to recover file using "Test Disk" and getting some file that can be recovered, as my attached JPG.

Are those file can be used for solving my problem?

---

### Post by bcbc on 2012-11-11
> **Tetramailbox said:**
> Thanks bcbc

I tried to recover file using "Test Disk" and getting some file that can be recovered, as my attached JPG.

Are those file can be used for solving my problem?

No those are grub modules.

This is the problem with the wubi virtual disk. It's a single file containing all your data files and none of these will be shown as deleted by data recovery software because they never existed 'on the ntfs filesystem', just within the root.disk itself.

I think [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") (that's installed with testdisk) might be able to recover some of this:
> PhotoRec ignores the file system and goes after the underlying data, so it will still work even if your media's file system has been severely damaged or reformatted

---

### Post by Tetramailbox on 2012-11-20
I already used the Photorec for backup my file.

As a precaution, what should I do to avoid this matter come up again?
Is there any software to help me to do it ?

---

### Post by bcbc on 2012-11-20
I would switch from Wubi to a normal dual boot. 

If you keep using Wubi then you can refer to these posts for some more information:
[Six Wubi rules]("http://ubuntu-with-wubi.blogspot.ca/2012/08/six-wubi-rules.html") and [What's wrong with Wubi/Ubuntu]("http://ubuntu-with-wubi.blogspot.ca/2012/07/whats-wrong-with-wubiubuntu.html")

tl;dr make sure you keep real-time backups i.e. synchronization of data and/or full root.disk backups.

---

### Post by monkeybrain2012 on 2012-11-20
11.04 is dead since oct 28 meaning it will no longer get security updates and all the repositories have been removed. Better do as bcbc said get rid of WUBI and do a real dual boot instead and get a newer Ubuntu release.

---

### Post by Tetramailbox on 2012-11-22
OK, bcbc and monkeybrain2012

Thanks for your advice


What's is the advantage and the disadvantage for using Ubuntu normal dual boot?

---

### Post by bcbc on 2012-11-22
In your case...

**Advantage of normal dual boot**:
Less chance of file system corruption and better chance of data recovery if there is.
Noticeably faster for certain file-intensive operations

**Disadvantage**:
A little more complicated to install since you need to partition. Since you already have four primary partitions this becomes harder (one has to be deleted)
Harder to uninstall, since you need to reinstall the windows bootloader prior to removing the ubuntu partition

That's about the major differences

---

