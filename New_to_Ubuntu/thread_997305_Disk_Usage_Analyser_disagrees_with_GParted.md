---
title: "Disk Usage Analyser disagrees with GParted"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by damianubuntu on 2008-11-29
Hi all - apparently my root partition is nearly full 92% and 13GB, but Disk Usage Analyser shows that / only has 4.5 GB usage, which is what I would expect. After searching around I still have no idea how to progress, only dire warnings that a filling up / is very bad on ext3.

```

rachel@rachel-laptop:~$ df -h /
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              15G   13G  1.2G  92% /

```

and fdisk -lu gives

```

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    12611024     6305481    7  HPFS/NTFS
/dev/hda2       113226120   117210239     1992060   82  Linux swap / Solaris
/dev/hda3        12611025    43857449    15623212+  83  Linux
/dev/hda4        43857450   113226119    34684335    b  W95 FAT32

```

The only suspicion I have is that somehow the contents of /dev/hda4 have become 'glued' onto my root partition, since usage of root+usage of hda4 =reported size of hda3.

To make matters worse, my dvdwriter on this laptop has died, and so until buying an external drive, and trying to find out how to get BIOS to boot from it, my normal format/reinstall options are limited.

Any suggestions?
TIA

---

