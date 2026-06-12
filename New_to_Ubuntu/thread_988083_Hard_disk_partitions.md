---
title: "Hard disk partitions"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by teranex on 2008-11-20
Currently I have Ubuntu installed with Wubi on a NTFS partition. Since i really like Ubuntu (and don't like Windows so much ;)), i want to install Ubuntu as my only OS on the computer.
I currenly have two hard disks in my machine, with a few partitions (all formatted in NTFS):

```

disk1
* C: 25GB "SYSTEM"     (contains windows)
* E: 45GB "DATA"       (contains al my documents, mail etc)
disk2
* D: 30GB "BACKUP"     (contains backups from "DATA" & websites)
* G: 90GB "MULTIMEDIA" (contains audio and video files)

```

To install Ubuntu, i would obviously use my first partition on disk1 (C: ) and i was thinking about splitting it up into 3 pieces for "/", "/home" and the swap. So my disks layout would become:

```

disk1
* /                 20GB (ext3)
* /home              4GB (ext3)
* swap               1GB (i currently have 512MB ram)
* /media/DATA       45GB (ntfs) (this partition stays untouched)
disk2
* /media/BACKUP     30GB (ntfs) (this partition stays untouched)
* /media/MULTIMEDIA 90GB (ntfs) (this partition stays untouched)

```

The first few months i'd like to keep most partitions in NTFS to make it a little easier in the (unlikely) case that i would like to go back to Windows.
I kind of like the idea to keep the /home folder sperate from the place where I really store my documents, that way my home folder is more like a place where settings are stored (and i can alwasy create a softlink in my home folder to the other partition). Therefore I think 4GB will be enough for /home (i'm the only user of the computer)

Does this make any sence?

thx!

---

### Post by Dedoimedo on 2008-11-20
Hello,

Looks good, except I'd give 10GB to root and 14GB to home.
You don't need that much for root, unless you plan to install everything. Having a large-ish home is good, especially for backups, but then, you do have these other partitions you can use.

You may want to consider leaving only a single ntfs partition and using others as ext3, since the Linux filesystem is superior to ntfs.

Dedoimedo

---

### Post by teranex on 2008-11-20
> **Dedoimedo said:**
> Hello,

Looks good, except I'd give 10GB to root and 14GB to home.
You don't need that much for root, unless you plan to install everything. Having a large-ish home is good, especially for backups, but then, you do have these other partitions you can use.

You may want to consider leaving only a single ntfs partition and using others as ext3, since the Linux filesystem is superior to ntfs.

Dedoimedo
Thanks! I plan to convert all my partitions to ext3 once I'm using Ubuntu as my sole OS, but i'd like to wait a few weeks/months with that just to "feel safe" that i can easily switch back to windows (i have been using windows for 10 years now and never really used linux before, so completely switching is a big step :))

---

