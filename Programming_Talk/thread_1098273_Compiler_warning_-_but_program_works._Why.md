---
title: "Compiler warning - but program works. Why?"
date: 2009-03-16
forum: Programming Talk
---

### Post by Krupski on 2009-03-16
Hi all,

Still on my quest to learn... I ran into another snag (should be easy for you guys).

First the code:

```

#include <stdio.h>
#include <time.h>

int main(void)
{
    struct timespec {
        time_t tv_sec;
        long tv_nsec;
    } ts;

    ts.tv_sec = 5; // experiment: 5 second delay

    ts.tv_nsec = 0;
    while(nanosleep(&ts, &ts)) {} // do nothing

    return 0;
}

```

Simple 5 second delay.

Compiling it with GCC and -Wextra, I get these warnings:

```

delay.c: In function ‘main’:
delay.c:14: warning: passing argument 1 of ‘nanosleep’ from incompatible pointer type
delay.c:14: warning: passing argument 2 of ‘nanosleep’ from incompatible pointer type

```

However, the program works:

```

root@ubuntu:~/c-progs# time ./delay

real	0m5.001s
user	0m0.000s
sys	0m0.000s

```

(yes I now I shouldn't log in as root all the time... but this is my experimental "expendable" machine - if I mess it up it's no loss).

So... anyone know why I get the warning message... and what to do about it?

Thanks!

-- Roger

---

### Post by WW on 2009-03-16
**struct timespec** is defined in time.h, so you shouldn't redefine it:
```

#include <stdio.h>
#include <time.h>

int main(void)
{
    struct timespec ts;

    ts.tv_sec = 5; // experiment: 5 second delay

    ts.tv_nsec = 0;
    while(nanosleep(&ts, &ts)) {} // do nothing

    return 0;
}

```

---

### Post by Krupski on 2009-03-16
> **WW said:**
> **struct timespec** is defined in time.h, so you shouldn't redefine it:
```

#include <stdio.h>
#include <time.h>

int main(void)
{
    struct timespec ts;

    ts.tv_sec = 5; // experiment: 5 second delay

    ts.tv_nsec = 0;
    while(nanosleep(&ts, &ts)) {} // do nothing

    return 0;
}

```

OH!!!!!! I get it. I didn't even know about "timespec"... I just copied the nanosleep stuff from another program and tried to make it work.

Upon looking at "time.h", I also see that tv_sec and tv_nsec are already defined, so *all* I need is the timespec struct!

I got confused initially by looking at the manpage for nanosleep. I thought I had to MAKE the structure... I didn't know it was already defined.

THANKS!!!

-- Roger

---

