---
title: "struct ntptimeval strangeness on Lucid, anyone else have this?"
date: 2010-07-04
forum: Programming Talk
---

### Post by mdurham on 2010-07-04
Hi,
There seems to be a problem with "struct ntptimeval" on Lucid & Maverick.
It appears that the 'time' structure in ntptimeval is using nanoseconds and not microseconds as it's supposed to.
As you can see, the code below prints the tv_sec and tv_usec values but the tv_usec is 9 digits long indicating that it's nanoseconds. If I try on Jaunty it prints the correct length of 6 digits for microseconds.
If you are running Lucid or Maverick could you try the following please and let me know the result.
You might find (small chance) that the number of digits will be less than 9 as it depends on the value when it's read, if it is, run it 2 or three times and you should get the right value.

When I run the following code, I get:
Timeval secs:usecs == 1278214921:191819434
Clearly the usecs is incorrect as it should only be a maximum of 6 digits if it's microseconds.
Cheers, Mike

[PHP]#include <stdio.h>
#include <time.h>
#include <sys/timex.h>

int main()
{
	struct ntptimeval Timeval;

	ntp_gettime(&Timeval);
	printf("Timeval secs:usecs == %d:%d\n", Timeval.time.tv_sec, Timeval.time.tv_usec);
	return(0);
}
[/PHP]

---

### Post by Dara Javaherian on 2010-07-04
> **mdurham said:**
> Hi,
There seems to be a problem with "struct ntptimeval" on Lucid & Maverick.
It appears that the 'time' structure in ntptimeval is using nanoseconds and not microseconds as it's supposed to.
As you can see, the code below prints the tv_sec and tv_usec values but the tv_usec is 9 digits long indicating that it's nanoseconds. If I try on Jaunty it prints the correct length of 6 digits for microseconds.
If you are running Lucid or Maverick could you try the following please and let me know the result.
You might find (small chance) that the number of digits will be less than 9 as it depends on the value when it's read, if it is, run it 2 or three times and you should get the right value.

When I run the following code, I get:
Timeval secs:usecs == 1278214921:191819434
Clearly the usecs is incorrect as it should only be a maximum of 6 digits if it's microseconds.
Cheers, Mike

[PHP]#include <stdio.h>
#include <time.h>
#include <sys/timex.h>

int main()
{
    struct ntptimeval Timeval;

    ntp_gettime(&Timeval);
    printf("Timeval secs:usecs == %d:%d\n", Timeval.time.tv_sec, Timeval.time.tv_usec);
    return(0);
}
[/PHP]

Hi, I'm running a nice fresh install of Lucid. 
```

Timeval secs:usecs == 1278223831:234043

```
Is what I got with 2 warnings: 

```
a.cc:10: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘__time_t’
a.cc:10: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘__suseconds_t’

```

---

### Post by mdurham on 2010-07-04
> **Dara Javaherian said:**
> Hi, I'm running a nice fresh install of Lucid. 
```

Timeval secs:usecs == 1278223831:234043

```
Is what I got with 2 warnings: 

```
a.cc:10: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘__time_t’
a.cc:10: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘__suseconds_t’

```

Thanks for the reply Dara. Yours is correctly using microseconds, it seems there must be something wrong with my install. I used Qt Creator for compiling and running, I wonder if that would make any difference? I don't see why it should.
Cheers, Mike

---

