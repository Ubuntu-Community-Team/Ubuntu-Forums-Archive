---
title: "Almost afraid to install Hardy"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by d3synguy on 2008-09-08
Hello, I am absolutely new to Linux and am not even sure of what version Linux I should install. However, I thought I would go ahead and install Hardy just to get familiar with the Linux platform. However, I already have my HD partitioned and am wary of the partitioning steps of the live CD install. Here is how my 750GB SATA is partitioned at present (as interpreted by Paragon Partition Manager):

Basic HD:                               698.6 GB--
  Logical Disk S:   Vista Ultimate       92.9 GB     Primary
  Logical Disk T:   XP Home SP3          93.5 GB     Primary
Extended Partition:                     512.1 GB-
  Logical Disk Q:   Ubuntu               30.3 GB     Logical
  Logical Disk P:   No Label             11.5 GB     Logical
  Logical Disk O:   Storage             187.2 GB     Logical
  Logical Disk N:   No Label             19.9 GB     Logical
  Logical Disk L:   Drivers, Updates     47.6 GB     Logical
  Logical Disk K:   No Label             70.5 GB     Logical
  Logical Disk J:   Backups             144.9 GB     Logical

All partitions are NTFS. Sorry about the strange drive letter configuration. There is another, smaller HD on this machine which is the C: drive that I will be phasing out of usage. When I installed this newer, larger HD a lot of letters were skipped because of a multi-card reader I have installed, and I have no idea why "M" and "R" were skipped. 

When I run the Hardy live CD to install and get to the partitioning step, (I select "manual",) I am confused by the partition layout that is displayed and I am unable to determine for certain which is the partition that I have designated for Ubuntu. I assume that this is the only partition I should concern myself with during installation. In Paragon Partition Manager I have the option to reformat a drive to either Linux Ext2, Linux Ext3 or Linux Swap2. Should I do this first? If so, should I allocate a portion for the Ubuntu partition as a swap file partition? Will there be a problem running three OS's?

Thanks for all answers in advance. For as little knowledge as I have, I'm already in way over my head.

---

### Post by starcannon on 2008-09-08
> **d3synguy said:**
> Hello, I am absolutely new to Linux and am not even sure of what version Linux I should install. However, I thought I would go ahead and install Hardy just to get familiar with the Linux platform. However, I already have my HD partitioned and am wary of the partitioning steps of the live CD install. Here is how my 750GB SATA is partitioned at present (as interpreted by Paragon Partition Manager):

Basic HD:                               698.6 GB--
  Logical Disk S:   Vista Ultimate       92.9 GB     Primary
  Logical Disk T:   XP Home SP3          93.5 GB     Primary
Extended Partition:                     512.1 GB-
  Logical Disk Q:   Ubuntu               30.3 GB     Logical
  Logical Disk P:   No Label             11.5 GB     Logical
  Logical Disk O:   Storage             187.2 GB     Logical
  Logical Disk N:   No Label             19.9 GB     Logical
  Logical Disk L:   Drivers, Updates     47.6 GB     Logical
  Logical Disk K:   No Label             70.5 GB     Logical
  Logical Disk J:   Backups             144.9 GB     Logical

All partitions are NTFS. Sorry about the strange drive letter configuration. There is another, smaller HD on this machine which is the C: drive that I will be phasing out of usage. When I installed this newer, larger HD a lot of letters were skipped because of a multi-card reader I have installed, and I have no idea why "M" and "R" were skipped. 

When I run the Hardy live CD to install and get to the partitioning step, (I select "manual",) I am confused by the partition layout that is displayed and I am unable to determine for certain which is the partition that I have designated for Ubuntu. I assume that this is the only partition I should concern myself with during installation. In Paragon Partition Manager I have the option to reformat a drive to either Linux Ext2, Linux Ext3 or Linux Swap2. Should I do this first? If so, should I allocate a portion for the Ubuntu partition as a swap file partition? Will there be a problem running three OS's?

Thanks for all answers in advance. For as little knowledge as I have, I'm already in way over my head.

I would recommend a WUBI install for your first time out, I see that you have a lot of logical drives there lol.

If how ever you really need/want to do a regular dual boot install:

I am assuming that you partitioned and labeled the drives yourself from windows, and that:
  Logical Disk Q:   Ubuntu               30.3 GB     Logical
is where you would like to install Ubuntu.
So in the manual partition editor, choose that partition, edit it to your hearts content, don't touch any of the others.

GL

---

### Post by billgoldberg on 2008-09-08
> **d3synguy said:**
> Hello, I am absolutely new to Linux and am not even sure of what version Linux I should install. However, I thought I would go ahead and install Hardy just to get familiar with the Linux platform. However, I already have my HD partitioned and am wary of the partitioning steps of the live CD install. Here is how my 750GB SATA is partitioned at present (as interpreted by Paragon Partition Manager):

