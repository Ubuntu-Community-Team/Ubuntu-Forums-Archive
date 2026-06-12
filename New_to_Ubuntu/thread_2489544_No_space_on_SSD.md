---
title: "No space on SSD"
date: 2023-08-02
forum: New to Ubuntu
---

### Post by stevef48-0 on 2023-08-02
I've installed Ubuntu 22.04 on the 128gb SSD in my old desktop. It would be nice if I could use space on this disk for digikam and its database, but Ubuntu seems to have grabbed all of the disk for itself.
```
df -h shows:-
Filesystem      Size   Used  Avail   Use% Mounted on
tmpfs             366M  1.8M  365M     1% /run
/dev/sdb3       117G   15G    96G   14% /
tmpfs              1.8G       0   1.8G     0% /rdev/shm
tmpfs              5.0M  4.0K   5.0M     1% /run
/dev/sdb2        512M  17M  496M     4% /boot/efi
tmpfs             366M  172K  366M     1% /run/user/1000
```

What can I do to make some of the available space available for digikam appimage, data etc?
Thanks in advance,
Steve

---

### Post by ActionParsnip on 2023-08-02
You aren't using much space. What is the output of:
```

sudo fdisk -l

```

---

### Post by DuckHook on 2023-08-02
Are you running digikam as an AppImage? I don't use AppImages so can only point you to [their documentation]("https://docs.appimage.org/"), but from the little that I know, it requires some tweaking to their settings to allow access to your /home directory.

I avoid all such problems by running only the repo versions of apps. I find packaging platforms like snaps, flatpacks and AppImages far too bloated and temperamental to be worth the tiny advantage of having the latest shiny bells and whistles. Repo apps are all tested to run with the version they accompany. No muss, no fuss, no bloat and everything is where it's supposed to be.

---

### Post by grahammechanical on 2023-08-02
When we install Ubuntu and choose the option to Erase disk and install Ubuntu, then Ubuntu will grab the whole disk. How can it not do that? The installer will create a partition table and format the drive and create two partitions. One partition will be a boot partition. That is your /dev/sdb2. It contains the file for the bootloader (Grub). The other partition is the Ubuntu partition (/dev/sdb3). It is 117 GB in size but Ubuntu is only using 15 GB. You have 96 GB to save files in your user /home directory - folder.

If you want to store files in a separate partition then you must use GParted to shrink the Ubuntu (117 GB ) partition and then create a new partition in the unallocated space that has been created by shrinking the Ubuntu partition. Do you want to do that?

Regards

---

### Post by stevef48-0 on 2023-08-03
This is the output from fdisk -l:-

Disk /dev/loop0: 63.45 MiB, 66531328 bytes, 129944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 63.28 MiB, 66355200 bytes, 129600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 73.86 MiB, 77443072 bytes, 151256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 240.61 MiB, 252301312 bytes, 492776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 73.88 MiB, 77463552 bytes, 151296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 346.33 MiB, 363151360 bytes, 709280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop7: 237.21 MiB, 248733696 bytes, 485808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: ST2000DM001-1CH1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: CDB3C15E-942E-4FF4-BD13-BE2E2B8A1EA7


Device     Start        End    Sectors  Size Type
/dev/sda1   2048 3907028983 3907026936  1.8T Microsoft basic data




Disk /dev/sdb: 119.24 GiB, 128035676160 bytes, 250069680 sectors
Disk model: PLEXTOR PX-128M5
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: FBBD940D-D48C-4A25-9A43-9AAEF2A0423C


Device       Start       End   Sectors   Size Type
/dev/sdb1     2048      4095      2048     1M BIOS boot
/dev/sdb2     4096   1054719   1050624   513M EFI System
/dev/sdb3  1054720 250068991 249014272 118.7G Linux filesystem




Disk /dev/sdd: 298.09 GiB, 320072933376 bytes, 625142448 sectors
Disk model: WDC WD3200AAJS-6
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000001


Device     Boot Start       End   Sectors   Size Id Type
/dev/sdd1        2048 625139711 625137664 298.1G  7 HPFS/NTFS/exFAT




Disk /dev/loop8: 349.7 MiB, 366682112 bytes, 716176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop10: 485.52 MiB, 509100032 bytes, 994336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop9: 12.32 MiB, 12922880 bytes, 25240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop11: 49.84 MiB, 52260864 bytes, 102072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop12: 53.26 MiB, 55844864 bytes, 109072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop13: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop14: 45.93 MiB, 48160768 bytes, 94064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop15: 304 KiB, 311296 bytes, 608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop16: 452 KiB, 462848 bytes, 904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

---

### Post by stevef48-0 on 2023-08-03
I took ownership of the disk and created the folders that I wanted.
Everything seems to be working as I would expect.
Thank you to everyone who replied.
Steve

---

### Post by stevef48-0 on 2023-08-03
I was using the latest appimage, but thought that I would try the latest repo version (8.0). 
It isn't working. It dosn't have the option to use an internal Mysql server for my data and has now stopped responding.

---

### Post by stevef48-0 on 2023-08-03
I spoke too soon, the program stopped responding.

---

