---
title: "Disk usage"
date: 2007-04-01
forum: Programming Talk
---

### Post by eshober on 2007-04-01
I need to get disk statistics in a program I'm porting from Windows. Specifically, I need to know how to find the filesystem that a given pathname belongs to and how much space is available on that filesystem. I'm having trouble finding a lib or system calls to support this requirement. Does anyone know what I can use?

---

### Post by ubuntu27 on 2007-04-01
I think there was an app called Disk usage Manager.

---

### Post by enopepsoo on 2007-04-01
try xdiskusage, it is cool.:guitar:

---

### Post by WW on 2007-04-01
The library function **statfs** returns information about a file system.  Check out **man statfs**.

For example:
```

/* fstest.c */

#include <sys/statfs.h>
#include <errno.h>
#include <stdio.h>

int main(int argc, char **argv)
    {
    struct statfs s;
    int e;

    if (argc != 2)
        {
        fprintf(stderr,"use: fstest filesystem\n");
        return -1;
        }
    e = statfs(argv[1], &s);
    if (e != 0)
        printf("statfs failed; errno = %d\n", errno);
    else
        {
        printf("Results of statfs for %s\n",argv[1]);
        printf("%10d block size\n",s.f_bsize);
        printf("%10ld total data blocks\n", s.f_blocks);
        printf("%10ld free blocks\n",s.f_bfree);
        printf("%10ld free blocks available to non-superuser\n",s.f_bavail);
        printf("%10ld total file nodes\n",s.f_files);
        printf("%10ld free file nodes\n",s.f_ffree);
        }
    return 0;
    }

```
Compile and run, and compare the output to the df command:
```

$ gcc -Wall fstest.c -o fstest
$ ./fstest /
Results of statfs for /
      4096 block size
   3605336 total data blocks
   2865519 free blocks
   2682379 free blocks available to non-superuser
   1831424 total file nodes
   1744030 free file nodes
$ df --block-size=4096 /
Filesystem           4K-blocks      Used Available Use% Mounted on
/dev/hda1              3605336    739817   2682379  22% /

```

---

### Post by eshober on 2007-04-02
Thanks to all for the responses. WW's response was exactly what I was looking for. For some reason I had fstat stuck in my brain. Neither my gray matter, nor man -k could find what WW so kindly provided. The statfs call was just the thing. Thank again!

---

