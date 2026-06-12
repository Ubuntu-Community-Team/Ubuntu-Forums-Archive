---
title: "Cant get sample code for sqlite 3 to compile"
date: 2012-03-05
forum: Packaging and Compiling Programs
---

### Post by kevstar31 on 2012-03-05
ubuntu version 11.10
packages installed: build-essential libsqlite3-dev

I can not compile to code given at the botom of this page:[http://www.sqlite.org/quickstart.html](http://www.sqlite.org/quickstart.html)

complie command: gcc -lsqlite3 test.c

compile error:> /tmp/cc1ZCXlJ.o: In function `main':
test.cpp:(.text+0xc6): undefined reference to `sqlite3_open'
test.cpp:(.text+0xdd): undefined reference to `sqlite3_errmsg'
test.cpp:(.text+0x104): undefined reference to `sqlite3_close'
test.cpp:(.text+0x13b): undefined reference to `sqlite3_exec'
test.cpp:(.text+0x16f): undefined reference to `sqlite3_free'
test.cpp:(.text+0x17b): undefined reference to `sqlite3_close'
collect2: ld returned 1 exit status

shell returned 1       


---

### Post by MadCow108 on 2012-03-05
it must be
```
 gcc test.c -lsqlite3
```

libraries always after objects needing them

---

### Post by kevstar31 on 2012-03-05
works thank you!

---

