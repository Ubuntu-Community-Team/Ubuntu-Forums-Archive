---
title: "[SOLVED] Program I wrote in C++"
date: 2008-09-04
forum: Programming Talk
---

### Post by Rany Albeg on 2008-09-04
Hi,

I wrote a program in C++.
Also made an alias to open that program.
When i activate this alias it opens the program.
When i exit the program is see this:

*** stack smashing detected ***: ./textSearch terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7dda138]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7dda0f0]
./textSearch[0x80498a7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d03450]
./textSearch(__gxx_personality_v0+0x59)[0x8048ed1]
======= Memory map: ========
08048000-0804a000 r-xp 00000000 08:01 3260448    /home/rany/C++/textSearch/textSearch
0804a000-0804b000 rw-p 00002000 08:01 3260448    /home/rany/C++/textSearch/textSearch
0804b000-0806c000 rw-p 0804b000 00:00 0          [heap]
b7cec000-b7ced000 rw-p b7cec000 00:00 0 
b7ced000-b7e36000 r-xp 00000000 08:01 13772130   /lib/tls/i686/cmov/libc-2.7.so
b7e36000-b7e37000 r--p 00149000 08:01 13772130   /lib/tls/i686/cmov/libc-2.7.so
b7e37000-b7e39000 rw-p 0014a000 08:01 13772130   /lib/tls/i686/cmov/libc-2.7.so
b7e39000-b7e3c000 rw-p b7e39000 00:00 0 
b7e3c000-b7e46000 r-xp 00000000 08:01 13754432   /lib/libgcc_s.so.1
b7e46000-b7e47000 rw-p 0000a000 08:01 13754432   /lib/libgcc_s.so.1
b7e47000-b7e48000 rw-p b7e47000 00:00 0 
b7e48000-b7e6b000 r-xp 00000000 08:01 13772138   /lib/tls/i686/cmov/libm-2.7.so
b7e6b000-b7e6d000 rw-p 00023000 08:01 13772138   /lib/tls/i686/cmov/libm-2.7.so
b7e6d000-b7f55000 r-xp 00000000 08:01 7473210    /usr/lib/libstdc++.so.6.0.9
b7f55000-b7f58000 r--p 000e8000 08:01 7473210    /usr/lib/libstdc++.so.6.0.9
b7f58000-b7f5a000 rw-p 000eb000 08:01 7473210    /usr/lib/libstdc++.so.6.0.9
b7f5a000-b7f60000 rw-p b7f5a000 00:00 0 
b7f6e000-b7f72000 rw-p b7f6e000 00:00 0 
b7f72000-b7f73000 r-xp b7f72000 00:00 0          [vdso]
b7f73000-b7f8d000 r-xp 00000000 08:01 13754387   /lib/ld-2.7.so
b7f8d000-b7f8f000 rw-p 00019000 08:01 13754387   /lib/ld-2.7.so
bf91c000-bf931000 rw-p bffeb000 00:00 0          [stack]
Aborted


For a beginner in linux like me it looks scary :)
Yes its related to the Memory stack i can see the title, but it looks like an error or something , you know "terminated","aborted" :D

I need some help with this.
Thanks.

---

### Post by Zugzwang on 2008-09-04
Run the program (from the console & the right directory) using valgrind:
```

valgrind --tool=memcheck ./textSearch

```

Of course, you need to install valgrind first (use synaptic). It will then give you hints on illegal memory access performed by your program. Have a look at the *first* error and try to fix it.

---

### Post by nvteighen on 2008-09-04
You're clearly writing more data into a variable than it can hold to. Use Zugzwang's advice and check all calls to string input functions, as those are the usual vectors for stack smashing errors.

---

### Post by Rany Albeg on 2008-09-04
Yea, I used a 25 characters array to contain path name of file and the input was longer.

Thanks for your useful and fast replies.

Have a nice day ;)

---

### Post by Zugzwang on 2008-09-04
> **Rany Albeg said:**
> Yea, I used a 25 characters array to contain path name of file and the input was longer.


Note that in this case you are not programming in C++-style. The C++ STL library has a string class for which this problem cannot occur. If you need some C-Style array (for example for opening files), you can always get it from such a string by calling the c_str() method.

The proper usage of the concepts of C++ can get you rid of all of the problems of *this* kind, you just have to know how. ;-)

---

