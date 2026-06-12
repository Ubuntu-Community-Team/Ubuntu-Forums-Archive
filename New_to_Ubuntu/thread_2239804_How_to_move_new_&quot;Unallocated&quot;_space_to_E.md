---
title: "How to move new &quot;Unallocated&quot; space to Extended Partition via GParted?"
date: 2014-08-15
forum: New to Ubuntu
---

### Post by JeQhdMD on 2014-08-15
Hello all,

I could use some help in figuring out how to manage my 640 GiB hdd so that I can use some newly created "unallocated" disk space.  The unallocated space is the result of reducing the partition size where Windows 7 resides.   I already have 4 partitions (with Windows utilizing 3 of those), so, when I selected the unallocated space, I noticed the menu options for creating a new partition were "greyed out" or unavailable.  This is not an EFI/GPT disk.  My disk layout is as follows:

>   sda1 = ntfs 15 GiB (8.9 GiB used) (recovery Windows),
>   sda2 = ntfs 100 MiB (24.14 MiB used),
>   sda3 = ntfs 164 Gib (51,6 GiB used) (main Windows),
>   sda4 = Extended Partition Container with 3 logical partitions for Linux,
   >   sda7 = ext4 52.07 GiB (4.45 GiB used), (Xubuntu 14.04.1),
   >   sda5 = ext4 268.82 GiB (7.94 GiB used), (main Ubuntu 14.04.1),
   >   sda6 = swap 4 Gib aprox.

And now aprox 90 GiB of former ntfs that's "unallocated" space.

How do I merge the unallocated space into the Extended Partition container so I can create another Logical partition?

Thanks much for any tips.

---

### Post by egeezer on 2014-08-15
It looks like you shrank the sda3 to get your 90GiB.  You actually need to extend the sda4 patition backwards (to the left) into the unallocated space, which will give you space in the extended partition to start a new partition.  You can't use the Gparted in either of your Linux installs for the job, because the partition number you want to move is lower than those.  Use a LiveCD or PartedMagic or SystemRescu for the job.

---

### Post by JeQhdMD on 2014-08-15
Worked perfect!   Used my Feb 2014 version of Parted Magic.

Thanks again.  ):P

---

