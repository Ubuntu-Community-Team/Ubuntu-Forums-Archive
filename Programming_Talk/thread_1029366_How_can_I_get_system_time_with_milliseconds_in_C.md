---
title: "How can I get system time with milliseconds in C"
date: 2009-01-03
forum: Programming Talk
---

### Post by sreeyeshns on 2009-01-03
I'm an Electronics and Communication engineering student but extremely interested in programming. 

I'm trying to develop a software tool to encrypt files using TDMRC algorithm. This algorithm requires the current system time to generate a random seed. I need some method(Standard library function or some other) to get the system time with the following fields. 

hour:minute:second:millisecond

No problem with the first three fields. But I'm not able to get the millisecond part.

Someone please help me. I'm writing the program in C.

---

### Post by dwhitney67 on 2009-01-03
Use gettimeofday().  Read the man-page for such.  You will note that it returns time down to the microsecond level; just perform a basic arithmetic operation to calculate milliseconds.


```

struct timeval tv;

gettimeofday(&tv, 0);

...

```

---

### Post by sreeyeshns on 2009-01-03
Thank you very much for spending time for me.
Which header file should I use? 
How can I get more information about this function from the bash shell?

Actually I'm a beginner to the world of linux.

---

### Post by dwhitney67 on 2009-01-03
Header file:
```
#include <sys/time.h>
```


From the shell:
```
man gettimeofday
```

If you do not have the man-pages installed:
```
sudo apt-get install manpages-dev
```

---

### Post by stroyan on 2009-01-03
Time of day isn't a very good source of randomness.  A program may be run by cron or another scheduling mechanism.  That would make the time values not very random at all.

  You can read from /dev/random on a linux system to get high quality random numbers.  See "man urandom" for details on the /dev/random and /dev/urandom pseudodevices.

---

### Post by jmartrican on 2009-01-03
I just happen to be working on a similar problem.   Check out this link.... [http://www.cs.utah.edu/dept/old/texinfo/glibc-manual-0.02/library_19.html](http://www.cs.utah.edu/dept/old/texinfo/glibc-manual-0.02/library_19.html)

It has what dwhitney said but with all the bells and whistles.

---

