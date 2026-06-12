---
title: "Timer POSIX compilation error?"
date: 2008-07-12
forum: Packaging and Compiling Programs
---

### Post by raedbenz on 2008-07-12
Hi,
i am trying to compile a code that uses:
timer_create(), timer_connect(), timer_settime() by typing:

```
gcc -o test test.c
```
i get these errors:
```
test.c:(.text+0x5d): undefined reference to `timer_create'
test.c:(.text+0x78): undefined reference to `timer_connect'
test.c:(.text+0x9a): undefined reference to `timer_settime'
collect2: ld returned 1 exit status

```
any hints?
Note: i have added the <time.h> and <signal.h>

---

### Post by WW on 2008-07-12
You have to link with the **rt** (realtime) library.  Try this:
```

gcc -o test test.c -lrt

```

---

### Post by raedbenz on 2008-07-12
> **WW said:**
> You have to link with the **rt** (realtime) library.  Try this:
```

gcc -o test test.c -lrt

```
HI, 
now i get only this:
```
test.c:(.text+0x78): undefined reference to `timer_connect'
collect2: ld returned 1 exit status

```
the other two functions are defined...
????

---

### Post by WW on 2008-07-12
Based on a quick google, I think **timer_connect** is a non-Posix extension that is available in the VxWorks operating system as part of its [timerLib](http://www.slac.stanford.edu/exp/glast/flight/docs/VxWorks/docs/vxworks/ref/timerLib.html) library.  I don't know if the function is available in Linux/Ubuntu. (But maybe you already know that, since one of the pages that I found is [this thread](http://www.linuxquestions.org/questions/linux-software-2/posix-resources-recommendations-655087/) :) . )

---

### Post by raedbenz on 2008-07-12
lol,
so what are ways to deal with a handler in Linux?

---

