---
title: "Timer Resolution on Ubuntu"
date: 2009-01-19
forum: Programming Talk
---

### Post by pha3z on 2009-01-19
can anyone tell me what resolution the timer has in the ubuntu kernel?  I'm not referring to multi-tasking resolution (as in pre-emptive switching between applications).  I'm actually referring to the system timer which is used by games to do all their computation in real-time.

i seem to have trouble finding any information that is not about the multi-tasking management.  Are the two actually directly connected?

---

### Post by stroyan on 2009-01-19
The gettimeofday and clock_gettime functions have a resolution near to a microsecond.
You can test that with this program.  It is compiled with ```
gcc -o clock_resolution clock_resolution.c -lrt
```
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

