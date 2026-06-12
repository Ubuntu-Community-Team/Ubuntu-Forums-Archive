---
title: "No Root File System Found"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by gc88 on 2013-06-22
This is my first time installing Ubuntu, so I'm not very familiar with hard drive partitioning. Right now, I'm trying to install it in a dual boot with Windows 8 by booting from the CD but it won't detect the Windows 8, so I have to manually partition it.

 From what I've read, Ubuntu needs an efi boot drive with 200 MB of space. But there is already an efi partition that exists and when I select it during the manual partitioning, it gives me an error saying no root file system found. So, I think I need to add a mount point (/boot/efi?) to the efi  partition, but I don't know how to do it and GParted doesn't seem to let me. I've already shrunk down the windows ntfs partition, but it still doesn't work. Also, could you give me some advice on how to partition the rest of the hard drive? Right now I have 4 partitions: sda1 ntfs 300 MB diag, sda2 fat32 260 MB boot (efi), sda3 unknown 128 MB msftres, ntfs 502.65 GB (windows storage), and 195.31 GB unallocated. Help would be much appreciated.

---

### Post by 3rdalbum on 2013-06-22
When you're using the manual partitioning, what mount points are you specifying? You must, at the very least, have one partition with the mount point set to /

I don't know about how things work with EFI, but if you haven't told Ubuntu which partition you want to use as the main system partition (/) it will give you the "no root file system defined" error message. So click the Edit button on that partition and set the mount point to /

---

### Post by CatKiller on 2013-06-22
You also already have four partitions there. That could be a problem.

And no Linux filesystems yet. You can't install into FAT or NTFS.

---

### Post by westie457 on 2013-06-22
Which version did you burn to CD 32-bit or 64-bit?

The 32-bit version will not detect UEFI. See here for more details. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

