---
title: "Getting data off a bad partition....need help"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2008-10-19
My /dev/sad5 partition seems to be unreadable,which was my working Ubuntu (dual boot ), untill WinXP failed, and everything went down hill after I re-installed it. I cant seem to mount it normally. I get an error to do with the super block...

I really only need to get info from the /Home dir

I have re-installed Ubuntu 7.1 ( sda8 )in a a new partiton along with another partition ( sda4 ) which is empty.

I know the HDD is a bit of a mess, but if/when I get the data out of /sad5
I will be re-formatting the whole thing and starting with fresh installs of WinXP and Ubuntu


I really want to get the data out if possible

Any help would be much appreciated

ncts@ncts-laptop:~$ sudo fdisk -l
[sudo] password for ncts:

[COLOR="Blue"]Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7         899     7173022+   7  HPFS/NTFS
/dev/sda3            3104        7236    33198322+   f  W95 Ext'd (LBA)
/dev/sda4             900        3103    17703630   83  Linux
/dev/sda5            4087        6636    20482812   83  Linux
/dev/sda6            7179        7236      465853+  82  Linux swap / Solaris
/dev/sda7   *        3104        4037     7502292   83  Linux
/dev/sda8            4038        4086      393561   82  Linux swap / Solaris

Partition table entries are not in disk order
ncts@ncts-laptop:~$ 

[/COLOR]

---

### Post by ptn107 on 2008-10-19
See if this helps: [http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

---

### Post by caljohnsmith on 2008-10-19
This might explain a little more in depth what ptn107 linked to:

[http://ubuntuforums.org/showthread.php?p=5806996#post5806996](http://ubuntuforums.org/showthread.php?p=5806996#post5806996)

---

### Post by dash86no on 2008-10-19
> **Ducatiboy Stu said:**
> My /dev/sad5 partition seems to be unreadable,which was my working Ubuntu (dual boot ), untill WinXP failed, and everything went down hill after I re-installed it. I cant seem to mount it normally. I get an error to do with the super block...

I really only need to get info from the /Home dir

I have re-installed Ubuntu 7.1 ( sda8 )in a a new partiton along with another partition ( sda4 ) which is empty.

I know the HDD is a bit of a mess, but if/when I get the data out of /sad5
I will be re-formatting the whole thing and starting with fresh installs of WinXP and Ubuntu


I really want to get the data out if possible

Any help would be much appreciated

ncts@ncts-laptop:~$ sudo fdisk -l
[sudo] password for ncts:

[COLOR="Blue"]Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7         899     7173022+   7  HPFS/NTFS
/dev/sda3            3104        7236    33198322+   f  W95 Ext'd (LBA)
/dev/sda4             900        3103    17703630   83  Linux
/dev/sda5            4087        6636    20482812   83  Linux
/dev/sda6            7179        7236      465853+  82  Linux swap / Solaris
/dev/sda7   *        3104        4037     7502292   83  Linux
/dev/sda8            4038        4086      393561   82  Linux swap / Solaris

Partition table entries are not in disk order
ncts@ncts-laptop:~$ 

[/COLOR]

I usually use spinrite [http://en.wikipedia.org/wiki/SpinRite](http://en.wikipedia.org/wiki/SpinRite) to fix HDD problems, but that's normally only useful for recovering data from a physically failing disk.

In your case, maybe you want to check out the ckfs or debugfs commands. I haven't used these much myself, I just came across them while studying for LPIC level 1 (so they may be a little old school/out of date judging by the rest of the course material)

Good luck with the recovery

---

### Post by drs305 on 2008-10-19
Until you decide on a recovery method, don't do anything which will write to the disk/partition you are trying to recover.

I'm a fan of testdisk. It and other utilities/methods are explained in the following link. Here's the Ubuntu wiki:

[DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by Ducatiboy Stu on 2008-10-20
OK...some more info

```
ncts@ncts-laptop:~$ sudo mount /dev/sda5 /mnt
[sudo] password for ncts:
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ncts@ncts-laptop:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-041B" TYPE="vfat" 
/dev/sda2: UUID="B031CDB031C9C4" LABEL="Win" TYPE="ntfs" 
/dev/sda4: LABEL="data" UUID="6368746f-2074-616b-6f65-207575696400" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="1ca445cc-89ad-4201-9f2c-4d0fddc2355f" TYPE="ext2" 
/dev/sda6: TYPE="swap" UUID="41d29e5b-9c29-4251-8d7b-78476d7e747a" 
/dev/sda7: UUID="1c5da9f8-d105-4c86-adc2-ed1365f0d043" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="be398488-99ab-40e9-87ef-2f1367727bfd" 
ncts@ncts-laptop:~$ 

```

testdisk /dev/sda5

```
TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63

     Partition                  Start        End    Size in sectors

  Linux                 4086   2  1  6635 254 63   40965624
superblock 0, blocksize=4096
  Linux                 4086   2  1  6635 254 63   40965624
superblock 32768, blocksize=4096
superblock 98304, blocksize=4096
superblock 163840, blocksize=4096
superblock 229376, blocksize=4096
superblock 294912, blocksize=4096
superblock 819200, blocksize=4096
superblock 884736, blocksize=4096
superblock 1605632, blocksize=4096
superblock 2654208, blocksize=4096



[  Quit  ]
                            Return to Advanced menu

```


fsck /dev/sda5 

```
ncts@ncts-laptop:~$ sudo fsck /dev/sda5
[sudo] password for ncts:
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda5 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Group 3's inode table at 98309 conflicts with some other fs block.
Relocate<y>? 

```

I did not yet do fsck


Before I go any further, can someone offer more advice..

Unfortunatly I dont have another media HDD dev I can use. I dont really want to muck around with any more partitioning just in case i create more issues. 

I know /dev/sda4 is a bit smaller than sda5.



I also installed ex2Ifs in XP, and can see all the partitions, sda5 is the only one I cant read

I dont have a DVD writer, just a CD writer

---

### Post by Ducatiboy Stu on 2008-10-20
Performed ex2fsck -y -v /dev/sda5

Went for 11hrs with no luck


I found a program called R-linux [http://www.data-recovery-software.net/Linux_Recovery.shtml]("http://www.data-recovery-software.net/Linux_Recovery.shtml")


It seems to be able to read the files and $Inode tables, and i can actually see files...

Hoping it will recover what I need

---

