---
title: "lubuntu 11.10 installs fine...but no boot-up"
date: 2011-12-24
forum: New to Ubuntu
---

### Post by stonecoldjha on 2011-12-24
Hi,
I installed lubuntu 11.10 on my desktop using a usb drive, which already had windows 7 installed. I had emptied out some 20 GB out of my C drive bearing my windows installation for installing ubuntu. The installation went on to completion without any errors. But when I restarted, i could not boot...as after the bios stage, i just saw a blinking cursor on the screen. I restored the windows mbr with my win 7 disk, and I can now boot into windows. But, I would like to have lubuntu on my machine, and let grub let me decide which os i want to boot into. Someone please help!!

---

### Post by Rubi1200 on 2011-12-24
Please post the specifications for the computer, especially RAM and graphics card.

Thanks.

---

### Post by stonecoldjha on 2011-12-24
I have a 2 GB ram ,nvidia geforce 6200 (256 MB) graphics card, and a 2 GHz Intel Core2Duo processor.My computer is fairly old, I got it in 2007. This was the second time i tried installing lubuntu 11.10. After I installed it for the first time, I got a grub error saying no such partition. I searched for it and found that old computers may have bios that cannot see beyond the first 137 GBs, I selected a different 20 GB partition, on my second installation, the one next only to my C drive containing windows which is some 50 GBs on sda 1, to let ubuntu format it into an ext 4 drive, assuming that the boot files will now be visible to the bios. Installation went fine, but on restart I could not boot into either of the OSes. Rather, I saw a blinking cursor, not even the grub error message like before. 
Its not the first time that this thing happened. I have been trying on and off to install ubuntu, both natty and oneiric, using my usb drive. But everytime, after a smooth installation, either a grub message pops up on restart saying no such partition, or i see a blinking cursor, and I can't boot into either windows or ubuntu, making me repeat the windows mbr fixing exercise.

---

### Post by Rubi1200 on 2011-12-25
Two things I can suggest:

