---
title: "Sqlite3 not working?"
date: 2009-04-21
forum: Packaging and Compiling Programs
---

### Post by Gannon8 on 2009-04-21
Hello all. Again.

I compiled the sqlite-amalgamation-3.6.13 tarball from [this]("http://www.sqlite.org/download.html") page. It says it completes and inserts the libraries and headers in /usr/local/whatever. I copied the example C code from [here]("http://www.sqlite.org/quickstart.html") into a .c file and tried to compile. Here is what I get:
```
gcc -Wall -c -I/usr/local/include sqlitetest.c
sqlitetest.c: In function 'main':
sqlitetest.c:14: error: 'sqlite3' undeclared (first use in this function)
sqlitetest.c:14: error: (Each undeclared identifier is reported only once
sqlitetest.c:14: error: for each function it appears in.)
sqlitetest.c:14: error: 'db' undeclared (first use in this function)
sqlitetest.c:20: warning: implicit declaration of function 'exit'
sqlitetest.c:20: warning: incompatible implicit declaration of built-in function 'exit'
sqlitetest.c:22: warning: implicit declaration of function 'sqlite3_open'
sqlitetest.c:24: warning: implicit declaration of function 'sqlite3_errmsg'
sqlitetest.c:24: warning: format '%s' expects type 'char *', but argument 3 has type 'int'
sqlitetest.c:25: warning: implicit declaration of function 'sqlite3_close'
sqlitetest.c:26: warning: incompatible implicit declaration of built-in function 'exit'
sqlitetest.c:28: warning: implicit declaration of function 'sqlite3_exec'
sqlitetest.c:31: warning: implicit declaration of function 'sqlite3_free'
```

What is exactly going wrong?

---

### Post by Gannon8 on 2009-04-22
Jeese, is everyone stuck in the main support categories?

---

### Post by LinuxGuy1234 on 2009-04-23
Source code?

---

### Post by LinuxGuy1234 on 2009-04-29
Try installing **libsqlite3-dev**.

---

