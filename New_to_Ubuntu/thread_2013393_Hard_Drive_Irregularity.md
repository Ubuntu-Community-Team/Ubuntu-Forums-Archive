---
title: "Hard Drive Irregularity"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by DGINSD on 2012-06-30
I noticed this while configuring conky my Windows partition is listed as only being 100G when it should be 200G the outpurt of df gives me this.

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda5       50899828   7487752  40823816  16% /
udev             1747412         4   1747408   1% /dev
tmpfs             702484       916    701568   1% /run
none                5120         0      5120   0% /run/lock
none             1756208       724   1755484   1% /run/shm
/dev/sda6      291064116 131399012 144876604  48% /home
/dev/sdb1        3860600    155204   3705396   5% /media/SDcard
/dev/sda2      102399992  48926996  53472996  48% /media/Windows_7

```

While a window shot of the disc utility shows what in my estimation should be the correct 200G. Windows disc utility show the same irregularity but worse pulling up windows disc manager for partitioning shows on the graphical representation for the HDD the proper 200G while on the lines listing partitions shows 100G.

[IMG]http://s19.postimage.org/nfvze8g2b/disc_utility6302012.png[/IMG]

How do I correct this for both systems? Whatever value is correct, I'd at least like to have everything agreeing on what space have. I don't know how to take a screen or window shot in Windows, but if someone things it will help I will do my best to find out and post one.

I'm assuming the 200G is correct because if I the sum of all the partitions using the 200G figure is close, to 600G, with the advertised size being 640G. I can accept 40g shrinkage but 140G is pushin' it a bit (though I wouldn't be the least surprised).

Any and all help as always is greatly appreciated.

---

### Post by sandyd on 2012-06-30
> **DGINSD said:**
> I noticed this while configuring conky my Windows partition is listed as only being 100G when it should be 200G the outpurt of df gives me this.

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda5       50899828   7487752  40823816  16% /
udev             1747412         4   1747408   1% /dev
tmpfs             702484       916    701568   1% /run
none                5120         0      5120   0% /run/lock
none             1756208       724   1755484   1% /run/shm
/dev/sda6      291064116 131399012 144876604  48% /home
/dev/sdb1        3860600    155204   3705396   5% /media/SDcard
/dev/sda2      102399992  48926996  53472996  48% /media/Windows_7

```While a window shot of the disc utility shows what in my estimation should be the correct 200G. Windows disc utility show the same irregularity but worse pulling up windows disc manager for partitioning shows on the graphical representation for the HDD the proper 200G while on the lines listing partitions shows 100G.

[IMG]http://s19.postimage.org/nfvze8g2b/disc_utility6302012.png[/IMG]

How do I correct this for both systems? Whatever value is correct, I'd at least like to have everything agreeing on what space have. I don't know how to take a screen or window shot in Windows, but if someone things it will help I will do my best to find out and post one.

