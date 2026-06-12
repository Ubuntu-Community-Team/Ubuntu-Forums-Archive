---
title: "how to include mutex.h"
date: 2010-10-10
forum: Programming Talk
---

### Post by vksingh on 2010-10-10
Hi,

I am not able to include mutex.h in ubuntu 10.4. It says "no such file exists".

Can some body tell me how to include.


[I]ques1.c:4:23: error: sys/mutex.h: No such file or directory
ques1.c: In function ‘main’:
ques1.c:10: error: ‘mutex_t’ undeclared (first use in this function)
ques1.c:10: error: (Each undeclared identifier is reported only once
ques1.c:10: error: for each function it appears in.)
ques1.c:10: error: expected ‘;’ before ‘mutex’
[/I]




Thanks,

Vivek

---

### Post by MadCow108 on 2010-10-10
sys/mutex.h is a freeBSD file.
you'll probably have to port your program to linux.

---

