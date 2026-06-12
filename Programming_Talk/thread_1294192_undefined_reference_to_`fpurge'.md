---
title: "undefined reference to `fpurge'"
date: 2009-10-18
forum: Programming Talk
---

### Post by Dananjaya86 on 2009-10-18
/tmp/ccGV15x0.o: In function `main':
blowup4.c:(.text+0x2e): undefined reference to `fpurge'
collect2: ld returned 1 exit status

this problem occurs when fpurge(stdin) is used to delete the previously stored value taken from standard input. (keyboard)

when fflush(stdin) is used i have to type CTRL+D to enter value.pressing ENTER will cause the variable to store and display ENTER (Means a space.)

gcc version:
gcc.real (Ubuntu 4.3.3-5ubuntu4) 4.3.3
OS:
Ubuntu 9.04
Linux Kernel Version:
2.6.28-14-generic

---

### Post by Arndt on 2009-10-18
> **Dananjaya86 said:**
> /tmp/ccGV15x0.o: In function `main':
blowup4.c:(.text+0x2e): undefined reference to `fpurge'
collect2: ld returned 1 exit status

this problem occurs when fpurge(stdin) is used to delete the previously stored value taken from standard input. (keyboard)

when fflush(stdin) is used i have to type CTRL+D to enter value.pressing ENTER will cause the variable to store and display ENTER (Means a space.)

gcc version:
gcc.real (Ubuntu 4.3.3-5ubuntu4) 4.3.3
OS:
Ubuntu 9.04
Linux Kernel Version:
2.6.28-14-generic

This part of the manual page seems relevant:


```
CONFORMING TO
       These  functions  are  non-standard  and  not  portable.   The function
       fpurge() was introduced in 4.4BSD and is  not  available  under  Linux.
       The  function  __fpurge()  was introduced in Solaris, and is present in
       glibc 2.1.95 and later.
```

---

### Post by MadCow108 on 2009-10-18
also don't fflush stdin!
fflush is only defined on **output** streams not on input streams

use fscanf or flush the stream by hand

---

### Post by nvteighen on 2009-10-18
There it also smells to a coding error when accepting input. Can you please post the code?

---

