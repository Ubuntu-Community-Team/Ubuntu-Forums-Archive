---
title: "C standard library clock() malfunction."
date: 2011-01-20
forum: Programming Talk
---

### Post by worksofcraft on 2011-01-20
I could have sworn I used clock() before and it worked just fine... but now look what I get:

[php]
// g++ clock.cpp
#include <cstdio>
#include <ctime>

int main(int argc, char *argv[], char *envp[]) {
	// record start time
	clock_t iStartClock = clock();
	printf("please press enter to end:\n");
	// wait for key press
	char i;
	scanf("%c", &i);
	// record new time
	clock_t iEndClock = clock();
	// report both start and end time values
	return !printf("iStartClock = %ld, iEndClock = %ld\n", iStartClock, iEndClock);
}
[/php]

gives me the following:
```

$ g++ clock.cpp
$ ./a.out
please press enter to end:

iStartClock = 0, iEndClock = 10000

```

and it always seems to be 10000 no matter how long I wait :confused:

Does it do that on your computer too?

---

### Post by trent.josephsen on 2011-01-20
From clock(3):
> 
       The clock() function returns an approximation of processor time used by
       the program.

Blocking for input doesn't require processor time.

---

### Post by worksofcraft on 2011-01-20
> **trent.josephsen said:**
> From clock(3):


Blocking for input doesn't require processor time.

D'oh... thanks yes... I need one that gives me elapsed time not processor time.
edit ok here it is if anyone else needs this:
[php]

// g++ clock.cpp
#include <cstdio>
#include <ctime>
#include <sys/time.h>

// note: clock() gives processor time not the elapsed time
// for that we need gettimeofday(timeval *tv, NULL) tv struct has seconds (since Jan 1970) and microseconds

struct elapsed_time {
	enum { U_SEC = 1000000 };
	void start() {
		timeval iT;
		gettimeofday(&iT, NULL); // IDK what the NULL parameter is for
		iStart = iT.tv_sec * U_SEC + iT.tv_usec;
	}
	void stop() {
		timeval iT;
		gettimeofday(&iT, NULL);
		iStart = (unsigned long) iT.tv_sec * U_SEC + iT.tv_usec - iStart;
	}
	operator unsigned long() { return iStart; }
	operator double() { return double(iStart)/double(U_SEC); }
private:
	unsigned long iStart;
};

int main(int argc, char *argv[], char *envp[]) {
	elapsed_time sTime;
	sTime.start();

	printf("please press enter to end:\n");
	// wait for key press
	char i;
	scanf("%c", &i);

	sTime.stop();
	return !printf("elapsed time = %f Sec = %lu uSec\n", double(sTime), (unsigned long) sTime);
}
[/php]

---

