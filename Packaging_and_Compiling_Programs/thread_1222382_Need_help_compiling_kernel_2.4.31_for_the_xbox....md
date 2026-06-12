---
title: "Need help compiling kernel 2.4.31 for the xbox..."
date: 2009-07-24
forum: Packaging and Compiling Programs
---

### Post by bc54 on 2009-07-24
ok, so i need help compiling the 2.4.31 kernel on xubuntu 9.04.

i am trying to compile a minilinux kernel for the xbox that is based off of a vanilla 2.4.31 kernel. i can successfully "make oldconfig" and "make dep" without error, but when i run "make bzImage" i get the following error:
```
root@spencer-desktop:/usr/src/linux-2.4.31# make bzImage
gcc -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -o scripts/split-include scripts/split-include.c
scripts/split-include.c: In function ‘main’:
scripts/split-include.c:133: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scripts/split-include include/linux/autoconf.h include/config
gcc -D__KERNEL__ -I/usr/src/linux-2.4.31/include -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -fomit-frame-pointer -pipe -mpreferred-stack-boundary=2 -march=i686 -fno-unit-at-a-time   -DKBUILD_BASENAME=main -c -o init/main.o init/main.c
In file included from /usr/src/linux-2.4.31/include/linux/prefetch.h:13,
                 from /usr/src/linux-2.4.31/include/linux/list.h:6,
                 from /usr/src/linux-2.4.31/include/linux/wait.h:14,
                 from /usr/src/linux-2.4.31/include/linux/fs.h:12,
                 from /usr/src/linux-2.4.31/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.31/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.31/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.31/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.31/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.31/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.31/include/asm/processor.h:75: error: array type has incomplete element type
In file included from /usr/src/linux-2.4.31/include/linux/fs.h:322,
                 from /usr/src/linux-2.4.31/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.31/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.31/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.31/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.31/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.31/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.31/include/linux/ncp_fs_i.h:26: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.31/include/linux/ncp_fs_i.h:27: warning: ‘packed’ attribute ignored for field of type ‘__u8[6]’
In file included from /usr/src/linux-2.4.31/include/linux/ncp_mount.h:12,
                 from /usr/src/linux-2.4.31/include/linux/ncp_fs_sb.h:12,
                 from /usr/src/linux-2.4.31/include/linux/fs.h:735,
                 from /usr/src/linux-2.4.31/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.31/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.31/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.31/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.31/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.31/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.31/include/linux/ncp.h:24: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.31/include/linux/ncp.h:25: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.31/include/linux/ncp.h:26: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.31/include/linux/ncp.h:27: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.31/include/linux/ncp.h:28: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.31/include/linux/ncp.h:29: warning: ‘packed’ attribute ignored for field of type ‘__u8[]’
/usr/src/linux-2.4.31/include/linux/ncp.h:37: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.31/include/linux/ncp.h:38: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.31/include/linux/ncp.h:39: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.31/include/linux/ncp.h:40: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.31/include/linux/ncp.h:41: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.31/include/linux/ncp.h:42: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.31/include/linux/ncp.h:43: warning: ‘packed’ attribute ignored for field of type ‘__u8[]’
/usr/src/linux-2.4.31/include/linux/ncp.h:137: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.31/include/linux/ncp.h:138: warning: ‘packed’ attribute ignored for field of type ‘__u8[256]’
/usr/src/linux-2.4.31/include/linux/ncp.h:174: warning: ‘packed’ attribute ignored for field of type ‘__u8’
In file included from /usr/src/linux-2.4.31/include/asm/smp.h:17,
                 from init/main.c:74:
/usr/src/linux-2.4.31/include/asm/mpspec.h:87: warning: ‘packed’ attribute ignored for field of type ‘unsigned char[6]’
init/main.c: In function ‘start_kernel’:
init/main.c:367: warning: format not a string literal and no format arguments
make: *** [init/main.o] Error 1
```

i looked up that error, and i found 1 post on the linux forums, but the advice was that it might be a bad download. also, its not a problem caused by xbox specific patches, because i get the same error without patching the source. any ideas?

---

