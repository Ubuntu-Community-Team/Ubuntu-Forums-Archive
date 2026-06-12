---
title: "[SOLVED] Rewriting to a block on disk?"
date: 2008-04-15
forum: Programming Talk
---

### Post by era86 on 2008-04-15
I am working on a project in C working with the Ext2 FS and I want to write some data stored in a variable back to the disk.  For example:

I read in data from disk into a buffer:

read( disk, 1024, buf );

Cast the buffer:

BLOCK_INFO * block;
block = (BLOCK_INFO *)buf;

Make some changes:

block->name = "askdjf"
block->var = 34;

Now I want to rewrite this to the disk.  Will this work?

strcpy( buf, (char *)block );
write (...)

What I have currently compiles, but I don't think it works correctly.  Any feedback helps.  Thanks!

---

### Post by era86 on 2008-04-18
Stupid mistake.  I guess I can just write buf right back to the disk.  Since "block" essentially points to "buf", any changes to "block" is done to "buf" as well.  Should've known.

---

