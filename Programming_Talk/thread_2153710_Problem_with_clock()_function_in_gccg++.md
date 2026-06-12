---
title: "Problem with clock() function in gcc/g++"
date: 2013-06-12
forum: Programming Talk
---

### Post by zobayer1 on 2013-06-12
I just wrote this code:
```
#include <stdio.h>
#include <time.h>
#include <unistd.h>
#include <stdlib.h>
int main() {
        clock_t clk1 = clock();
        printf("%ld\n", clk1);
        int i,r=0;
        for(i = 0; i < 100000; i++) r^=rand();
        printf("%d\n", r);
        clock_t clk2 = clock();
        printf("%ld\n", clk2);
        return 0;
}
```

I also tried using a sleep() before the loop, in both cases, clk1 and clk2 both showing 0, why is that? Am I suppossed aren't they supposed to be showing approximate clock cycle count for the program? What am I doing wrong here?

---

### Post by ofnuts on 2013-06-12
clock() is the processor time actually used, not the "wallclock time", so the delay added by a sleep() is not taken in account (no CPU used while sleeping).

Your problem is that your test runs too fast for the clock resolution (the output is in microseconds, but the standard doesn't say that you should have microsecond resolution). On my Core I5 laptop, I start to get different clock() values for 500K loops and the clock seems to have a 10ms resolution.

---

### Post by zobayer1 on 2013-06-12
> **ofnuts said:**
> clock() is the processor time actually used, not the "wallclock time", so the delay added by a sleep() is not taken in account (no CPU used while sleeping).

Your problem is that your test runs too fast for the clock resolution (the output is in microseconds, but the standard doesn't say that you should have microsecond resolution). On my Core I5 laptop, I start to get different clock() values for 500K loops and the clock seems to have a 10ms resolution.

Yah, I had no intention for getting wallclock time, for every query I wanted an incremental value, and thought the clock count could serve the purpose, but I guess you are right, after running around 10^7 - 10^8 loops, I got difference, so the pc is too fast for the algorithm. Can you suggest anything that can help here?

---

### Post by ofnuts on 2013-06-12
Try clock_gettime().

---

### Post by dwhitney67 on 2013-06-12
Or try using gettimeofday().

```

#include <sys/time.h>
...

struct timeval tv;

if (gettimeofday(&tv, NULL) == 0)
{
    // perform computation(s) using tv.tv_sec and tv.tv_usec
}
else
{
    // error
}

```

---

### Post by zobayer1 on 2013-06-12
> **dwhitney67 said:**
> Or try using gettimeofday().

```

#include <sys/time.h>
...

struct timeval tv;

if (gettimeofday(&tv, NULL) == 0)
{
    // perform computation(s) using tv.tv_sec and tv.tv_usec
}
else
{
    // error
}

```

Thanks a lot, tv_usec worked fine for the scenario.

---