Basic HD:                               698.6 GB--
  Logical Disk S:   Vista Ultimate       92.9 GB     Primary
  Logical Disk T:   XP Home SP3          93.5 GB     Primary
Extended Partition:                     512.1 GB-
  Logical Disk Q:   Ubuntu               30.3 GB     Logical
  Logical Disk P:   No Label             11.5 GB     Logical
  Logical Disk O:   Storage             187.2 GB     Logical
  Logical Disk N:   No Label             19.9 GB     Logical
  Logical Disk L:   Drivers, Updates     47.6 GB     Logical
  Logical Disk K:   No Label             70.5 GB     Logical
  Logical Disk J:   Backups             144.9 GB     Logical

All partitions are NTFS. Sorry about the strange drive letter configuration. There is another, smaller HD on this machine which is the C: drive that I will be phasing out of usage. When I installed this newer, larger HD a lot of letters were skipped because of a multi-card reader I have installed, and I have no idea why "M" and "R" were skipped. 

When I run the Hardy live CD to install and get to the partitioning step, (I select "manual",) I am confused by the partition layout that is displayed and I am unable to determine for certain which is the partition that I have designated for Ubuntu. I assume that this is the only partition I should concern myself with during installation. In Paragon Partition Manager I have the option to reformat a drive to either Linux Ext2, Linux Ext3 or Linux Swap2. Should I do this first? If so, should I allocate a portion for the Ubuntu partition as a swap file partition? Will there be a problem running three OS's?

Thanks for all answers in advance. For as little knowledge as I have, I'm already in way over my head.


First and foreall make sure you have Ubuntu 8.04.1, not an older version.

Ubuntu likes to use the ext3 file system, but during install, you can pick Reiserfs and a few others (don't pick ext2).

If I were you, I would clean up the mess you made out of you HDD.

2 or 3 partition max, is much easier to use.

Just let Ubuntu pick the largest partition and it will do everything itself.

If you want manual, you'll need a different partition for / and /swap. Swap should be around double your ram memory.

--
.
Drives in Ubuntu don't use letters, you can find mounted drives under /media.

---

### Post by d3synguy on 2008-09-08
Wow, this looks almost too easy. I have downloaded the WUBI installer and it is running now. I will let you know how it turns out.

Yes, I did create those partitions myself, but using the Paragon software. Yes I have a lot of partitions and I am sure that at some point I will end up merging several of them. I'm experimenting for now. (Hope I don't blow anything up!)

---

### Post by d3synguy on 2008-09-08
To billgoldberg:

I am also able to create a Reiserfs partition with Paragon, I just didn't realize that this could be utilized by Linux as well. Yes, I have version 8.04.1.

I agree that my HD is a mess with all the partitions. I had read an article that put forth the notion that you should install an OS on a small partition at the leading edge of the disk. The idea is that your computer would spend less time searching for files this way. It seemed logical to me, so that is what I tried to do. My partitions are a bit larger than recommended. I have a LOT of software installed on my Vista partition, and I can always shrink the partitions later if need be. (Perhaps I should have gone the other way -- smaller partitions and expand later if needed?) I will probably merge several of these partitions later on once I decide what they will utilized for. Because I am wont to experiment with OS's I like to keep my important files on a separate partition in case of a serious crash.

---

### Post by d3synguy on 2008-09-08
UPDATE

Decided against the WUBI install. I formatted my pre-selected Ubuntu partition to EXT3 and installed there. I successfully connected to my wireless network after a little fooling around. Now I just need to get my Nvidia drivers installed and see if I can configure Ubuntu for dual monitors. I'm sure I saw a couple of threads on here dealing with those issues. I will update later.

More Update:
I got the nVidia drivers working no problem, but for some reason now I have a lower refresh rate. I'm not real concerned with that at the moment. I'm more concerned with enabling dual monitors and operating them independently i.e., having separate windows open on separate monitors rather than one window stretched across two. I have found many lengthy threads dealing with this but none that I felt were what I was looking for.

---

### Post by starcannon on 2008-09-08
easiest way to set up dual monitors is with nvidia-settings.

```

sudo apt-get install nvidia-settings

```

A nice little gui written by nvidia for nvidia cards, and dual monitor configuration is in there.

Be sure to take some time to enjoy it now that its up and running, that in itself was a big project. Give yourself some time to breathe and enjoy what you've accomplished; beware of gfs(geek fatigue syndrome), recognized in its early stages by quad shots and mountain dew no longer do much more than making your left eye twitch slightly.

---

### Post by Bölvaður on 2008-09-08
I may add that in order to save your screens' configurations you should run as super user that has rights to change system like that.

You can either type : sudo nvidia-settings
in the terminal. or just change the command of the shortcut to include sudo infront to tell it to be run by super user.

(Normal users/programs are not allowed to fiddle with the system, only super user can)

---

