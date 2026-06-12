---
title: "Reinstallation with Hardy Heron"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by magicman5421 on 2008-04-24
I would like to reinstall the OS on my computer to be Hardy Heron from Gutsy Gibbon. Right now I am running a HP DV9500 laptop with 2 hard drives.
1st:
Partition 1: NTFS Windows Vista
Partition 2: Recovery Partition
2nd:
Partition 1: 30 GB FAT32 partition for file exchanges
Partition 2: 120 GB ext3 Ubuntu 7.10 Gutsy partition
Partition 3: 5 GB swap partition

I would like to back up my Gutsy partition in case I want to put gutsy back on my computer. Is there any way I can ghost the 2nd hard drive onto an external drive and recover it in case Hardy doesn't perform well? I noticed in GParted there is a "copy" feature, could this be used? Or would I have to use a different piece of software? I have a 320 GB external that I could partition/use to backup.
BTW I don't want to upgrade so don't suggest it.

---

### Post by Bodsda on 2008-04-24
in a terminal type       

```
man dd
```

or check out 

[http://www.partimage.org]("http://www.partimage.org")

---

### Post by Paqman on 2008-04-24
Partimage or Clonezilla are both good for cloning partitions. They're both available as LiveCDs, too.

---