1. try booting with nomodeset because of the graphics card you have:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
(see post # 1 there)

2. if that doesn't help, then post the results of the boot info script here as that may also give us some clues as to what is happening.

There is a link at the bottom of my post with instructions.

---

### Post by stonecoldjha on 2011-12-25
Hi,
I tried reinstalling with nomodeset turned off at the start of installation, but still the same thing after installation. In order to use the bootinfo script, I need to boot into lubuntu live mode using my usb drive, and download it, and post its text output to this forum. But, lubuntu comes only with a chromium browser that doesn't let you set up the proxy settings (I am on a university network, and connect to the internet via some proxies), unlike firefox. So, I cannot connect to the internet to get the script. If I were to download the script in windows, and save it on my hard drive, I cannot access it when I have booted using my usb. What do i do now?

---

### Post by Rubi1200 on 2011-12-25
Check the Windows Disk Management utility and let us know if the disks are labeled as Basic or Dynamic.

If you can boot the LiveUSB choosing to try not install, then post the output of the following command:

```
sudo fdisk -l
```
(lowercase L not 1)

Thanks.

---

### Post by kansasnoob on 2011-12-25
> **Rubi1200 said:**
> Check the Windows Disk Management utility and let us know if the disks are labeled as Basic or Dynamic.

If you can boot the LiveUSB choosing to try not install, then post the output of the following command:

```
sudo fdisk -l
```
(lowercase L not 1)

Thanks.

Maybe you could use the git version of the BIS, which also happens to work better:

[http://ubuntuforums.org/showpost.php?p=11559146&postcount=18](http://ubuntuforums.org/showpost.php?p=11559146&postcount=18)

I'd get more involved but I'm working on something else ATM :)

But downloading the git version should be OK with most networks ..... I think.

---

### Post by stonecoldjha on 2011-12-25
Hi,
I created a new ubuntu 11.10 usb bootable(since it has firefox), and booted using it, downloaded theat bootinfo script using firefox. The following is the output in the file results.txt:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2    *        206,848   102,402,047   102,195,200   7 NTFS / exFAT / HPFS
/dev/sda3         102,404,094   488,394,751   385,990,658   f W95 Extended (LBA)
/dev/sda5         102,404,096   144,979,967    42,575,872  83 Linux
/dev/sda6         144,982,016   145,412,095       430,080  82 Linux swap / Solaris
/dev/sda7         145,414,144   206,854,143    61,440,000   7 NTFS / exFAT / HPFS
/dev/sda8         206,856,192   488,394,751   281,538,560   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   976,769,023   976,766,976   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 3869 MB, 3869544448 bytes
32 heads, 63 sectors/track, 3748 cylinders, total 7557704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     7,555,967     7,555,905   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FE10F39210F3505F                       ntfs       System Reserved
/dev/sda2        38D01AB4D01A7878                       ntfs       
/dev/sda5        7a352601-292a-41bc-97fa-0b74a52c0834   ext4       
/dev/sda6        e5dac027-5425-4210-8361-9aea14a85bf7   swap       
/dev/sda7        0A74AB9E74AB8B51                       ntfs       New Volume
/dev/sda8        ECB6B4F7B6B4C37E                       ntfs       New Volume
/dev/sdb1        8CDE899FDE8981E6                       ntfs       New Volume
/dev/sdc1        60C5-C4E4                              vfat       MYLINUXLIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

---

### Post by stonecoldjha on 2011-12-25
The following is the output of fdisk-l:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6981fb11

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2   *      206848   102402047    51097600    7  HPFS/NTFS/exFAT
/dev/sda3       102404094   488394751   192995329    f  W95 Ext'd (LBA)
/dev/sda5       102404096   144979967    21287936   83  Linux
/dev/sda6       144982016   145412095      215040   82  Linux swap / Solaris
/dev/sda7       145414144   206854143    30720000    7  HPFS/NTFS/exFAT
/dev/sda8       206856192   488394751   140769280    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f05ca48

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976769023   488383488    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 3869 MB, 3869544448 bytes
32 heads, 63 sectors/track, 3748 cylinders, total 7557704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3751324c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     7555967     3777952+   b  W95 FAT32

---

### Post by Rubi1200 on 2011-12-26
The boot script results are not showing all the information we need.

Try in live mode again, but this time install gawk before running the script:

```
sudo apt-get install gawk
```

Then run the script again and post the results as before please.

Thanks.

---

### Post by stonecoldjha on 2011-12-26
i installed gawk in live mode, and ran the bootinfo script. The results are:
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2    *        206,848   102,402,047   102,195,200   7 NTFS / exFAT / HPFS
/dev/sda3         102,404,094   488,394,751   385,990,658   f W95 Extended (LBA)
/dev/sda5         102,404,096   144,979,967    42,575,872  83 Linux
/dev/sda6         144,982,016   145,412,095       430,080  82 Linux swap / Solaris
/dev/sda7         145,414,144   206,854,143    61,440,000   7 NTFS / exFAT / HPFS
/dev/sda8         206,856,192   488,394,751   281,538,560   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   976,769,023   976,766,976   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 3869 MB, 3869544448 bytes
32 heads, 63 sectors/track, 3748 cylinders, total 7557704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     7,555,967     7,555,905   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FE10F39210F3505F                       ntfs       System Reserved
/dev/sda2        38D01AB4D01A7878                       ntfs       
/dev/sda5        7a352601-292a-41bc-97fa-0b74a52c0834   ext4       
/dev/sda6        e5dac027-5425-4210-8361-9aea14a85bf7   swap       
/dev/sda7        0A74AB9E74AB8B51                       ntfs       New Volume
/dev/sda8        ECB6B4F7B6B4C37E                       ntfs       New Volume
/dev/sdb1        8CDE899FDE8981E6                       ntfs       New Volume
/dev/sdc1        60C5-C4E4                              vfat       MYLINUXLIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

---

### Post by oldfred on 2011-12-26
Did you download the latest version? Even if you did, try the newest one Gert posted for testing and be sure to add lzma and/or 

sudo apt-get install gawk
sudo apt-get install xz-utils

[http://ubuntuforums.org/showthread.php?t=1897412&page=5](http://ubuntuforums.org/showthread.php?t=1897412&page=5)

I think I have seen where the grldr causes it to crash and whether the updates will fix that or not this may tell. It will be a good test.

---

### Post by stonecoldjha on 2011-12-28
Hi,
Thank you very much for the help. I have run into another problem now, which is preventing me from running the script in live mode. I tried booting in live mode using my usb, but after it boots up, ubuntu 11.10 freezes up, and I have to restart. I formatted my usb, and made it bootable again with ubuntu 11.10, but cannot get it to work as it freezes up after the unity interface shows up on choosing to try ubuntu. I also tried installing using wubi just to run those scripts. But, there was some error, and the installation failed. What do I do now?

---

### Post by oldfred on 2011-12-28
Often not booting fully is related to video issues. Try nomodeset or other settings depending on video card/chip you have.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by stonecoldjha on 2011-12-31
Hi,
I reinstalled lubuntu 11.10, but still the same problem. I booted into an ubuntu 11.10 live session, after restoring the windows mbr, and downloaded the script from that post you gave the link to. The results.txt contents are:

                   Boot Info Script 0.60      [17 May 2011]

Last git commit:       Use lzma or xz for decompression of lzma streams.
Retrieved from git on:


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1
                       and looks at sector 149140672 of the same hard drive
                       for core.img. core.img is at this location and looks
                       for (,msdos6)/boot/grub on this drive. No errors found
                       in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2    *        206,848   102,402,047   102,195,200   7 NTFS / exFAT / HPFS
/dev/sda4         102,404,094   488,394,751   385,990,658   f W95 Extended (LBA)
/dev/sda5         151,805,952   488,394,751   336,588,800   7 NTFS / exFAT / HPFS
/dev/sda6         102,404,096   149,852,159    47,448,064  83 Linux
/dev/sda7         149,854,208   151,805,951     1,951,744  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   976,769,023   976,766,976   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 3869 MB, 3869544448 bytes
32 heads, 63 sectors/track, 3748 cylinders, total 7557704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     7,555,967     7,555,905   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs  
/dev/sda1        FE10F39210F3505F                       ntfs       System Reserved
/dev/sda2        38D01AB4D01A7878                       ntfs      
/dev/sda5        286CE6D86CE6A034                       ntfs       New Volume
/dev/sda6        1b8efe7d-1379-486d-bead-9461cd955164   ext4      
/dev/sda7        0835a094-fe47-4249-954a-c729a43a8df4   swap      
/dev/sdb1        E2162C73162C4ABD                       ntfs       New Volume
/dev/sdc1        5218-FF4A                              vfat       MYLINUXLIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
/home/ubuntu/Desktop/bootinfoscript_xz_lzma: line 1971: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

Thanks!!

---

### Post by oldfred on 2011-12-31
You may still have video issues, but you installed grub2's boot loader to sda2, your NTFS partition. While that does let you boot, it does not let you use the NTFS partition as it has to have NTFS data structures not grub.

I have seen where script has issues with grub4dos.
sda1/grldr

You need to install grub to the MBR first then use testdisk to recover the backup PBR - partition boot sector for sda2. If it cannot recover it write a basic NTFS BS boot sector with Testdisk or else Windows will not try to repair it.
If you have written to it more than once then you will have to use Windows repairCD to run fixboot & chkdsk, usually several times & then it may not work.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Then when you get booting squared away we can look at video issues.

---

