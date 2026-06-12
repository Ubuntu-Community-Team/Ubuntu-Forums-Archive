---
title: "ext3 filesystem programming (c[++])"
date: 2011-02-22
forum: Programming Talk
---

### Post by dozy on 2011-02-22
hey everyone,

i've spent the last couple days scouring the internet for information on the down-and-dirty workings of ext3. i keep finding conceptual information regarding superblocks and inodes, but have yet to find exactly what i need.

i'm looking for the information i would need to write my own ext3 driver; but that's not what i'm doing.. well, not fully anyway.
i understand superblocks, inodes, etc. but i need information about how/where the information is actually stored on disk and how to follow the chain to the actual data.

here are the things i want to try to program for myself, without the help of the ext3 kernel driver or the normal c[++] libraries:
- search a block device (ext3) for an existing file.
- list all files
- return file attributes
- return file data

just to be clear, i'm not talking about how to search for, open and retrieve data from files - the normal way - using c[++] (ie. fopen, stat, etc...).

can anyone point me to information that could help me?

thank you, and happy coding.

---

### Post by foxmuldr on 2011-03-02
> **dozy said:**
> hey everyone,

i've spent the last couple days scouring the internet for information on the down-and-dirty workings of ext3. i keep finding conceptual information regarding superblocks and inodes, but have yet to find exactly what i need.

i'm looking for the information i would need to write my own ext3 driver; but that's not what i'm doing.. well, not fully anyway.
i understand superblocks, inodes, etc. but i need information about how/where the information is actually stored on disk and how to follow the chain to the actual data.

here are the things i want to try to program for myself, without the help of the ext3 kernel driver or the normal c[++] libraries:
- search a block device (ext3) for an existing file.
- list all files
- return file attributes
- return file data

just to be clear, i'm not talking about how to search for, open and retrieve data from files - the normal way - using c[++] (ie. fopen, stat, etc...).

can anyone point me to information that could help me?

thank you, and happy coding.

Download the Linux kernel source and you'll find everything you need there in a file like "ext3.c".

- Rick C. Hodgin

---

### Post by ssam on 2011-03-02
could also look at something like
[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

---

### Post by WritZ on 2012-01-01
[[COLOR="Red"]HERE[/COLOR]]("http://sourceforge.net/projects/gparted/files/gparted/") you will get the GParted Source and can find the files like "ext2.cc"[with Header : "ext2.h"] and more ext file system sources....

---

