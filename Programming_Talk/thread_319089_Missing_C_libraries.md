---
title: "Missing C libraries"
date: 2006-12-15
forum: Programming Talk
---

### Post by Amablue on 2006-12-15
I recently did a complete switch from Kubuntu to Ubuntu and now I get an error when I try run gcc compiler. Here is the output:

```
tim@optimus:~$ cd src/gtest
tim@optimus:~/src/gtest$ make
gcc  -c -Wall gtest.c
gtest.c:11:20: error: string.h: No such file or directory
gtest.c:12:20: error: stdlib.h: No such file or directory
gtest.c:13:19: error: stdio.h: No such file or directory
gtest.c: In function ‘myDumpFunc’:
gtest.c:61: warning: implicit declaration of function ‘printf’
gtest.c:61: warning: incompatible implicit declaration of built-in function ‘printf’
gtest.c: In function ‘configure’:
gtest.c:79: error: storage size of ‘object_’ isn’t known
gtest.c:92: error: ‘new’ undeclared (first use in this function)
gtest.c:92: error: (Each undeclared identifier is reported only once
gtest.c:92: error: for each function it appears in.)
gtest.c:92: error: expected ‘,’ or ‘;’ before ‘object’
gtest.c:95: error: ‘struct DllAdmin’ has no member named ‘push’
gtest.c:110: warning: incompatible implicit declaration of built-in function ‘printf’
gtest.c:111: error: ‘uint’ undeclared (first use in this function)
gtest.c:111: error: expected ‘)’ before ‘dll’
gtest.c:111: warning: too few arguments for format
gtest.c:79: warning: unused variable ‘object_’
gtest.c: In function ‘gtest’:
gtest.c:198: warning: implicit declaration of function ‘strcpy’
gtest.c:198: warning: incompatible implicit declaration of built-in function ‘strcpy’
gtest.c: In function ‘dispatch’:
gtest.c:257: warning: incompatible implicit declaration of built-in function ‘printf’
make: *** [gtest.o] Error 1
tim@optimus:~/src/gtest$
```

I've tried reinstalling the gcc package, but that didn't make any difference.

---

### Post by jan247 on 2006-12-15
To install gcc and its libraries
```
sudo apt-get install build-essential
```

better install manpages for it as well:
```
sudo apt-get install manpages-dev
```

---

### Post by fiskem on 2006-12-17
thanx m8, really helped me !

---

