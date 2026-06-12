---
title: "changing the data block"
date: 2009-03-04
forum: Programming Talk
---

### Post by aishwarya on 2009-03-04
Hi all,i am currently working in Linux v2.6.26..by using debugfs command,we will get the block numbers of an inode,..i want to know how the block numbers are assigned to data blocks and whether shall i change the block number of a particular data block....is there any function available?..if so,how to use that function?...

---

### Post by Zugzwang on 2009-03-04
Question: Why do you want to do that?

Anyway, see here: [http://en.wikipedia.org/wiki/E2fsprogs](http://en.wikipedia.org/wiki/E2fsprogs) - There's some program named "debugfs" available. That should help you.

---

