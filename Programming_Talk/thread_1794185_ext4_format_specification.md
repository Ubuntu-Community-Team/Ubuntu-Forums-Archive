---
title: "ext4 format specification"
date: 2011-06-30
forum: Programming Talk
---

### Post by YesWeCan on 2011-06-30
Does anyone know the whereabouts of the ext4 format specification?

I specifically want to know how to use the superblock and group descriptor block to navigate the directory files.

Many thanks.

---

### Post by nvteighen on 2011-06-30
> **YesWeCan said:**
> Does anyone know the whereabouts of the ext4 format specification?

I specifically want to know how to use the superblock and group descriptor block to navigate the directory files.

Many thanks.

No idea about this, but if you want that you're surely doing pretty low-level programming there... Normally, you can navigate directories using the POSIX API (opendir and friends).

---

### Post by megabytemonster on 2011-07-01
This may prove helpful: [https://ext4.wiki.kernel.org/index.php/Main_Page](https://ext4.wiki.kernel.org/index.php/Main_Page)

---

### Post by YesWeCan on 2011-07-01
Thanks. I had a look around but it is all very high-level, except for "ext4 on-disk layout" which provides maybe 70% of what I need but seems to be missing some rather vital information, such as what the method is for navigating. I assume the author thought this was obvious, but unfortunately it is not obvious to me. There are details missing like the units of measurement of certain fields, such as the inodes table address...I have looked at the numbers in my real partition and they are too big to represent even an absolute byte address. The content of directory blocks is defined but there is no explanation of where they are or how to find them.

For instance, how does one find the sector address of the start of a file by filename? Seems like one of the most likely operations. But I can not work out how to use the information in the only two blocks whose locations are fixed, the group 0 superblock and the first group descriptor block, to find anything else. Does one somehow find the inodes table, then look for an inode that represents a directory, then scan the directory for a file name which in turn gives an inode number that one uses to find the extent tree to locate the file blocks? If that is how it is meant to be used I don't know how to get the thing started.

There has to be a formal ext4 format specification, presumably online as it is all open-source, etc?

Help. :)

---

### Post by YesWeCan on 2011-07-04
Solved. I had to figure it out by rolling my sleeves up and reverse-engineering it. A real pain. I find the info on wiki.kernel is incomplete and is not consistent with how ext4 really works. So I had to spend a lot of time staring at the hexdump of a real ext4 file-system while executing and modifying code to navigate it.

---

