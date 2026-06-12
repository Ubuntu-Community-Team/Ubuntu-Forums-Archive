---
title: "glibc installation problems"
date: 2007-08-07
forum: Programming Talk
---

### Post by hansteam on 2007-08-07
When I run the configure file for glibc I get an error at the end:

```
configure: error: C preprocessor "/lib/cpp" fails sanity check

```


The config.log file shows this errror:

```
configure:3386: result: /lib/cpp
configure:3410: /lib/cpp  conftest.c
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from conftest.c:11:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
configure:3416: $? = 1
configure: failed program was:
```


and this one:

```
configure:3410: /lib/cpp  conftest.c
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from conftest.c:11:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
configure:3416: $? = 1
configure: failed program was:
```configure:3410: /lib/cpp  conftest.c
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from conftest.c:11:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
configure:3416: $? = 1
configure: failed program was:[/code]

Any ideas?

---

### Post by nitro_n2o on 2007-08-07
don't install it manually type 
```
sudo apt-get install build-essential 
```
this will save all the hassle :)

---

### Post by hansteam on 2007-08-07
You know what, I'm going to take your advice ;) I planned on manually installing just for the sake of figuring out how it was done but it's too much of a pain... thanks.

---

