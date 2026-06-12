---
title: "ext2_fs.h issues"
date: 2010-02-16
forum: Programming Talk
---

### Post by newmatt on 2010-02-16
Hi all,

I am currently trying to include the ext2_fs header file and receiving several errors. Here's my program:

```
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>
#include <linux/ext2_fs.h>

int main (int argc, char * argv[])
{
    return 0;
}
```and the errors:
> 
In file included from showblock.c:4:
/usr/include/linux/ext2_fs.h: In function ‘ext2_mask_flags’:
/usr/include/linux/ext2_fs.h:182: error: ‘FS_DIRSYNC_FL’ undeclared (first use in this function)
/usr/include/linux/ext2_fs.h:182: error: (Each undeclared identifier is reported only once
/usr/include/linux/ext2_fs.h:182: error: for each function it appears in.)
/usr/include/linux/ext2_fs.h:182: error: ‘FS_TOPDIR_FL’ undeclared (first use in this function)
/usr/include/linux/ext2_fs.h:184: error: ‘FS_NODUMP_FL’ undeclared (first use in this function)
/usr/include/linux/ext2_fs.h:184: error: ‘FS_NOATIME_FL’ undeclared (first use in this function)
I have reinstalled the packages to no avail and am getting a bit flustered by this.

Any advice/fixes?

---

### Post by dwhitney67 on 2010-02-16
Yes; add an include for <linux/fs.h>

```

...
#include <linux/fs.h>
#include <linux/ext2_fs.h>

...

```

---

### Post by newmatt on 2010-02-16
Excellent. Thanks a lot.

---

### Post by kcwang on 2010-02-16
U no use innernet to complete assignment!

---

