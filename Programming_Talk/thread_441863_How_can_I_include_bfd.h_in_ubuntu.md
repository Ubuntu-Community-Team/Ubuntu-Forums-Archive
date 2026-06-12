---
title: "How can I include bfd.h in ubuntu"
date: 2007-05-13
forum: Programming Talk
---

### Post by yinglcs2 on 2007-05-13
Hi,

I am trying to compile a program in ubuntu, but it failes when it can't find bfd.h.

I have use 'sudo apt-get install libcwd-dev' , but the compilation still failed.

Any help is appreciated.



gcc -pipe -Wall -Wreturn-type -fno-exceptions -Winline -Wdisabled-optimization -Wno-unused-parameter -Wreturn-type -fmessage-length=0  -march=i686 -O0 -g -DDEBUG -D_DEBUG  -I../../../common/runtime/pub -I/usr/X11R6/include -I../../../common/fileio/pub/platform/unix -I../../../common/netio/pub/platform/unix -I../../../server/common/netio/pub/platform/unix -Ipub/platform/unix -I../../../common/include -I../../../common/container/pub -I../../../common/dbgtool/pub -I../../../common/fileio/pub -I../../../common/netio/pub -I../../../common/system/pub -I../../../common/util/pub -I../../../server/include -I../../../server/common/fileio/pub -I../../../server/common/netio/pub -I../../../server/common/struct/pub -I../../../server/engine/config/pub -I../../../server/engine/context/pub -I../../../server/engine/core/pub -I../../../server/engine/dataflow/pub -I../../../server/engine/netio/pub -I../../../protocol/common/util/pub -I./pub -I. -include dbg/server_common_util_make_lib_ribodefs.h -fPIC -DPIC -o dbg/obj/make_lib/trace.o -c trace.c
trace.c:203:17: error: bfd.h: No such file or directory
trace.c:204:1: warning: "__USE_GNU" redefined
In file included from /usr/include/stdio.h:28,
                 from trace.c:200:
/usr/include/features.h:270:1: warning: this is the location of the previous definition

---

### Post by po0f on 2007-05-13
yinglcs2,

The package you installed came with a pkg-config file; it's beyond me why whatever you're compiling isn't using it.  Add `pkg-config libcwd --cflags` to any includes and `pkg-config libcwd --libs` to any libraries used in this program's Makfile and you should be fine.

---

### Post by yinglcs2 on 2007-05-13
Thanks. Is there some environment variables I can set to fix this?
I think this program has lot of Makefiles, and i am not sure how to fix all of them.

---

### Post by yinglcs2 on 2007-05-13
Can I set the pkconfig to point to a right directory to solve my problem? if yes, what should be my pkconfig set to for bfd.h ?

Thank you.

---

