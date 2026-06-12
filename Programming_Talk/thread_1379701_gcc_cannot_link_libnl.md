---
title: "gcc cannot link libnl"
date: 2010-01-12
forum: Programming Talk
---

### Post by cuthbertkao on 2010-01-12
Hi folks,

   I am newbie to linux application programming and got a problem of linking standard library 'libnl.so'. Here my test code:

```

#include <netlink/netlink.h>
#include <netlink/genl/genl.h>
#include <netlink/genl/ctrl.h>

int main() {
    struct nl_handle *sock;
    int family;

    // Allocate a new netlink socket
    sock = nl_handle_alloc();
}

```

Then, compile and link my code with libnl:

> 
$ gcc test.c 
/tmp/ccJh2gSl.o: In function `main':
test.c:(.text+0x12): undefined reference to `nl_handle_alloc'
collect2: ld returned 1 exit status


However, the paths of header file and library were included already. still don't know why couldn't compile it??
> 
$ gcc -v test.c 
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 
COLLECT_GCC_OPTIONS='-v' '-mtune=generic'
 /usr/lib/gcc/i486-linux-gnu/4.3.3/cc1 -quiet -v test.c -D_FORTIFY_SOURCE=2 -quiet -dumpbase test.c -mtune=generic -auxbase test -version -fstack-protector -o /tmp/ccMicv7a.s
ignoring nonexistent directory "/usr/local/include/i486-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../i486-linux-gnu/include"
ignoring nonexistent directory "/usr/include/i486-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/gcc/i486-linux-gnu/4.3.3/include
 /usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed
[COLOR="Red"] /usr/include[/COLOR]
End of search list.
GNU C (Ubuntu 4.3.3-5ubuntu4) version 4.3.3 (i486-linux-gnu)
	compiled by GNU C version 4.3.3, GMP version 4.2.4, MPFR version 2.4.0.
GGC heuristics: --param ggc-min-expand=98 --param ggc-min-heapsize=128351
Compiler executable checksum: 0bf5703b57e064ca90b48f4e2c186f4a
COLLECT_GCC_OPTIONS='-v' '-mtune=generic'
 as -V -Qy -o /tmp/cckXhlcm.o /tmp/ccMicv7a.s
GNU assembler version 2.19.1 (i486-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.19.1
COMPILER_PATH=/usr/lib/gcc/i486-linux-gnu/4.3.3/:/usr/lib/gcc/i486-linux-gnu/4.3.3/:/usr/lib/gcc/i486-linux-gnu/:/usr/lib/gcc/i486-linux-gnu/4.3.3/:/usr/lib/gcc/i486-linux-gnu/:/usr/lib/gcc/i486-linux-gnu/4.3.3/:/usr/lib/gcc/i486-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/i486-linux-gnu/4.3.3/:/usr/lib/gcc/i486-linux-gnu/4.3.3/:/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/:/lib/../lib/:/usr/lib/../lib/:/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../:/lib/:[COLOR="red"]/usr/lib/[/COLOR]
COLLECT_GCC_OPTIONS='-v' '-mtune=generic'
 /usr/lib/gcc/i486-linux-gnu/4.3.3/collect2 --eh-frame-hdr -m elf_i386 --hash-style=both -dynamic-linker /lib/ld-linux.so.2 -z relro /usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o /usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.3.3/crtbegin.o -L/usr/lib/gcc/i486-linux-gnu/4.3.3 -L/usr/lib/gcc/i486-linux-gnu/4.3.3 -L/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/i486-linux-gnu/4.3.3/../../.. /tmp/cckXhlcm.o -lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc/i486-linux-gnu/4.3.3/crtend.o /usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crtn.o
/tmp/cckXhlcm.o: In function `main':
test.c:(.text+0x12): undefined reference to `nl_handle_alloc'
collect2: ld returned 1 exit status


Search the header file and library:

> 
$ ls /usr/include/netlink/*
/usr/include/netlink/addr.h       /usr/include/netlink/list.h            /usr/include/netlink/object.h
/usr/include/netlink/attr.h       /usr/include/netlink/msg.h             /usr/include/netlink/socket.h
/usr/include/netlink/cache-api.h  /usr/include/netlink/netlink-compat.h  /usr/include/netlink/types.h
/usr/include/netlink/cache.h     [COLOR="Red"] /usr/include/netlink/netlink.h[/COLOR]         /usr/include/netlink/utils.h
/usr/include/netlink/data.h       /usr/include/netlink/netlink-kernel.h
/usr/include/netlink/handlers.h   /usr/include/netlink/object-api.h

/usr/include/netlink/fib_lookup:
lookup.h  request.h

/usr/include/netlink/genl:
ctrl.h  family.h  genl.h  mngt.h

/usr/include/netlink/route:
addr.h        classifier-modules.h  link.h       nexthop.h        route.h  sch
class.h       class-modules.h       neighbour.h  qdisc.h          rtnl.h   tc.h
classifier.h  cls                   neightbl.h   qdisc-modules.h  rule.h
$ ls /usr/lib/libnl*
[COLOR="red"]/usr/lib/libnl.so[/COLOR]  /usr/lib/libnl.so.1  /usr/lib/libnl.so.1.1


> $ gcc --version
gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3

libnl installation info:
libnl-1.1.so
libnl-dev
libnl-doc

The header file and library seem to be in the right place but why I can not link the library successfully?? 
Is there any one know where I was wrong or missed? Thanks in advance.

Cuthbert

---

### Post by Senesence on 2010-01-13
Well, I don't think you're linking with the actual library.

To link with a library, you have to include the path to that specific library as an additional argument.

So, try doing this:

```
gcc test.c /usr/lib/libnl.so
```

---

### Post by Some Penguin on 2010-01-13
gcc might know about the directory, but it's not going to assume which library you meant.  Specify it (with -L).

---

### Post by cuthbertkao on 2010-01-13
Thanks a lot for your answers.

I just tried out the same result and the reason is just like all you said: specify the library.

I wrote a simple Makefile for this:
```
CC = gcc

srcs = ex_libnl.c
objects = ex_libnl.o
LIB_PATH = /usr/lib/
INC_PATH = /usr/include/
CFLAGS = -Wall -g
LDFLAGS = -lnl

ex_libnl : $(objects)
	$(CC) -o ex_libnl -L$(LIB_PATH) -I$(INC_PATH) $(LDFLAGS) $(objects) 

.c.o:
	$(CC) $(CFLAGS) -c $*.c

.PHONY : clean
clean :
	rm ex_libnl $(objects)

```
-L/usr/lib <-- don't really need it, gcc includes it ad default library search path
LDFLAGS = -lnl  <-- tell gcc where to search undefined functions. It's more important that using nl instead of libnl.

Then, it showed:
> $ make
gcc -Wall -g -c ex_libnl.c
gcc -o ex_libnl -L/usr/lib/ -I/usr/include/ -lnl ex_libnl.o


It works just fine. Thank you.

Cuthbert

---

### Post by danica on 2010-04-12
hello,
which version of libnl i should take,if i work in ubuntu9.10,and i have allready use latest versions of compat-wireless and wireless redgb. ??  when i install version 3 and 5, there are problems,like no development...thank you

---

