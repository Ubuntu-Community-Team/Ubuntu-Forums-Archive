---
title: "mktime: why is this inconsistent?"
date: 2012-03-08
forum: Programming Talk
---

### Post by MrWheeliebin on 2012-03-08
Consider the following code, why do the first two printfs differ from the last two? (NB: Requires that you are in the London time zone). Note the times are around the end of DST this year.

Is something global being changed in the system just by calling mktime?

MrWheeliebin

PS: I get the following output

1351386900 isdst flag now 0 (301)
1351390500 isdst flag now 0 (301)
1351379700 isdst flag now 1 (301)
1351383300 isdst flag now 1 (301)
1351390500 isdst flag now 0 (301)


.......

#include <stdio.h>
#include <time.h>
#include <string.h>

void do_time(int hour)
{
        time_t utc;
        struct tm tp;

        memset(&tp,0,sizeof(tp));

        /* construct a time on Sunday 29 October 2012 (the day the clocks go back at 2am) */
        tp.tm_hour = hour;
        tp.tm_min = 15;
        tp.tm_sec = 0;
        tp.tm_year = 2012 - 1900;
        tp.tm_mon = 9;
        tp.tm_wday = 0;
        tp.tm_mday = 28;
        tp.tm_isdst = -1;

        utc = mktime( &tp );
        printf("%d isdst flag now %d (%d)\n",utc, tp.tm_isdst, tp.tm_yday);
}


int main(int argc, char** argv)
{

        /* why do these two time/dates ... */
        do_time(1);
        do_time(2);

        do_time(0);

        /* ... produce different time_t dates from these two time/dates? */
        do_time(1);
        do_time(2);

        return 0;
}

---

### Post by r-senior on 2012-03-08
I don't know the answer, but I can confirm I get the same result:

```
$ ./time
1351386900 isdst flag now 0 (301) 2012-10-28 01:15 GMT
1351390500 isdst flag now 0 (301) 2012-10-28 02:15 GMT
1351379700 isdst flag now 1 (301) 2012-10-28 00:15 BST
1351383300 isdst flag now 1 (301) 2012-10-28 01:15 BST
1351390500 isdst flag now 0 (301) 2012-10-28 02:15 GMT

```

This all seems a bit weird. By setting tm_isdst to -1, you ask mktime to figure out the DST using its calendar. But shouldn't the first line be BST, not GMT? 01:15 is before the clocks go back.

I suppose 02.15 is definitely GMT and 00:15 is definitely BST. But 01:15 could be BST or GMT before/after the switch. How would it know which you meant if you specify tm_isdst as -1?

Anyway, those were my musings ...

I've taken the liberty of running indent on it and put it into CODE tags (see the posting toolbar - the # option) to make it easier to read in the thread, along with output of the human-readable time:

```
#include <stdio.h>
#include <time.h>
#include <string.h>

void do_time(int hour)
{
	time_t utc;
	struct tm tp;

	memset(&tp, 0, sizeof(tp));

    	/* construct a time on Sunday 29 October 2012 (the day the clocks go back at 2am) */
	tp.tm_hour = hour;
	tp.tm_min = 15;
	tp.tm_sec = 0;
	tp.tm_year = 2012 - 1900;
	tp.tm_mon = 9;
	tp.tm_wday = 0;
	tp.tm_mday = 28;
	tp.tm_isdst = -1;

    	/* Added conversion to human-readable format using strftime */
	char buf[128];
	utc = mktime(&tp);
	strftime(buf, 127, "%Y-%m-%d %H:%M %Z", &tp);
	printf("%d isdst flag now %d (%d) %s\n", utc, tp.tm_isdst, tp.tm_yday, buf);
}

int main(int argc, char **argv)
{

    	/* why do these two time/dates ... */
	do_time(1);
	do_time(2);

	do_time(0);

    	/* ... produce different time_t dates from these two time/dates? */
	do_time(1);
	do_time(2);

	return 0;
}
```

---

### Post by r-senior on 2012-03-08
As a footnote, I copied the same code to my Mac running Mac OS X Lion and compiled it:

```
$ ./time
1351383300 isdst flag now 1 (301) 2012-10-28 01:15 BST
1351386900 isdst flag now 0 (301) 2012-10-28 01:15 GMT
1351379700 isdst flag now 1 (301) 2012-10-28 00:15 BST
1351383300 isdst flag now 1 (301) 2012-10-28 01:15 BST
1351386900 isdst flag now 0 (301) 2012-10-28 01:15 GMT

```

So at least that's consistent. Whether that makes it correct or incorrect is a different question.

---

### Post by ofnuts on 2012-03-08
> **MrWheeliebin said:**
> Consider the following code, why do the first two printfs differ from the last two? (NB: Requires that you are in the London time zone). Note the times are around the end of DST this year.

Is something global being changed in the system just by calling mktime?

"man mktime" says:
"*Calling mktime() also sets the external variable tzname with information about the current timezone.*"

---

