---
title: "wierd file stat problem"
date: 2007-10-13
forum: Programming Talk
---

### Post by bmvbab on 2007-10-13
I have some files in the fs sub directory of the latest kernel source which produce a long listing as follows:

total 0
?--------- ? ? ? ?                ? fcntl.c
?--------- ? ? ? ?                ? fifo.c
?--------- ? ? ? ?                ? filesystems.c
?--------- ? ? ? ?                ? file_table.c
?--------- ? ? ? ?                ? freevxfs

So Im not able to delete them, or change perms or ownership even as root :(

Not sure if the problem is from the repo or just on my machine....
Noticed it when my kernel compilation failed....

Any ideas on removing these?

---

### Post by bmvbab on 2007-10-13
did an fsck and it solved it....thanks

---

