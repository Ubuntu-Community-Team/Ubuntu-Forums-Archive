---
title: "Programing with libodbc.a"
date: 2006-08-21
forum: Programming Talk
---

### Post by hcobbs on 2006-08-21
I've been having some difficulty of late.  I've decided that we will be using Ubuntu as the host OS for our future Linux Development at my work.  I've gotten pretty much everything going except for a particular program.

This program compiles everything properly, except when it comes to linking with the libodbc.a library. (BTW, I'm doing this statically)  When it does attempt to link, this is the output I get.

```
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libodbc.a(SQLConnect.o): In function `odbc_dlopen': undefined reference to `lt_dlopen'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libodbc.a(SQLConnect.o): In function `odbc_dlclose': undefined reference to `lt_dlclose'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libodbc.a(SQLConnect.o): In function `odbc_dlclose': undefined reference to `lt_dlclose'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libodbc.a(SQLConnect.o): In function `odbc_dlclose': undefined reference to `lt_dlclose'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libodbc.a(SQLConnect.o): In function `__connect_part_two': undefined reference to `lt_dlsym'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libodbc.a(SQLConnect.o): In function `__connect_part_two': undefined reference to `lt_dlerror'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libodbc.a(SQLConnect.o): In function `__connect_part_one': undefined reference to `lt_dlinit'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libodbc.a(SQLConnect.o): In function `__connect_part_one': undefined reference to `lt_dlsym'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libodbc.a(SQLConnect.o): In function `__connect_part_one': undefined reference to `lt_dlsym'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libodbc.a(SQLConnect.o): In function `__connect_part_one': undefined reference to `lt_dlsym'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libodbc.a(SQLConnect.o): In function `__connect_part_one': undefined reference to `lt_dlsym'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libodbc.a(SQLConnect.o): In function `__connect_part_one': undefined reference to `lt_dlsym'
/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib/libodbc.a(SQLConnect.o): In function `__connect_part_one': undefined reference to `lt_dlerror'
collect2: ld returned 1 exit status

```

As you can see, I'm using the gcc-3.4.6 and the version of myodbc installed(from ubuntu) is 2.2.11-11build1.  Am I just missing something, or does there seem to be a bug in the library?

---

