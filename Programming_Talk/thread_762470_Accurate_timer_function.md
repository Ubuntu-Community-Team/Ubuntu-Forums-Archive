---
title: "Accurate timer function"
date: 2008-04-22
forum: Programming Talk
---

### Post by mashamoo on 2008-04-22
Hi,

I need a a way of recording the elapsed time in milliseconds for a c++ program. I understand that the standard c/c++ libraries are not capable of this, thus I need an operating system call.

Can someone help me with this?

---

### Post by sq377 on 2008-04-22
```
NAME
       gettimeofday - get the date and time

SYNOPSIS
       #include <sys/time.h>

       int gettimeofday(struct timeval *restrict tp, void *restrict tzp);

DESCRIPTION
       The gettimeofday() function shall obtain the current time, expressed as
       seconds and microseconds since the Epoch, and store it in  the  timeval
       structure  pointed  to  by  tp.  The  resolution of the system clock is
       unspecified.

       If tzp is not a null pointer, the behavior is unspecified.

RETURN VALUE
       The gettimeofday() function shall  return  0  and  no  value  shall  be
       reserved to indicate an error.

```

You could get the time when you start, and get it when you stop and compare the times.  The other option would be to use the GTimer interface in Glib.
[http://library.gnome.org/devel/glib/stable/glib-Timers.html](http://library.gnome.org/devel/glib/stable/glib-Timers.html)

---

### Post by stroyan on 2008-04-22
The gettimeofday function is quite accurate on linux.
But the resolution is not actually specified.
If you link your program with "-lrt" you can use the
clock_gettime and clock_getres functions that actually report their (best) resolution.
```

#include <stdio.h>
#include <time.h>
#include <sys/time.h>

int main(int argc, char *argv[])
{
	struct timeval t1, t2;
	struct timezone timez;
	struct timespec tp1, tp2, res;
	double elapsed_time, resolution;

	gettimeofday(&t1, &timez);
	do {
	    gettimeofday(&t2, &timez);
	    elapsed_time = t2.tv_sec - t1.tv_sec
		+ (t2.tv_usec - t1.tv_usec) / 1e6;
	} while (elapsed_time == 0.0);
	printf("gettimeofday changed with elapsed time of %lg\n", elapsed_time);

	clock_gettime(CLOCK_REALTIME, &tp1);
	do {
	    clock_gettime(CLOCK_REALTIME, &tp2);
	    elapsed_time = tp2.tv_sec - tp1.tv_sec
		+ (tp2.tv_nsec - tp1.tv_nsec) / 1e9;
	} while (elapsed_time == 0.0);
	printf("clock_gettime changed with elapsed time of %lg\n", elapsed_time);

	clock_getres(CLOCK_REALTIME, &res);
	resolution = tp2.tv_sec - tp1.tv_sec
	    + (tp2.tv_nsec - tp1.tv_nsec) / 1e9;
	printf("clock_getres reports resolution of %lg\n", resolution);

	return 0;
}

```

---

### Post by ruy_lopez on 2008-04-22
oops!

---

