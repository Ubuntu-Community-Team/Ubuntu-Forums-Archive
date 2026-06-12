---
title: "install xubuntu alongside win8"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by EpicMinerBackup on 2013-01-27
I keep getting this

This happens with all distros 

[B]I'd love some help

[/B]

---

### Post by candtalan on 2013-01-27
1)
My experience with the (Windows) OS being treated as 'unmanageable' ie ignored for re size, has been that the Windows file system has been damaged. In the past that has usually been corrected by running a tool within Windows. However
2) It is more than possible that you purchased the machine with Windows 8 installed, which would mean that the Microsoft requirements for UEFI motherboard configuration applies. If so, then Microsoft 'secure boot' will be preventing a lot of things happening.

If this is bad news, then you have my sympathies.

---

### Post by EpicMinerBackup on 2013-01-27
I didn't buy a win 8 PC i just got the CD and installed it so if its win 8's fault 
im guessing i should A) install over Win 8 B) try to use the "something else" option and do 
some type of work around to duel boot C) just run it in live mode?
I'm kinda well really new to this

---

### Post by Bucky Ball on 2013-01-27
Welcome to the forums. That's what you should be getting. Choose 'Something Else' and partition manually if you don't want to kill Win.

Please remove these oversize images and attach them as thumbnails, thanks. They are a nightmare for some users with low bandwidth/speed and prevents them from assisting you.

---

### Post by EpicMinerBackup on 2013-01-27
Thanks for the help um but im not sure how to make it a thumbnail

---

### Post by Bucky Ball on 2013-01-27
> **EpicMinerBackup said:**
> Thanks for the help um but im not sure how to make it a thumbnail

Edit the first post, delete the image, click on 'Go Advanced', click the paperclip icon and attach the image. ;)

---

### Post by oldfred on 2013-01-27
How did you install Windows?

If you have used all 4 partitions Ubuntu has no place to go, so that screen is typical for Windows in BIOS/MBR with all 4 primary partitions used.
Or if UEFI/gpt do you have Intel SRT? That uses RAID.
 or old RAID data on drive from previous install?
Desktop installer does not yet have RAID drivers.

Post this from terminal in liveCd/DVD/flash.

sudo fdisk -lu
#If gpt drive.
       sudo parted /dev/sda unit s print

---

### Post by EpicMinerBackup on 2013-01-27
------------------
System Information
------------------
Time of this report: 1/27/2013, 18:26:28
       Machine name: FAMILY
   Operating System: Windows 8 Pro 64-bit (6.2, Build 9200) (9200.win8_gdr.121119-1606)
           Language: English (Regional Setting: English)
System Manufacturer: Dell Inc.
       System Model: Inspiron 560  
               BIOS: Default System BIOS
          Processor: Pentium(R) Dual-Core  CPU      E5700  @ 3.00GHz (2 CPUs), ~3.0GHz
             Memory: 4096MB RAM
Available OS Memory: 4060MB RAM
          Page File: 1891MB used, 6265MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 11
DX Setup Parameters: Not found
   User DPI Setting: Using System DPI
 System DPI Setting: 96 DPI (100 percent)
    DWM DPI Scaling: Disabled
     DxDiag Version: 6.02.9200.16384 64bit Unicode

---------------
Display Devices
---------------
          Card name: Intel(R) G45/G43 Express Chipset
       Manufacturer: Intel Corporation
          Chip type: Intel(R) 4 Series Express Chipset Family
           DAC type: Internal
        Device Type: Full Device
         Device Key: Enum\PCI\VEN_8086&DEV_2E22&SUBSYS_04391028&REV_03
     Display Memory: 1695 MB
   Dedicated Memory: 64 MB
      Shared Memory: 1631 MB
       Current Mode: 1366 x 768 (32 bit) (60Hz)
       Monitor Name: Dell IN1910N(Analog)
      Monitor Model: DELL IN1910N
         Monitor Id: DELA04C
        Native Mode: 1366 x 768(p) (59.790Hz)
        Output Type: HD15
        Driver Name: igdumd64.dll,igd10umd64.dll,igdumdx32,igd10umd32
Driver File Version: 8.15.0010.2202 (English)
     Driver Version: 8.15.10.2202
        DDI Version: 10
     Feature Levels: 10.0,9.1
       Driver Model: WDDM 1.1
Graphics Preemption: DMA
 Compute Preemption: DMA
  Driver Attributes: Final Retail
   Driver Date/Size: 8/25/2010 19:36:02, 6547968 bytes
        WHQL Logo'd: Yes
    WHQL Date Stamp: 
  Device Identifier: {D7B78E66-6D62-11CF-027B-3324A3C2C535}
          Vendor ID: 0x8086
          Device ID: 0x2E22
          SubSys ID: 0x04391028
        Revision ID: 0x0003
I hope this helps

---

### Post by EpicMinerBackup on 2013-01-27
> **oldfred said:**
> How did you install Windows?

If you have used all 4 partitions Ubuntu has no place to go, so that screen is typical for Windows in BIOS/MBR with all 4 primary partitions used.
Or if UEFI/gpt do you have Intel SRT? That uses RAID.
 or old RAID data on drive from previous install?
Desktop installer does not yet have RAID drivers.

Post this from terminal in liveCd/DVD/flash.

sudo fdisk -lu
#If gpt drive.
       sudo parted /dev/sda unit s print
xubuntu@xubuntu:~/Desktop$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3847905c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   976771071   488026112    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15633407     7816688    b  W95 FAT32
xubuntu@xubuntu:~/Desktop$ #If gpt drive.
xubuntu@xubuntu:~/Desktop$ sudo parted /dev/sda unit s print
Model: ATA WDC WD5000AAKS-7 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start    End         Size        Type     File system  Flags
 1      2048s    718847s     716800s     primary  ntfs         boot
 2      718848s  976771071s  976052224s  primary  ntfs

---

### Post by EpicMinerBackup on 2013-01-27
Holy guacamole i fixed by removing my USB O_o

---

### Post by candtalan on 2013-01-28
> **EpicMinerBackup said:**
> Holy guacamole i fixed by removing my USB O_o

Magic! :-)  LOL

---

