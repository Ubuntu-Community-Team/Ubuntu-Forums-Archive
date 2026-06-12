---
title: "Wierd freezing issues / skype / firefox / not much drive used"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by NeverUsedItBefore on 2011-12-10
Just ran the latest updates (on Release 11.10, Oneric).

I've rebooted a few times now and seem to have the following issues:

1) Skype cannot login; just hangs on login page.
Workaround found to launch skype from terminal using PULSE_SERVER=127.0.0.1 skype.
I got this command from the web so it could be dodgy for all I know, but it did seem to mean that I could login to Skype.

2) In Firefox, you cannot click any of the menus. For instance I tried to navigate to this forum using the bookmark, but if you click up there then firefox just seems to hang for ages and ages

3) Finally, according to system monitor I have a tiny amount of free disk space. When I originally installed Ubuntu I used the wizard to handle drive partian. I'm sure the disk must be at least 250 GB but according to ubuntu avalaible disk space is at 6.6. GB .
System monitor lists the disk as follows:
Total 17.6 GiB
Free 7.9 GiB
Avaliable 7.0 GiB
USed 9.7 GiB

I asked the wizard to use about half the full drive. (I now wish I'd set it to use as much as possible without not being able to launch windoze - I never use windoze now).
Why is it using such a small amount of the drive and how to make it use more ? (Or, is this worth it even, perhaps it's OK as it is?)

---

### Post by BC59 on 2011-12-10
Could you post the results of these commands on a terminal?

```
sudo parted /dev/sda print
```

```
sudo fdisk -l
```

Please use the wrap with QUOTE option, to seen more clear the result.

---

### Post by NeverUsedItBefore on 2011-12-10
First one

Model: ATA ST380011A (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      41.1MB  60.0GB  59.9GB  primary   ntfs            boot
 2      60.0GB  80.0GB  20.1GB  extended
 5      60.0GB  79.1GB  19.2GB  logical   ext4
 6      79.1GB  80.0GB  883MB   logical   linux-swap(v1)

---

### Post by NeverUsedItBefore on 2011-12-10
Second one. Sorry I don't know what the Quote thingie means.

sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43744e16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       80325   117131735    58525705+   7  HPFS/NTFS/exFAT
/dev/sda2       117133310   156301311    19584001    5  Extended
/dev/sda5       117133312   154574847    18720768   83  Linux
/dev/sda6       154576896   156301311      862208   82  Linux swap / Solaris

---

### Post by BC59 on 2011-12-10
Looks like you don't have space to expand your ext4 partition. 

You could empty your Ubuntu partition of any personal files you have in Documents, Videos, Music and Pictures.

You could take some from the Windows NTFS but depends to you and it's more complicated.

---

### Post by NeverUsedItBefore on 2011-12-11
This is confusing, so I have the following questions?
1)Why is there four partians when there should be two (one for windows, one for ubuntu)

2) Why has ubuntu created such a small partian? I'm sure it wasn't that small before oneric

3) How to fix this, how to make ubuntu use more of the disk?

---

### Post by BC59 on 2011-12-12
Windows need 2 partitions and the extended you have includes the Linux partition and the swap which Linux uses as RAM supplement. Everything is correct. Ubuntu used all the space available.
To take space from Windows it's a little complicated now. The better way to leave space for Ubuntu is move some files to the Windows part.

---

