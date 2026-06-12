---
title: "Word docs wouldn't open, then disappeared - not in Rubbish Bin :-("
date: 2015-05-18
forum: New to Ubuntu
---

### Post by ned5 on 2015-05-18
In Pangolin, Word docs on the desktop suddenly became unopenable (with libre office writer or wordpad), though not immediately after updates, then suddenly just vanished (possibly because the disk was showing as short of memory, and it tried to save it? In fact there was ~800 Mb free! Also wouldn't let other partitions mount due to insufficient space - could there be a virus on board?).

The documents are not in the Rubbish Bin, nor can I find them with ordinary 'Search' on my three main partitions, and I'm reluctant to install a special 'Search' in case I overwrite them.

I'm running Pangolin, with a Linux (0x83) Ext4 (version 1.0) partition /dev/sda2 device mounted at / (with an underscore touching the bottom bit) according to 'Disk Utility'; sda1 is a W95 FAT32 (LBA) (0x0c) partition, which is never used.

I'd welcome some help please, as it's my diary that's gone.

Many thanks.

Regards,
Ned.

---

### Post by jones quest on 2015-05-19
Hi Ned,

It's doubtful you have a virus. Your symptoms (unopenable and dissapearing files) however  are typical to a failing hard drive (mechanical failure).

I recommend backing up your precious files or the whole hard drive (ddrescue). Even if the document files are no longer visible doesn't mean the data is gone forever. You can recover deleted files with PhotoRec or TestDisk. 

Boot into a live CD/USB, and copy your data to another hard drive. System rescue CD is a good choose. Once your data is safe you can diagnose your hard drive if it's truly dying.

Hope you find your lost files.

---

