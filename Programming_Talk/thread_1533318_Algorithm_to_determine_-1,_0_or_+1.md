---
title: "Algorithm to determine -1, 0 or +1"
date: 2010-07-17
forum: Programming Talk
---

### Post by Krupski on 2010-07-17
[COLOR="Red"]**NOTE: I am not a student and this is not homework.**[/COLOR]

With that out of the way...

Hi all!

I've been racking my brain on this problem and just can't seem to find a decent solution.

What I need is an algorithm that will accept any number, negative or positive or zero, and ONLY return:

If number is negative, output is -1.
If number is zero, output is 0.
If number is positive, output is 1.

The range of input won't be terribly large... no more than a few thousand in either direction.

Anyone? This seems like it should be easy, but I seem to have a mental block for it. ](*,)

Thanks!

-- Roger

---

### Post by Can+~ on 2010-07-17
x/abs(x) when x != 0.

For vectors, this is called [normalization]("http://en.wikipedia.org/wiki/Normalized_vector"). Your problem is just a one-dimensional vector.

---

### Post by lisati on 2010-07-17
Pseudo code:
```

int sgn(x) {
    if (x<0) return -1;
    if (x>0) return 1;
    return 0;
    }

```

---

### Post by Krupski on 2010-07-17
Wow! That has to be a record for the fastest reply and the easiest solution!!!

Thank you to both **lisati** and **Can+~**!

Why didn't I think of that???

Thanks again!!!!

-- Roger

(edit to add): This is what I wanted it for... the program just tests "Zeller's Congruence" which is an algorithm that determines the day of the week for any date.


```

// zeller.c - zeller's congruence test program

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <time.h>

#undef BUFSIZ
#define BUFSIZ 1024

int readln(FILE *);
int getusr(int, int, char *);
int ppf(int);

int main(void)
{

	const char *day_name[7] = {
		"Sunday", "Monday", "Tuesday", "Wednesday",
		"Thursday", "Friday", "Saturday"
	};

	const char *month_name[12] = {
		"January", "February", "March", "April", "May", "June", "July",
		"August", "September", "October", "November", "December"
	};

	const char *tense[3] = { "was", "is", "will be" };

	time_t now;
	struct tm *ts;
	char buf[BUFSIZ];

	int month, day, year;
	int curmonth, curday, curyear;

	long int today, anyday;

	time(&now);
	ts = localtime(&now);

	strftime(buf, sizeof(buf), "%m", ts);
	curmonth = atoi(buf);

	strftime(buf, sizeof(buf), "%d", ts);
	curday = atoi(buf);

	strftime(buf, sizeof(buf), "%Y", ts);
	curyear = atoi(buf);

	// get current date for proper tense
	today = (curyear * 365) + (curmonth * 12) + curday;

	fprintf(stdout, "\n");

	if ((month = getusr(1, 12, "Enter the month: ")) == 0) {
		return 1;
	}
	if ((day = getusr(1, 31, "Enter the day  : ")) == 0) {
		return 1;
	}
	if ((year = getusr(1, 9999, "Enter the year : ")) == 0) {
		return 1;
	}

	anyday = (year * 365) + (month * 12) + day;

	if (month < 3) {
		month += 12;
		year -= 1;
	}

	int dow =
	    (((day + (((month + 1) * 26) / 10) + year + (year / 4) +
	       (6 * (year / 100)) + (year / 400)) - 1) % 7);

	if (month > 12) {
		month -= 12;
		year += 1;
	}
	month -= 1;		// make index zero based

	fprintf(stdout, "\n%s %d, %04d %s a %s\n", month_name[month], day, year,
		tense[ppf(anyday - today) + 1], day_name[dow]);
	fprintf(stdout, "\n");

	return 0;
}

int readln(FILE * fp)
{
	char buf[BUFSIZ];
	int len;
	double dnum;

	buf[0] = 0;
	fgets(buf, BUFSIZ, fp);

	len = strlen(buf);

	while (len >= 0) {
		if (buf[len] <= 32) {
			buf[len] = 0;
			len--;
		} else {
			break;
		}
	}

	len++;
	buf[len] = 0;
	dnum = atof(buf);
	return (int)((dnum < 0) ? (dnum - 0.5) : (dnum + 0.5));
}

getusr(int low, int high, char *prompt)
{
	int count = 0;
	int n = -1;
	while (n < low || n > high) {
		fprintf(stdout, "%s", prompt);
		n = readln(stdin);
		count++;
		if (count == 3) {
			return 0;
		}
	}
	return n;
}

int ppf(int n)
{
	return (n > 0 ? 1 : (n < 0 ? -1 : 0));
}

```


Note the tiny function at the bottom... "ppf" (past, present, future). I use it as an index to print "was", "is", or "will be" as appropriate.


Thanks again for the help!

-- Roger

---

