---
title: "World Time/Zones API"
date: 2011-06-08
forum: Programming Talk
---

### Post by Kleenux on 2011-06-08
I'm looking at a way to get the current Time in a number of places.

Is there some API made available to the Linux community?

Basically, I would call that API 4 times a day.

---

### Post by gmargo on 2011-06-09
If you're looking for a simple command to get the time in various timezones, you can use the **date(1)** command with various values of the **TZ** environment variable.  For instance:
```

$ TZ=UTC date
Thu Jun  9 15:51:06 UTC 2011

$ TZ=America/New_York date
Thu Jun  9 11:51:07 EDT 2011

$ TZ=America/Los_Angeles date
Thu Jun  9 08:51:08 PDT 2011

```Or you could do the equivalent in C:
```

#include <stdio.h>
#include <time.h>
int main()
{
        char buf[80];
        time_t curtime;
        char * fmt = "%a %b %e %H:%M:%S %Z %Y";
        time(&curtime);

        putenv("TZ=UTC");
        strftime(buf, sizeof(buf), fmt, localtime(&curtime));
        puts(buf);

        putenv("TZ=America/New_York");
        strftime(buf, sizeof(buf), fmt, localtime(&curtime));
        puts(buf);

        putenv("TZ=America/Los_Angeles");
        strftime(buf, sizeof(buf), fmt, localtime(&curtime));
        puts(buf);
}

```Output:
```

$ ./date_test1 
Thu Jun  9 16:08:11 UTC 2011
Thu Jun  9 12:08:11 EDT 2011
Thu Jun  9 09:08:11 PDT 2011

```

---

