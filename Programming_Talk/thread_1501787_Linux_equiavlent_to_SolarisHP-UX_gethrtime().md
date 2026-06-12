---
title: "Linux equiavlent to Solaris/HP-UX gethrtime() ?"
date: 2010-06-04
forum: Programming Talk
---

### Post by jbm222 on 2010-06-04
Is there a single function call in linux  that will return a high resolution timestamp, similar to gethrtime() found on HP-UX & Solaris systems?

I want to use it to accurately measure how long it takes to execute other pieces of code.  For example:

```

hrtime_t start, end;
start = gethrtime();
DoSomeStuff();
end = gethrtime();
printf("Delta time = %lld\n", end-start);


```

---

### Post by jobix on 2010-06-04
> man clock_gettime

The clock_gettime populates a structure where you can get seconds and nanoseconds. Call that before and after and subtract to get your elapsed time.

---

### Post by jbm222 on 2010-06-05
I was already aware of clock_gettime, hoping to find something a little lighter weight & easier to use.

If I do go with clock_gettime, it seems like CLOCK_MONOTONIC_RAW is what I would want to use, but it doesn't appear to be supported on my system. gcc gives me an undeclared symbol error.   From the manpage, I can't tell why.

CLOCK_MONOTONIC_RAW (since Linux 2.6.28; Linux-specific)
    Similar to CLOCK_MONOTONIC, but provides access to a  raw  hard&#8208;
    ware-based time that is not subject to NTP adjustments.

"uname -r" shows I am running 2.6.32-22

---

### Post by jobix on 2010-06-06
I'm guessing you included "time.h" and compiled with the -lrt option. If your program is not going to be running for a long time, I'm not sure you need to worry about the NTP adjustment part. NTP adjustment is a long, slow process, e.g., to adjust time by 1 second, it typically takes about half an hour. In other words, you can just use CLOCK_MONOTONIC instead of CLOCK_MONOTONIC_RAW. If your program is going to be running for a long time, then I'm not sure you need to be worried about the accuracy down to the nanosecond granularity.

---

### Post by dwhitney67 on 2010-06-06
If you do indeed require nanosecond time resolution, then use CLOCK_REALTIME as the clock ID for clock_gettime().  Otherwise an alternative is to use gettimeofday() which reports time with microsecond resolution.

P.S.  You can use clock_getres() to determine if your system even supports nanosecond time resolution.

---

