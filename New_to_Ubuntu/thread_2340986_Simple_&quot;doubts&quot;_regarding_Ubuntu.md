---
title: "Simple &quot;doubts&quot; regarding Ubuntu"
date: 2016-10-24
forum: New to Ubuntu
---

### Post by jkepler on 2016-10-24
Hi,

I've just made a clean install of Ubuntu with a dual boot with Windows 7 - all seems perfect.

No I have some doubts...would someone be so kind to assist me?

- First of all, I wish to copy some files I had in windows 7 to a directory in Ubuntu (in a pen, for instance). Can I, for example, copy them to an USB flash drive in Windows and copy that content in Ubuntu? My doubt here is that Windows works in NTFS mode, but Ubuntu in FAT32...And windows tryes to format any flash drive that it's in fat32.

- I made a too small partition for Ubuntu. If I free some more Gigabytes in Windows main disk (c:), how can I give them to Ubuntu? (the easiest way please) Or must I reinstall Ubuntu again?

Sorry for the trouble.

Kind regards,

JKepler

---

### Post by sudodus on 2016-10-24
Welcome to the Ubuntu Forums :-)

In a dual boot system you can mount the Windows partition and read from it directly into linux. It is even possible to write into the Windows partition, but not recommended.

Many people create a separate **data** partition 'between' Windows and linux, and create an NTFS partition table in that partition. Data can be read and written by both operating systems, so effectively shared, in such a data partition.

If you use a separate data partition, it should be enough with 20 GB for linux, but you might want 40 GB.

I suggest that boot into Windows and

1. Turn off fast boot, which is a kind of hibernation, that can cause problems in dual boot systems.

2. Shrink the Windows partition from Windows. Do not create the new partitions, just leave the freed drive space 'unallocated'.

Leave a fair amount of free space in Windows for future updates and upgrades. If too little space, it will soon get very defragmented, so leave for example 25% free space in the Windows partition.

3. Boot from the Ubuntu install drive, use gparted to create the partitions that you want:

- data partition with NTFS 

- root partition for linux with ext4 (>= 20 GB)

- swap partition for linux (linux swap), size >= RAM size in GIB, so for example 4 GiB RAM --> 4,8 GB swap, if you intend to hibernate. Otherwise I think 2 GB swap is good.

4. Run the Ubuntu installer, and at the partitioning page, select ***Something else*** and select the partition intended as root partition. It will select the swap partition automatically.

---

### Post by T.J. on 2016-10-24
> **jkepler said:**
> Hi,

I've just made a clean install of Ubuntu with a dual boot with Windows 7 - all seems perfect.

No I have some doubts...would someone be so kind to assist me?

- First of all, I wish to copy some files I had in windows 7 to a directory in Ubuntu (in a pen, for instance). Can I, for example, copy them to an USB flash drive in Windows and copy that content in Ubuntu? My doubt here is that Windows works in NTFS mode, but Ubuntu in FAT32...And windows tryes to format any flash drive that it's in fat32.

- I made a too small partition for Ubuntu. If I free some more Gigabytes in Windows main disk (c:), how can I give them to Ubuntu? (the easiest way please) Or must I reinstall Ubuntu again?

Sorry for the trouble.

Kind regards,

JKepler

First, welcome!  I hope you find your time here with the community pleasant and that you decide to stick with Linux.

To answer your questions, Linux can read and write Windows NTFS drives natively. In most cases, it should work out of the box, just use your file manager to open them.  To expand your partition, it depends on your original install, so I cannot answer that question directly without more information.  USB flash drives are usually formatted in FAT32 as per UEFI boot specification.  Microsoft helped design UEFI, and so FAT32 was chosen as the default bootloader format.  Definitely not my first choice, but it works well enough.

---

