---
title: "Hard disk partitions"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by GeordieJedi on 2008-09-20
Hi everyone. Hope your all taking it easy.

Quick question, at the moment I Ubuntu cant see one of my XP
partitions on my 1st internal drive. It's the D: partition.

I'm going to re-install Ubuntu 8.04.01. What selection do I
need to make in order to let Ubuntu See my D: partition?

Do I mount it as /windows or as /DOS? in the installation setup.


System setup =

Dual boot XP / Ubuntu 8.4

HD #1 =
C: XP
D: Downloads
E: Extra apps for XP

HD #2 =
Partition # 1 = Root
Partition # 2 = Swap
Partition # 3 = Home

HD # 3 (External)

A buch of partitions. which includes my main data partition
which I use to store all of my data between both OS's.


Any help/advice is appreciated.

Thanks

---

### Post by vanadium on 2008-09-20
Rather than reinstalling Ubuntu, load Windows, have the partition checked with the windows tools, then exit Windows completely (shut down, no hibernate) before starting Ubuntu. Next time, Ubuntu will be able to mount it automatically.

In Hardy, ntfs partitions are mounted "on demand". If you would rather want the partition to be available on startup (I would because it is a "Downloads" partition), then you can mount it "the old way", i.e. through /etc/fstab. If you post the output of the commands

```

sudo fdisk -l
cat /etc/fstab

```

we can give precise instructions for your case.

---