I'm assuming the 200G is correct because if I the sum of all the partitions using the 200G figure is close, to 600G, with the advertised size being 640G. I can accept 40g shrinkage but 140G is pushin' it a bit (though I wouldn't be the least surprised).

Any and all help as always is greatly appreciated.
Post output of
```

sudo fdisk -l
```
or 
```

sudo parted -l
```
if using gpt

---

### Post by DGINSD on 2012-07-01
I actually seemingly solved the issue by re-sizing my windows partition down to 100G moving my windows recovery over into the void and then extending my extended partition into that void. So I'm assuming there was a goof in my partition table somewhere that the re-sizing and movement corrected. But just in case here's the output of those commands.

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ sudo fdisk -l
[sudo] password for david: 

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0b9757b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   205209599   102400000    7  HPFS/NTFS/exFAT
/dev/sda3       205209600   249073663    21932032    7  HPFS/NTFS/exFAT
/dev/sda4       249073664  1250263039   500594688    5  Extended
/dev/sda5       463429632   566960127    51765248   83  Linux
/dev/sda6       566962176  1158502399   295770112   83  Linux
/dev/sda7      1240700928  1250263039     4781056   82  Linux swap / Solaris
/dev/sda8       453875712   463429631     4776960    7  HPFS/NTFS/exFAT
/dev/sda9      1158504448  1240698879    41097216   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8192     7744511     3868160    b  W95 FAT32
david@david-HP-Pavilion-g6-Notebook-PC:~$ sudo parted -l
Model: ATA TOSHIBA MK6476GS (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  210MB  209MB   primary   ntfs            boot
 2      210MB   105GB  105GB   primary   ntfs
 3      105GB   128GB  22.5GB  primary   ntfs
 4      128GB   640GB  513GB   extended
 8      232GB   237GB  4892MB  logical   ntfs
 5      237GB   290GB  53.0GB  logical   ext4
 6      290GB   593GB  303GB   logical   ext4
 9      593GB   635GB  42.1GB  logical   ext4
 7      635GB   640GB  4896MB  logical   linux-swap(v1)


Model: Generic- xD/SD/M.S. (scsi)
Disk /dev/sdb: 3965MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  3965MB  3961MB  primary  fat32



```

---

### Post by DGINSD on 2012-07-01
For future reference and in the interest of learning something. What might of those commands revealed about my problem? They have seemingly similar outputs and I'm assuming various different programs (disk utility, etc.) pull data from each of them, so if there were discrepancies between their outputs that would explain how the difference came about, but how would even these programs get different values?

---

### Post by sandyd on 2012-07-01
> **DGINSD said:**
> I actually seemingly solved the issue by re-sizing my windows partition down to 100G moving my windows recovery over into the void and then extending my extended partition into that void. So I'm assuming there was a goof in my partition table somewhere that the re-sizing and movement corrected. But just in case here's the output of those commands.

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ sudo fdisk -l
[sudo] password for david: 

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0b9757b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   205209599   102400000    7  HPFS/NTFS/exFAT
/dev/sda3       205209600   249073663    21932032    7  HPFS/NTFS/exFAT
/dev/sda4       249073664  1250263039   500594688    5  Extended
/dev/sda5       463429632   566960127    51765248   83  Linux
/dev/sda6       566962176  1158502399   295770112   83  Linux
/dev/sda7      1240700928  1250263039     4781056   82  Linux swap / Solaris
/dev/sda8       453875712   463429631     4776960    7  HPFS/NTFS/exFAT
/dev/sda9      1158504448  1240698879    41097216   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8192     7744511     3868160    b  W95 FAT32
david@david-HP-Pavilion-g6-Notebook-PC:~$ sudo parted -l
Model: ATA TOSHIBA MK6476GS (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  210MB  209MB   primary   ntfs            boot
 2      210MB   105GB  105GB   primary   ntfs
 3      105GB   128GB  22.5GB  primary   ntfs
 4      128GB   640GB  513GB   extended
 8      232GB   237GB  4892MB  logical   ntfs
 5      237GB   290GB  53.0GB  logical   ext4
 6      290GB   593GB  303GB   logical   ext4
 9      593GB   635GB  42.1GB  logical   ext4
 7      635GB   640GB  4896MB  logical   linux-swap(v1)


Model: Generic- xD/SD/M.S. (scsi)
Disk /dev/sdb: 3965MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  3965MB  3961MB  primary  fat32



```
Hmm. fdisk seems to be wrong as well.
205209599-409600   =204799999 sectors
512-byte sectors = 204799999 * ([COLOR=#000000]512/107374182) = 97.65624952316284 GB

512 * 1 sector/track * 255 heads
[/COLOR](512 bytes/sector)×(63 sectors/track)×(255 heads (tracks/cylinder) )×(1024 cylinders

The weirder thing is that the Extended Partition starts at 249073664, yet there is no partition that starts there. The partitions (inside the extended partition) start at 453875712. 

I believe that the source of your problems lie somewhere there.

---

