---
title: "libnl-3-dev Includes broken?"
date: 2012-12-03
forum: Programming Talk
---

### Post by Beliar on 2012-12-03
Hello everyone,
I am trying to use libnl 3 ([http://www.infradead.org/~tgr/libnl/](http://www.infradead.org/~tgr/libnl/)), a library to conviniently use the netlink interface to the kernel.

But I can't even compile my firs test program. I am including "libnl3/netlink/netlink.h" but I get the error:

```
In file included from netlink_test.c:11:0:
/usr/include/libnl3/netlink/netlink.h:24:36: fatal error: netlink/netlink-compat.h: No such file or directory
compilation terminated.
```

netlink.h is including netlink/netlink-compat.h, but there is no folder netlink in /usr/include/.
There is just /usr/include/libnl3/netlink"

So including netlink/netlink.h also fails.

Am I missing something or is libnl-3-dev broken?

Cheers,
Ben

N.B.:

I have the following packages installed:

libnl-3-200
libnl-3-200-dbg
libnl-3-dev
libnl-3-doc
libnl-genl-3-200
libnl-genl-3-200-dev
libnl-route-3-200
libnl-route-3-200-dev

---

### Post by Zugzwang on 2012-12-03
The problem you are facing is that "libnl3" is not supposed to be used this way. This can be seen from the fact that "/usr/include/libnl3/netlink/netlink.h" tries to include "netlink/netlink-compat.h", which resides in "/usr/include/libnl3". So it is assuming that the directory "/usr/include/libnl3" is in the list of so-called include directories of the compiler. The compiler searching in these paths when looking for header files.

So you have to ensure that "/usr/include/libnl3" is added to the list of include paths. Deending on your build chain, this is done differently. If you are compiling from the terminal, you would simply add "-I /usr/include/libnl3" to the compilation command. If you are using a Makefile, you have to add that to the right place in the file. Many build systems used by IDEs have some fields in the project settings for this.

Note that there is a tool called "pkg-config", which manages include paths and library files to link against for many libraries. Look it up on google and check if pkg-config is supported by libnl3. If yes, try to use the plenty of documentation available on using pkg-config for your choice of build system.

---

