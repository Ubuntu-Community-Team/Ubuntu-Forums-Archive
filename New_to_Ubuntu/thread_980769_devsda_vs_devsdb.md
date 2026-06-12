---
title: "/dev/sda vs dev/sdb"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by raedq on 2008-11-13
Hi All,

I am happy to be in a place where I am allowed to ask questions that are most definitely idiotic without being judged !! :)

What is the difference between sda and sdb? reason is:

I have recently (after 3 weeks of thorough trials) eradicated Vista (Happily) and have installed Ubuntu 8.10... during which i had to reset my laptop's partition table (160 GB) as follows:
1.  Dev/sda1 120 GB Mount point as /
2.  Dev/sda2  10 GB Swap (thinking bigger swap is faster)
3.  Dev/sda3  30 GB FAT32 (thinking i may need to install  windows one day !!!)

Now I have about 10 Gigs missing, plus using GPartEd i see that I have two drives /dev/sda and /dev/sdb with the same size, only dev/sdb is quite used !! can someone please explain?

Cheers,
Ray

---

### Post by kernelhaxor on 2008-11-13
sda and sdb just correspond to two different physical disks .. if you had a third, it would be sdc ..
sda1, sda2, sda2 would be logical partitions of the disk sda .. Similarly sdb1, sdb2 and so on for sdb ..and so on ..

---

### Post by raedq on 2008-11-13
> **kernelhaxor said:**
> sda and sdb just correspond to two different physical disks .. if you had a third, it would be sdc ..
sda1, sda2, sda2 would be logical partitions of the disk sda .. Similarly sdb1, sdb2 and so on for sdb ..and so on ..

Gotcha !! cheers :)

---

### Post by porchrat on 2008-11-13
> **raedq said:**
> Hi All,

I am happy to be in a place where I am allowed to ask questions that are most definitely idiotic without being judged !! :)

What is the difference between sda and sdb? reason is:

I have recently (after 3 weeks of thorough trials) eradicated Vista (Happily) and have installed Ubuntu 8.10... during which i had to reset my laptop's partition table (160 GB) as follows:
1.  Dev/sda1 120 GB Mount point as /
2.  Dev/sda2  10 GB Swap (thinking bigger swap is faster)
3.  Dev/sda3  30 GB FAT32 (thinking i may need to install  windows one day !!!)

Now I have about 10 Gigs missing, plus using GPartEd i see that I have two drives /dev/sda and /dev/sdb with the same size, only dev/sdb is quite used !! can someone please explain?

Cheers,
Ray

When you see "sda" it means SCSI Disk a, just as sdb means SCSI disk b and so on.  All HDDs use the linux SCSI drivers regardless of whether they are SATA, IDE or SCSI drives.

As for the larger swap = faster, that is not necessarily true.  Swap is the area of your hard drive that acts as virtual memory.  Meaning that when your RAM is full it starts placing stuff into the swap area on your harddrive.  Problem is swap is a lot slower than RAM and so never finctions as quickly.  Swap is important and keep in mind that you need at least as much swap as you have RAM in order to hibernate.  The amount of swap you need is dependant on how much RAM you have.

---

### Post by Duck2006 on 2008-11-13
> . Dev/sda2 10 GB Swap (thinking bigger swap is faster)

Far to big, 1 to 2Gb is large enough.

---

### Post by porchrat on 2008-11-13
hey I have a 10Gb swap area...but then again I have 8Gb of RAM and sometimes I do use most of it and then I want to hibernate...

---

### Post by snova on 2008-11-13
> **raedq said:**
> 2.  Dev/sda2  10 GB Swap (thinking bigger swap is faster)

If you're using swap at all, it'll be slower regardless of how much you have. The general rule of thumb is to have twice the amount of memory you have, so this is a bit silly.

---

