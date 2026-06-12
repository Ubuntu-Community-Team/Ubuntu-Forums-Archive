---
title: "Problems with Grub and now Ubuntu installation is gone"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by mvburgos on 2012-05-18
Hello i have a HP Desktop PC with Windows and Ubuntu dualboot.
Today i wanted to boot into Ubuntu to put Widnows as Default boot OS in startup manager with 3 seconds delay but i don't know what happened that it booted into HP_RECOVERY partition, once the hp repair windows show up i clicked in the X button to close the windows and restart to boot into Ubuntu again and see what i did wrong in the settings but oh surprise all i got was:

[B]error: no such partition. 
Grub rescue>[/B]

So ok i started reading and booted with a Live CD i tried to fix it with some commands but i could not figure it out my ubuntu partition. The **sudo fdisk -l** command shows:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2    *        206,848   212,041,934   211,835,087   7 NTFS / exFAT / HPFS
/dev/sda3         212,043,774 1,927,269,854 1,715,226,081   f W95 Extended (LBA)
/dev/sda5         421,738,443 1,927,269,854 1,505,531,412   7 NTFS / exFAT / HPFS
/dev/sda4       1,927,276,544 1,953,521,663    26,245,120   7 NTFS / exFAT / HPFS

Disk /dev/sdb: 4110 MB, 4110417920 bytes
127 heads, 62 sectors/track, 1019 cylinders, total 8028160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     8,023,605     8,023,544   c W95 FAT32 (LBA)
```

I installed Ubuntu 11.10 right after WINDOWS 7 you can see how it shows the order of labels now:

```
Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       50dce586-b93a-4815-968c-a0d97562d413   ext3       
/dev/sda1        EA24B2B324B281DD                       ntfs       System Reserved
/dev/sda2        01CD20F3AE8A1880                       ntfs       WINDOWS 7
/dev/sda4        78E64789E647469A                       ntfs       HP_RECOVERY
/dev/sda5        01CC6600234661B0                       ntfs       V-FILES
/dev/sdb1        221D-3686                              vfat    

```

then as i could not find my linux partition downloaded boot repair from command line and selected the recommended boot repair. After that i could boot but into Windows no grub menu.

**[SIZE="3"][CENTER]* I haven't in any moment deleted or formatted ubuntu partition so the os should be there i really have no idea why it can't be recognized *[/CENTER][/SIZE]**

**Also here is the pastebin of boot rescue software:**
[http://paste.ubuntu.com/994439/]("http://paste.ubuntu.com/994439/")

Here is a screenshot taken from a partition software on windows:
[IMG]http://dl.dropbox.com/u/21630798/ubuntugone.png[/IMG]

The unallocated partition is where ubuntu is installed.

I need to restore my system :( 

Thank you in advance for any help you can offer.

---

### Post by oldfred on 2012-05-18
You are not showing any Linux partition. If it is in the unallocated shown you may be able to use testdisk to restore it.

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by mvburgos on 2012-05-18
> **oldfred said:**
> You are not showing any Linux partition. If it is in the unallocated shown you may be able to use testdisk to restore it.

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Thank you ill try that and report back

---

### Post by mvburgos on 2012-05-18
SUCCESS!!! thank you very much @oldfred TestDisk restored my missing Linux partitions, im back and running now. I had to boot with LiveCD and start boot restore application > advanced option to purge-reinstall grub though as it still was booting directly to windows.

KUDOS!!!

---

### Post by oldfred on 2012-05-18
Glad it worked.   :)

---

