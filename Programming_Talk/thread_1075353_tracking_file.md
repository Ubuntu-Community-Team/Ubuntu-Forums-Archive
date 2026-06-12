---
title: "tracking file"
date: 2009-02-20
forum: Programming Talk
---

### Post by veda87 on 2009-02-20
i need to keep an record of each and every file that has been created. how can i do it. if i know the absolute pathname for the files, i can easily path walk through it. but i can't trace the absolute pathname.

i am using linux-2.6.26 and working on ext2 file system.

can anyone tell me how to keep track. or any suggestions please. 
so please help me....

---

### Post by Ferrat on 2009-02-20
Just guessing here but I would think you need to look in to a module or something that hooks the kernel calls for filehandling from:
**[http://www.kevinboone.com/linux_kernel_file_0.html](http://www.kevinboone.com/linux_kernel_file_0.html)**
> The Filesystem layer. The filesystem layer converts the high-level operations understood by VFS -- reading, writing, etc. -- into low-level operation on disk blocks (or whatever the storage medium happens to be). However, because most disk filesystems are essentially similar, VFS also provides generic filesystem handling code. Specific filesystems are free to make use of this generic code (most do), or do all the work themselves. Most of this code is in the fs/ directory, along with the other VFS stuff, but some is in mm/ with the virtual memory management infrastructure. 
but for ext2 the ofc.
As I say it's just a guess but shouldn't be that hard to just hook the message and print it to a log file.

---

### Post by veda87 on 2009-02-24
i got the absolute pathaname.... i got it through the function
char *dentry_path(struct dentry *dentry, char *buf, int buflen) which is defined in fs/dcache.c

it gives the pathname of the file from the root of the filesystem.....

---

