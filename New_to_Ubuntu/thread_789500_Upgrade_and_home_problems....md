---
title: "Upgrade and /home problems..."
date: 2008-05-10
forum: New to Ubuntu
---

### Post by toastybob on 2008-05-10
My sincerest apologies for posting these questions, which I'm sure will tax the patience of most here, but I was unable to find a solution searching the forum...

A friend set me up with Ubuntu and initially set up my home folder on a new partition.  I recently upgraded to 8.04 off of a disk and have since been unable to get the new system to recognize the old /home.

The parition structure looks like this:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1217     9775521    7  HPFS/NTFS
/dev/sda2            1218        1340      987997+  82  Linux swap / Solaris
/dev/sda3            1341        2313     7815622+  83  Linux
/dev/sda4            2314        7296    40025947+   5  Extended
/dev/sda5            2314        7296    40025916   83  Linux


My fstab currently looks like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c7083d96-aa39-4966-bd18-67989af4fbce /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=ee4984a3-1351-4be3-b6f9-4cd2b875fc16 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4       /home           ext3    defaults        0       2

Yet whenever I reboot, I get the following error:
Checking file systems...
fsck.ext3  Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Could this be a zero-length partition?
fsck died with exit status 8

Does anyone recognize this error?  Any help would be greatly appreciated.

Many thanks.

---

### Post by avtolle on 2008-05-10
I just looked at my fstab file, with a separate home, and find that it reads (using your device designation):
/dev/sda4/home ext 3 nodev,nosuid 0 2

I'm not an expert on fstab, but I would suggest you backup your current fstab file by typing this at the terminal:```
sudo cp /etc/fstab /etc/fstab.bak
```, then editing the final line by ```
sudo nano /etc/fstab
(enter password here, if needed)
```
Delete existing final line, then type in its place:```

/dev/sda4/home ext3 nodev,nosuid 0 2
```
CTRL-O to write
Return to save
CTRL-X to exit[/code]then reboot and see this works. HTH.

---

### Post by Irony on 2008-05-10
Perhaps you need to change sda4 to sda5 as home must be a partition and not the extended bit, thus;

```
/dev/sda2 none swap sw 0 0
/dev/sda3 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 /home ext3 defaults 1 2
```

---

### Post by forestpixie on 2008-05-10
dev/sda4 is an extended partition - try editing fstab so that your /dev/sda4 line is /dev/sda5

Edit - snap :D - went his really slow fingers

---

### Post by avtolle on 2008-05-10
At least you were quicker than I was; after I posted, I thought about that, (slow, I know) and was getting back to the thread to post that, too, and two of you beat me to it.

---

### Post by toastybob on 2008-05-10
SCORE!

Thanks everyone, but _that_ did it!

And by that, I mean, I initially tried replacing:

```
/dev/sda4 /home ext3 defaults 0 2
```

with:

```
/dev/sda4/home ext3 nodev,nosuid 0 2
```

which prevented the fsck error and booted just fine, but still no /home

So then I replaced that last line with:

```
/dev/sda2 none swap sw 0 0
/dev/sda3 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 /home ext3 defaults 1 2
```

And everything just worked.

Thanks!

One last quick question, then.  Can anyone explain to me what we just did/what was going on?  Or at least point me to a link that explains how this works (the view at 30,000 feet).  At least in terms of a learning experience towards getting my feet wet with linux...

---

### Post by forestpixie on 2008-05-10
> /dev/sda4 2314 7296 40025947+ 5 Extended
/dev/sda5 2314 7296 40025916 83 Linux

If you imagine that an extended partition is a box in which you can put many other boxes ( called logical partitions)  filled with data - then trying to get anything from the outside box will yield nothing. The data you're wanting is inside a box inside a box :)

sda4 is the extended partition and sda4 the logical partition 

If you look at your fdisk information
> 
/dev/sda1 * 1 1217 9775521 7 HPFS/NTFS
/dev/sda2 1218 1340 987997+ 82 Linux swap / Solaris
/dev/sda3 1341 2313 7815622+ 83 Linux
/dev/sda4 2314 7296 40025947+ 5 Extended
/dev/sda5 2314 7296 40025916 83 Linux

You will see that see that both sda4 and sda5 have the same start and end blocks, 2341 and 7296. If you had a second logical partition then the start and end blocks for the logical partitons would be different - but sda4 the extended partition would not change

> /dev/sda4 2314 7296 40025947+ 5 Extended
/dev/sda5 2314 4140 40025916 83 Linux
/dev/sda 4141 7296 40025916 83 Linux

Fstab - the file you edited and saved a backup for is the file which points at the various partitions and where they should be mounted in order to be used. You could if you so wished comment lines out so that they didn't mount at boot.

Edit - generally, many commands can have a manual page which you can get from terminal, and while it can be quite dry to read - they are useful - try man fstab in a terminal.

---

### Post by Irony on 2008-05-10
Fire up gparted and you will see that sda5 is in the extended partition of sda4.

Note I assume you just replaced the last line with;

```
/dev/sda5 /home ext3 defaults 1 2
```

Not;

```
/dev/sda2 none swap sw 0 0
/dev/sda3 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 /home ext3 defaults 1 2
```

I use actual device entries rather than uuids because I'm always swapping partitions about and uuids are confusing.

---

