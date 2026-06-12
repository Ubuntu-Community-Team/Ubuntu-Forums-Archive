---
title: "difference in size of blocks by stat and ls -ls"
date: 2010-09-27
forum: Programming Talk
---

### Post by piyush.neo on 2010-09-27
Why is there difference in size of file in terms of block by the two commands - ls and stat..???
```
[user@linux ~]$ stat pro.c
  File: `pro.c'
  Size: 469             Blocks: 8          IO Block: 4096   regular file
Device: 802h/2050d      Inode: 916696      Links: 1
Access: (0664/-rw-rw-r--)  Uid: (  500/    user)   Gid: (  500/    user)
Access: 2010-09-27 22:31:43.000000000 +0530
Modify: 2010-09-21 22:17:35.000000000 +0530
Change: 2010-09-21 22:17:35.000000000 +0530


[user@linux ~]$ ls -ls pro.c
4 -rw-rw-r-- 1 user user 469 Sep 21 22:17 pro.c
[user@linux ~]$ 

```

---

### Post by amauk on 2010-09-27
Because you're not actually measuring the same thing
stat works on the block device
ls works on the filesystem

The disk has a natural "block size" (which is usually 512 bytes)
The filesystem has another different block size (usually a multiple of the disk blocksize)

If you change the ls command to this
```
ls -ls --block-size=512 pro.c
```
it should match the stat block size

---

