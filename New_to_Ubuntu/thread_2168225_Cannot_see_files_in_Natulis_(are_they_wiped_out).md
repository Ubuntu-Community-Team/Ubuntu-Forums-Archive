---
title: "Cannot see files in Natulis (are they wiped out?)"
date: 2013-08-16
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2013-08-16
Ok, this is very strange. I have Ubuntu 12.04 on an external hard drive and yesterday I booted it up and was running dxdiag.exe in Wine just for the heck of it. The resolution was kind of screwed up so I rebooted and got the "grub rescue" screen. So I booted up Ubuntu 13.04 (in the internal drive of the same computer) and attached the drive, it didn't mount and blkid showed nothing. fdisk -l showed the drive and the partitions but attempted to mount them resulted in an error which says "unknown filesystem". I started gparted and it couldn't detect the drive either.

So I ran fsck on each partitions on the drive, it reported a lot of inode errors and offered to fix them, I press yes all the way and now the file system appeared to be restored. So I mount sdb1 (where Ubuntu 12.04's boot partition) and reinstalled grub and then rebooted with the drive attached. But then I got to a grub screen with a prompt instead of Ubuntu 12.04. So I booted into 13.04 again and attached the external drive. All partitions mounted but they appear to be empty in Nautilus, however running gparted  showed that the partitions are populated with data. 

What has happened? Are there still data in those partitions or have they been wiped out? If they are still there how can I access them and boot the drive again? Thanks

fdisk output
```

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072932352 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142446 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006b6bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    41945407    20971680   83  Linux
/dev/sdb2        41947134   415971327   187012097    5  Extended
/dev/sdb5        41947136   325720063   141886464   83  Linux
/dev/sdb6       325722112   332015615     3146752   82  Linux swap / Solaris
/dev/sdb7       332017664   363675647    15828992   83  Linux
/dev/sdb8       363677696   415971327    26146816   83  Linux


```

blkid output

```
/dev/sdb1: LABEL="ubu1204" UUID="211934fe-e4d8-49aa-b623-9552dec61563" TYPE="ext4" 
/dev/sdb5: LABEL="ubu1204_home" UUID="bc6ec861-3289-4351-8663-aa71d5a568ca" TYPE="ext4" 
/dev/sdb6: UUID="9ca2b28f-6052-4091-a97f-f89b0712227c" TYPE="swap" 
/dev/sdb7: UUID="424769e1-e0a2-4b35-9875-1a66e963f3b7" TYPE="ext4" 
/dev/sdb8: UUID="d956ffb6-eac3-43eb-8773-975795cc1a0d" TYPE="ext4"

```



P.S. I have the whole thing cloned so I could restore it, but I want some idea about what happened and the proper way to fix this kind of problems.

p.p.s I tried to upload a screenshot from gparted but somehow I couldn't. Basically I can't see anything unusal, it showed sdb1 and sdb5 with the correct label and format and the amount of data.

---

### Post by monkeybrain20122 on 2013-08-16
Update: Just mounted sdb5 and cd into it and run ls, it shows nothing other than lost+found. But gparted showed that it has 135 G of data??!!

---

### Post by nerdtron on 2013-08-16
Any files in the lost+found? Some files that were recovered/repaired would be there.
Also (sorry, it may seem obvious) have you tried showing hidden files?

---

### Post by monkeybrain20122 on 2013-08-17
Hi, 

Yes, I have tried show hidden file and lost+found showed up (it shouldn't be hidden) and I have no way to access its content, but it seems that you are right that the files maybe inside because if I right click Nautilus and choose properties it reported 97G of used space which is about the same as gparted (typo in first post 135G is the total)

---

### Post by westie457 on 2013-08-17
Hi, have you thought about using Testdisk to recover the partition table? It is in the repo's.

See here for more info. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by monkeybrain20122 on 2013-08-17
The drive may be corrupted or damaged. I have repartitioned it with gparted and tried a clean install of 12.04 with / on sdb1 and /home on sdb5. Before the installation I formatted both as ext4 and everything seemed to be in order (ran fsck and reported clean) Then ran the installer and it either aborted complaining that device not found (something like that) if I chose to format the partition at installation, or stuck in "copying installed packages" forever if I chose not to format. After the aborted attempt the drive would become unreadable, gparted indicated that sdb1 and sdb5 have unknown file system.
Ran fsck on /dev/sdb1 and I got these massive errors (just the begining)

```
Superblock invalid, trying backup blocks...
/dev/sdb1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(65536--67318) ... a whole lot more
```

Hardware problem?

---

### Post by monkeybrain20122 on 2013-08-17
> **westie457 said:**
> Hi, have you thought about using Testdisk to recover the partition table? It is in the repo's.

See here for more info. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Hi, thanks for the suggestion. will check it out.

---

### Post by westie457 on 2013-08-17
Testdisk has rescued complete hard -drives for me in the past. Corrupted partitions and accidentally wiped drives.

---

### Post by monkeybrain20122 on 2013-08-18
> **westie457 said:**
> Testdisk has rescued complete hard -drives for me in the past. Corrupted partitions and accidentally wiped drives.

Hi, I downloaded testdisk and tried to run it but the script won't start

Here are the commands and the outputs

```
$ cd Desktop/testdisk-6.14
user@raring:~/Desktop/testdisk-6.14$ sudo testdisk_static
[sudo] password for user: 
sudo: testdisk_static: command not found
user@raring:~/Desktop/testdisk-6.14$ sudo ./testdisk_static
./testdisk_static: 1: ./testdisk_static: Syntax error: "&" unexpected

```

Any idea what went wrong? Thanks.

---

### Post by westie457 on 2013-08-18
Yes, the command is wrong. Try ```
sudo testdisk
```

---

### Post by monkeybrain20122 on 2013-08-18
Hi

Still not working
```
user@raring:~/Desktop/testdisk-6.14$ sudo testdisk
[sudo] password for user: 
sudo: testdisk: command not found
```

There is no executable called "testdisk" inside the folder testdisk-6.14. Only testdisk-staic

Edited: OK, I ended up installing testdisk6-13 from Ubuntu's repo instead and it does start.

---

### Post by westie457 on 2013-08-18
Okay, you have only downloaded the package, not installed it.

Locate where it has been downloaded to. Right-click on the file select 'Extract here' check the small box to 'show extracted files'.
Double-clicking on the extracted file will install it through 'Software Centre'.
Then you can run the previously posted command.

Ignore this post

---

### Post by monkeybrain20122 on 2013-08-18
Hi,

I did "analysis" several times and here are the outputs

```
Disk /dev/sdb - 320 GB / 298 GiB - CHS 310091 32 63
     Partition               Start        End    Size in sectors
 L FAT12                 2796  22 23  2798   4  4       2880
 L FAT12                 5147  13 46  5148  27 27       2880
 L Linux                68637  14 47 89349   2 34   41754624
 L HPFS - NTFS          100797  30 63 100899  17 49     204800
 L Linux                144515   0  1 152444  28 60   15986688
 L Linux                154785   0  1 158751  31 31    7997440
 L Linux                158950  19 20 165213  14 46   12625920
 L Linux                175175   3 36 185576   8 48   20968744
 L HPFS - NTFS          185577  20 53 237277  14 39  104226809 [temdat]
 L Linux                237278  15 16 250747  29 53   27154424
 L Linux                250748  30 31 264325  28 12   27371088 [ubu1304test]
>L Linux                264327   3 36 279930  29 29   31457280
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock, 16 GB / 15 GiB
```

Not sure where the FAT partitions come from and the NTFS have been deleted long time ago. If I choose any of these with the right arrow to change the status to D (delete) then press enter I get back the beginning screen. If I choose "delete" I get "Write error: Can't clear partition table."

I don't want to recover any data, I have them all backed up. I just want to clean up the file system so I can use this drive again (if possible)

What should I do? Thanks.

---

### Post by westie457 on 2013-08-19
Part of the output of fdisk in your original post.
Disk /dev/sdb: 320.1 GB, 320072932352 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142446 sectors

The first line of the output of testdisk
Disk /dev/sdb - 320 GB / 298 GiB - CHS 310091 32 63

There is a big difference in the reported geometry of the hard drive. fdisk has given what it should be and testdisk has given what it actually is.

Testdisk should have given you an informative grumble about the hard drive values being incorrect when you started the analysis search of the partitions.

There probably is a more elegant way of adjusting the CHS values to the correct ones than the one I know.

You can wait to see if anyone chimes in with the elegant solution or you can go with the way I know which is to write a new partition table using Gparted. This will effectively wipe all information off the drive. Use this way only if you have already backed up the information or if you do not need it ever again.

As an experiment afterwards you could always give testdisk a re-try and reset upto 4 partitions as Primary and write the changes to the MBR.

Anyway that is something for you to think about. Hope it helps.

---

### Post by monkeybrain20122 on 2013-08-20
> **westie457 said:**
> Part of the output of fdisk in your original post.
Disk /dev/sdb: 320.1 GB, 320072932352 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142446 sectors

The first line of the output of testdisk
Disk /dev/sdb - 320 GB / 298 GiB - CHS 310091 32 63

There is a big difference in the reported geometry of the hard drive. fdisk has given what it should be and testdisk has given what it actually is.


Hi, nevermind the original post. I have tried to repartition the drive.

Now the data are as follows:

fdisk -l

```
Disk /dev/sdb: 320.1 GB, 320072932352 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142446 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000566b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    41945087    20971520   83  Linux
/dev/sdb2        41945088   625141759   291598336    5  Extended
/dev/sdb5        41947136   293605375   125829120   83  Linux
/dev/sdb6       293607424   299898879     3145728   82  Linux swap / Solaris
/dev/sdb7       299900928   625141759   162620416   83  Linux

```

blkid
```
/dev/sdb1: UUID="885a9562-830c-42c0-a752-08203c5f82f7" TYPE="ext4" 
/dev/sdb5: UUID="255df065-7972-47e8-9d3b-df60290f426c" TYPE="ext4" 
/dev/sdb6: UUID="08dd2b64-e14f-4113-bae5-63b0f234b18f" TYPE="swap" 
/dev/sdb7: UUID="77876229-a910-4ebf-b902-4c757214882c" TYPE="ext4"

```

testdisk Analyse  > Quicksearch

```
Disk /dev/sdb - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
>* Linux                    0  32 33  2610 245  3   41943040
 P Linux                 2611  22 36 18276  22 50  251658240
 P Linux Swap           18276  55 20 18667 214 27    6291440
 L Linux                18667 247 13 38913  70  5  325240832

```

Then go to "Deeper search" Many more partitions show up

```
Disk /dev/sdb - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
>D Linux                    0  32 33  2610 245  3   41943040
 D FAT12                  136 201  2   136 246 46       2880
 D FAT12                  139 216 14   140   6 58       2880
 D FAT12                  146 121 40   146 167 21       2880
 D FAT12                  156 237 18   157  27 62       2880
 D FAT12                  158 117 24   158 163  5       2880
 D FAT12                  162   7 38   162  53 19       2880
 D FAT12                  350 179 22   350 225  3       2880
 D FAT12                  350 244 23   351  35  4       2880
 D FAT12                  645 242 46   646  33 27       2880
 D Linux                 2611  22 36 18276  22 50  251658240
 D Linux                 8613  83 47 11212 110 34   41754624
 D Linux                 8942  26 45 11541  53 32   41754624
 D Linux                 8960 247 56 11560  19 43   41754624
 D Linux                 8992 214 55 11591 241 42   41754624
 D Linux                 9037 150 10 11636 176 60   41754624
 D HPFS - NTFS          12636 169 14 12649 104 63     204800
 D HPFS - NTFS          12649  39 63 12661 230 49     204800
 D Linux                18160  85 38 19155 117 34   15986688
 D Linux Swap           18276  55 20 18667 214 27    6291440
 D Linux                18440  40 33 25136   7 23  107569152
 D Linux                18667 247 13 38913  70  5  325240832
 D Linux                18734 228 55 20003 250 23   20387840
 D Linux                18735 136 26 20004 157 57   20387840
 D Linux                18735 201 27 20004 222 58   20387840
 D Linux                18738 184  7 20007 205 38   20387840
 D Linux                19424   0  1 19921 208 31    7997440
 D Linux                19692 138 31 20997 244 47   20971520
 D Linux                19716 194 63 20502 176 26   12625920
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock Recover, 21 GB / 20 GiB

```

Should I delete the superfluous partitions, how should I do it? Thanks.

---

### Post by monkeybrain20122 on 2013-08-20
Updated:

I just removed the drive and plug it in and get an error that a partition failed to mount

running dmesg | tail produced
```
dmesg | tail
[23855.419595] sd 7:0:0:0: [sdb] No Caching mode page present
[23855.419600] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[23855.419942] sd 7:0:0:0: [sdb] Attached SCSI disk
[23856.588623] EXT4-fs (sdb1): recovery complete
[23856.588631] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[23856.672406] EXT4-fs (sdb5): ext4_check_descriptors: Block bitmap for group 640 not in group (block 1128420181)!
[23856.672414] EXT4-fs (sdb5): group descriptors corrupted!
[23856.695094] EXT4-fs (sdb7): ext4_check_descriptors: Block bitmap for group 0 not in group (block 1128420181)!
[23856.695101] EXT4-fs (sdb7): group descriptors corrupted!
[23856.906194] systemd-hostnamed[16325]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```

---

### Post by westie457 on 2013-08-20
AKAIK you cannot delete those partitions that are in the 'Deeper Search' listing. Testdisk is designed to find traces of all partition records created on a hard disk for the life of the drive. In other words - every time you create/delete a partition and invoke a deeper search that list will get longer.

As the output shows they are already deleted and you will not have any problems from them. If you try to recover any of them you will be re-writing the MBR and probably resetting the hard drive to the situation that started this thread.

Personally, I would go with the results of 'Quick Search' and use the drive as normal. Install an OS and restore info/data from back-ups.

On the other hand if the drive is a spare or on its last legs and out of curiosity to find out how good testdisk is, I would attempt recovery of some of the partitions just to see if the info can be recovered as well. Testdisk will tell you immediately which partitions cannot be recovered. Also it will prompt you for confirmation before committing the changes you have asked for.

Good luck with which course you choose.

---

### Post by westie457 on 2013-08-20
Did you use Gparted to manually delete the original partitions one at a time and then create the new ones or did you go to the 'Device' menu of Gparted and select 'Create partition table....' and then create the new partitions?

First course of action now should be to force a check of the file-systems. Can be done through Gparted, Disks (Disk Utility) or the Cli, because I am not very good with the Cli I use GUI apps which for me are easier to use - point and click but take longer to explain. See ```
man fsck
``` for command line options.

---

### Post by monkeybrain20122 on 2013-08-20
I erased all partitions and create new partition table, then created partitions with same layout as from my last post. DId fsck and come out clean. testdisk smple search gave no error but when I tried to install Ubuntu 12.04 on sdb1 and chose option reformat it complained that / cannot be mounted and stuck. Maybe the disk is dead?

---

