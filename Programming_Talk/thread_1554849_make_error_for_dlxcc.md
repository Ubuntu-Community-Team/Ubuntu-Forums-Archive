---
title: "make error for dlxcc"
date: 2010-08-17
forum: Programming Talk
---

### Post by myquidproquo on 2010-08-17
Hi!

I'm trying to use a C to DLX assembly compiler I found called dlxcc but I can't get it to work.

When I 'make' I get this: 
```
gcc -g -O  -I. -I. -I./config \
  -DSTANDARD_STARTFILE_PREFIX=\"/labs/acaps/lib/\" \
  -DSTANDARD_EXEC_PREFIX=\"/labs/acaps/packages/dlxcc/bin/dlxcc-\" -c \
  `echo ./gcc.c | sed 's,^\./,,'`
In file included from /usr/include/stdio.h:75,
                 from gcc.c:120:
/usr/include/libio.h:491: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/libio.h:493: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
In file included from gcc.c:120:
/usr/include/stdio.h:349: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:354: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:357: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:368: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:395: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:454: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:461: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:466: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:476: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:481: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:484: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
In file included from /usr/include/stdio.h:910,
                 from gcc.c:120:
/usr/include/bits/stdio2.h:28: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h:44: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h: In function ‘vsprintf’:
/usr/include/bits/stdio2.h:48: error: ‘__ap’ undeclared (first use in this function)
/usr/include/bits/stdio2.h:48: error: (Each undeclared identifier is reported only once
/usr/include/bits/stdio2.h:48: error: for each function it appears in.)
/usr/include/bits/stdio2.h: At top level:
/usr/include/bits/stdio2.h:58: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h:75: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h: In function ‘vsnprintf’:
/usr/include/bits/stdio2.h:79: error: ‘__ap’ undeclared (first use in this function)
/usr/include/bits/stdio2.h: At top level:
/usr/include/bits/stdio2.h:90: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h:92: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h:115: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h: In function ‘vprintf’:
/usr/include/bits/stdio2.h:118: error: ‘__ap’ undeclared (first use in this function)
/usr/include/bits/stdio2.h:118: error: too many arguments to function ‘__vfprintf_chk’
/usr/include/bits/stdio2.h: At top level:
/usr/include/bits/stdio2.h:126: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h: In function ‘vfprintf’:
/usr/include/bits/stdio2.h:128: error: ‘__ap’ undeclared (first use in this function)
/usr/include/bits/stdio2.h:128: error: too many arguments to function ‘__vfprintf_chk’
In file included from gcc.c:127:
gvarargs.h:49:1: warning: "va_start" redefined
In file included from /usr/include/libio.h:53,
                 from /usr/include/stdio.h:75,
                 from gcc.c:120:
./stdarg.h:13:1: warning: this is the location of the previous definition
gcc.c: In function ‘store_arg’:
gcc.c:389: warning: incompatible implicit declaration of built-in function ‘realloc’
gcc.c: In function ‘record_temp_file’:
gcc.c:444: warning: incompatible implicit declaration of built-in function ‘strlen’
gcc.c:444: warning: cast to pointer from integer of different size
gcc.c:445: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:453: warning: cast to pointer from integer of different size
gcc.c:466: warning: cast to pointer from integer of different size
gcc.c: In function ‘choose_temp_base’:
gcc.c:559: warning: incompatible implicit declaration of built-in function ‘strlen’
gcc.c:560: warning: cast to pointer from integer of different size
gcc.c:561: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c: In function ‘find_exec_file’:
gcc.c:581: warning: incompatible implicit declaration of built-in function ‘strlen’
gcc.c:591: warning: cast to pointer from integer of different size
gcc.c:599: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:600: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:606: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:607: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:616: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:617: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:623: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:624: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:633: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:634: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:640: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:641: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:650: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:651: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:657: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:658: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c: In function ‘pexecute’:
gcc.c:747: warning: incompatible implicit declaration of built-in function ‘exit’
gcc.c: In function ‘execute’:
gcc.c:791: warning: incompatible implicit declaration of built-in function ‘alloca’
gcc.c:879: warning: incompatible implicit declaration of built-in function ‘abort’
gcc.c: In function ‘process_command’:
gcc.c:984: warning: cast to pointer from integer of different size
gcc.c:985: warning: cast to pointer from integer of different size
gcc.c: In function ‘do_spec_1’:
gcc.c:1203: warning: incompatible implicit declaration of built-in function ‘bcopy’
gcc.c:1218: warning: incompatible implicit declaration of built-in function ‘alloca’
gcc.c:1219: warning: incompatible implicit declaration of built-in function ‘strncpy’
gcc.c:1226: warning: incompatible implicit declaration of built-in function ‘bcopy’
gcc.c:1232: warning: incompatible implicit declaration of built-in function ‘bcopy’
gcc.c:1294: warning: incompatible implicit declaration of built-in function ‘alloca’
gcc.c:1294: warning: incompatible implicit declaration of built-in function ‘strlen’
gcc.c:1333: warning: incompatible implicit declaration of built-in function ‘abort’
gcc.c: In function ‘handle_braces’:
gcc.c:1381: warning: incompatible implicit declaration of built-in function ‘abort’
gcc.c: In function ‘find_file’:
gcc.c:1491: warning: incompatible implicit declaration of built-in function ‘strlen’
gcc.c:1510: warning: incompatible implicit declaration of built-in function ‘alloca’
gcc.c:1516: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1517: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1523: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1524: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1533: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1534: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1540: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1541: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1550: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1551: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1557: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1558: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1567: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1568: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1574: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1575: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1584: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1585: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1591: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1592: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1601: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1602: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1608: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1609: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1618: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1619: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1625: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1626: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1635: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1636: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c:1642: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c:1643: warning: incompatible implicit declaration of built-in function ‘strcat’
gcc.c: In function ‘main’:
gcc.c:1688: warning: cast to pointer from integer of different size
gcc.c:1704: warning: incompatible implicit declaration of built-in function ‘exit’
gcc.c:1713: warning: cast to pointer from integer of different size
gcc.c:1714: warning: incompatible implicit declaration of built-in function ‘bzero’
gcc.c:1718: warning: cast to pointer from integer of different size
gcc.c:1729: warning: incompatible implicit declaration of built-in function ‘strlen’
gcc.c:1816: warning: incompatible implicit declaration of built-in function ‘exit’
gcc.c: In function ‘xmalloc’:
gcc.c:1822: warning: incompatible implicit declaration of built-in function ‘malloc’
gcc.c:1822: warning: initialization makes integer from pointer without a cast
gcc.c: In function ‘xrealloc’:
gcc.c:1831: warning: incompatible implicit declaration of built-in function ‘realloc’
gcc.c:1831: warning: passing argument 1 of ‘realloc’ makes pointer from integer without a cast
gcc.c:1831: note: expected ‘void *’ but argument is of type ‘int’
gcc.c:1831: warning: initialization makes integer from pointer without a cast
gcc.c: In function ‘concat’:
gcc.c:1843: warning: incompatible implicit declaration of built-in function ‘strlen’
gcc.c:1844: warning: cast to pointer from integer of different size
gcc.c:1846: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc.c: In function ‘save_string’:
gcc.c:1859: warning: cast to pointer from integer of different size
gcc.c:1861: warning: incompatible implicit declaration of built-in function ‘bcopy’
gcc.c: In function ‘pfatal_with_name’:
gcc.c:1870: error: conflicting types for ‘sys_errlist’
/usr/include/bits/sys_errlist.h:28: note: previous declaration of ‘sys_errlist’ was here
gcc.c: In function ‘fatal’:
gcc.c:1960: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [gcc.o] Error 1

```

Can anyone help me make this work?

---

### Post by gmargo on 2010-08-18
Please tell us exactly where you downloaded it.

---

### Post by myquidproquo on 2010-08-18
I've found dlxcc in many sites but most are from 98 - 2000 with many dead links.

Here is one of the sites:
[http://www.weblearn.hs-bremen.de/risse/RST/software/linux/dlxcc/dlxcc-2.0.tar.gz](http://www.weblearn.hs-bremen.de/risse/RST/software/linux/dlxcc/dlxcc-2.0.tar.gz)

I really need to compile code from c to dlx assembly but I don't know how. 
I've tried to install different (old) versions of debian (with old gcc and glibc) in a virtual machine but dlxcc still doesn't work...

Can anyone help me get this to work?

---

### Post by gmargo on 2010-08-19
I downloaded a slightly different version (later I think) including a simulator, from [ftp://ftp.cs.helsinki.fi/pub/People/Kerola_Teemu/dlx/](ftp://ftp.cs.helsinki.fi/pub/People/Kerola_Teemu/dlx/) 
 It is instructive to look at the diff in the compiler source.

(Seems to be quite difficult to get that old a version of gcc to compile though.)

---

