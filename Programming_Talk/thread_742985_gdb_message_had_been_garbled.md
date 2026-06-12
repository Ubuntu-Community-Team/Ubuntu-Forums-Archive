---
title: "gdb message had been garbled?"
date: 2008-04-02
forum: Programming Talk
---

### Post by HolyJoe on 2008-04-02
Hi, 
I using gdb to debug a small c program, when I execute *where* gdb command, I got the following 'Garbled' message:
(gdb) where
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e80875 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e82201 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7ec4a70 in ?? () from /lib/tls/i686/cmov/libc.so.6
#4  0x00000003 in ?? ()
#5  0xb7fca820 in ?? ()
#6  0xb7ec48db in ?? () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7f9bff4 in ?? () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7fc9ce0 in ?? () from /lib/ld-linux.so.2
#9  0x0804a030 in ?? ()
#10 0xbf888f18 in ?? ()
#11 0xb7ec37a5 in free () from /lib/tls/i686/cmov/libc.so.6
Backtrace stopped: frame did not save the PC

My question is what caused the **??()** ? and how can I fix that?

Thanks.

---

### Post by Zugzwang on 2008-04-02
Did you compile your program using the "-g" switch (for example "-g3")? Otherwise you don't have debug symbols in your executable file, so GDB can't display more information.

You are using gcc, right?

---

### Post by HolyJoe on 2008-04-02
Hi, Zugzwang,

Thank you for your reply.

I use 'gcc -Wall -g" to compile my c program, and I try '-g3' option, but the result is the same. It's terrible.

---

### Post by heikaman on 2008-04-02
> **HolyJoe said:**
> 
I use 'gcc -Wall -g" to compile my c program, and I try '-g3' option, but the result is the same. It's terrible.
try using "-ggdb"

---

### Post by Zugzwang on 2008-04-02
Dear OP,

I have to apologize for not reading your post correctly. As you can see, the last line refers to a function of glibc, so even though you have debug symbols enabled, this doesn't change anything since these lines do not refer to your code.

According to ([http://sourceware.org/ml/gdb/2007-02/msg00275.html](http://sourceware.org/ml/gdb/2007-02/msg00275.html)) you have to:
```

Make sure that your Linux distributor's debug info packages for glibc
are installed, and that your GDB is configured to use them.

```
You would do that by running the following command on Ubuntu:
```
sudo apt-get install libc6-dbg
```

Also the "Backtrace stopped: frame did not save the PC" message might occur if you compile your program using optimization, so additionally try the "-O0" option.

Let's see if that helps...

---

### Post by HolyJoe on 2008-04-03
> **heikaman said:**
> try using "-ggdb"

Thank you for your reply.
 
Use '-ggdb' option can not resolved my problem too.

---

### Post by HolyJoe on 2008-04-03
> **Zugzwang said:**
> Dear OP,

I have to apologize for not reading your post correctly. As you can see, the last line refers to a function of glibc, so even though you have debug symbols enabled, this doesn't change anything since these lines do not refer to your code.

According to ([http://sourceware.org/ml/gdb/2007-02/msg00275.html](http://sourceware.org/ml/gdb/2007-02/msg00275.html)) you have to:
```

Make sure that your Linux distributor's debug info packages for glibc
are installed, and that your GDB is configured to use them.

```
You would do that by running the following command on Ubuntu:
```
sudo apt-get install libc6-dbg
```

Also the "Backtrace stopped: frame did not save the PC" message might occur if you compile your program using optimization, so additionally try the "-O0" option.

Let's see if that helps...

Thank your help again.
I try install libc-dbg, but I got the following message:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libc6-dbg instead of libc-dbg
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dbg: Depends: libc6 (= 2.6.1-1ubuntu9) but 2.6.1-1ubuntu10 is to be installed
E: Broken packages

How to install libc-dbg package on Ubuntu 7.10?

---

