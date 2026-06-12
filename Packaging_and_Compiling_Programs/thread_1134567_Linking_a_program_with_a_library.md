---
title: "Linking a program with a library"
date: 2009-04-23
forum: Packaging and Compiling Programs
---

### Post by Gannon8 on 2009-04-23
Hello all. I am trying to run gcc to compile my first single file sqlite3 program that tests if a build of sqlite3 is threadsafe. Unfortunately, here is what I get when I try to:
```
gcc -Wall -I/usr/local/include -L/usr/local/lib/libsqlite3.a -o sqlitethread.o sqlitethread.c
/tmp/ccuqj4zv.o: In function `main':
sqlitethread.c:(.text+0x12): undefined reference to `sqlite3_threadsafe'
collect2: ld returned 1 exit status

```

Am I doing something wrong?

---

### Post by Gannon8 on 2009-04-24
Aaanyone?

---

### Post by Namtabmai on 2009-04-24
Try

```

gcc -Wall -I/usr/local/include -L/usr/local/lib -lsqlite3.a -o sqlitethread.o sqlitethread.c

```

-L specifies a directory to search for libraries
-l specifies a library

---

