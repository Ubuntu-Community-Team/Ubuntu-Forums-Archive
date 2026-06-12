---
title: "BerkeleyDB Link Problem"
date: 2013-06-12
forum: Programming Talk
---

### Post by pzYsTorM on 2013-06-12
Hi,  I have a problem with BerlekeyDB (5.1, installed via Ubuntu 12.04 apt-get) and the appropriate dev libs: Some programs like APR-Util/Subversion seem to have problems when using this lib... 
 I have analysed the problem and tried to compile my own program:
```

#include stdlib.h (of course in angle brackets, but this does not seem to work)
#include db.h (of course in angle brackets, but this does not seem to work)
int main ()  {
  int major, minor, patch;
  db_version (&major, &minor, &patch);
  if (major != DB_VERSION_MAJOR)
    exit (1);
   else
     exit (0);
}

```
The compile command is as simple
```
gcc -o test -ldb-5.1 test.c
```
 (does not matter if I omit the -ldb-5.1)

  The error is:
```

/tmp/ccWs9TOd.o: In function `main':
test.c:(.text+0x1b): undefined reference to `db_version'
collect2: ld gab 1 als Ende-Status zurück (engl. ld returned with 1)

```

But the files are there:
```

# ls -al /usr/include/db.h
-rw-r--r-- 1 root root 112882 Dez  3  2011 /usr/include/db.h 
 # ls -al /usr/lib/x86_64-linux-gnu/libdb*
-rw-r--r-- 1 root root 2548514 Dez  3  2011 /usr/lib/x86_64-linux-gnu/libdb-5.1.a
-rw-r--r-- 1 root root 1518928 Dez  3  2011 /usr/lib/x86_64-linux-gnu/libdb-5.1.so
lrwxrwxrwx 1 root root      11 Dez  3  2011 /usr/lib/x86_64-linux-gnu/libdb.a -> libdb-5.1.a
lrwxrwxrwx 1 root root      12 Dez  3  2011 /usr/lib/x86_64-linux-gnu/libdb.so -> libdb-5.1.so

```
```

# dpkg --get-selections | grep libdb5
libdb5.1                                        install
libdb5.1-dev                                    install

```

I can use printf to print the constant DB_VERSION_MAJOR... That works!.. '5' is printed.
So the header file is found. But why does the program not find the library?  Thanks for your help in advance.

---

### Post by steeldriver on 2013-06-12
Have you tried changing the link order?

```
gcc -o test test.c -ldb-5.1
```

From [FONT=courier new]man gcc [/FONT]:
```

       -llibrary
       -l library
           Search the library named library when linking.  (The second alternative with the library as a separate
           argument is only for POSIX compliance and is not recommended.)

[B]           It makes a difference where in the command you write this option; the linker searches and processes libraries
           and object files in the order they are specified.  Thus, foo.o -lz bar.o searches library z after file foo.o
           but before bar.o.  If bar.o refers to functions in z, those functions may not be loaded.
[/B]

```

---

### Post by pzYsTorM on 2013-06-12
Uhhh... that is new to me.
Thanks! It worked instantly.
Now I will try to get APR-util and subversion to work with libdb5.1

---

