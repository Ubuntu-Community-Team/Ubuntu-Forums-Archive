---
title: "Format time_t to show relative day names (today, yesterday,...)"
date: 2009-08-29
forum: Programming Talk
---

### Post by spupy on 2009-08-29
Hi. I'm trying to modify a program's method that formats a time_t variable. Right now the method prints the time in format "HH:MM:SS DD Month YYYY". I want to keep this format, but if the date is today or yesterday, show "today" or "yesterday" instead of the full date (the time format doesn't change).
Unfortunately, my C is on a very basic level, and this task is beyond my skills. After googling a little, the only idea I came up with is very crude - split the formatter string (strtok with " " as delimiter), compare the last 3 tokens with other strings strftime'd from the current time, compare the dates, and in case of 'today' or 'yesterday', append 'today' or 'yesterday' to the first token (the time part).
I'm not requesting code (although it would be very helpful big_smile). I'd like to know if this is best way to tackle this, or is there an easier way?
This is the code (from support.c from rox-filer):
```
/* Format this time nicely.
 * g_free() the result.
 */
char *pretty_time(const time_t *time)
{
    char time_buf[32];
    struct tm *tms;

    if (time == NULL)
        return g_strdup("(null)");

    tms = localtime(time);
    if (tms == NULL)
        return g_strdup("(invalid time)");

    if (strftime(time_buf, sizeof(time_buf), TIME_FORMAT, tms) == 0)
        time_buf[0]= 0;

    return to_utf8(time_buf);
}
```

EDIT: I looked at the tm struct. It looks like it would be easier to compare the fields (is it what they are called?) of this struct, and then do the concatenation of the time with either the date or 'yesterday'/'today'.

---

### Post by dwhitney67 on 2009-08-29
The time_t object represents the number of seconds since the *nix epoch (00:00:00 01/01/1970).  For instance, as I am writing this post, the time (on my system) is 1251551163.

With rudimentary math skills, one can deduce that there are (approximately) 86400 seconds in a day. (60 sec/min * 60 min/hour * 24 hour/day = 86400 sec/day)

So if you want to compute the date yesterday, or that of tomorrow, you can merely subtract or add 86400 from/to the current time.  Similarly, if you need to determine if a date is today, yesterday, or tomorrow, you can perform basic comparisons between two numbers.

Since you already have a pretty_time() function, the rest should be cake.

---

### Post by Gen2ly on 2009-08-29
Looks alot like this one:

[http://bbs.archlinux.org/viewtopic.php?id=79055](http://bbs.archlinux.org/viewtopic.php?id=79055)

;)

---

### Post by Cyanidepoison on 2009-08-29
> **Gen2ly said:**
> Looks alot like this one:

[http://bbs.archlinux.org/viewtopic.php?id=79055](http://bbs.archlinux.org/viewtopic.php?id=79055)

;)
I saw this thread and immediately thought I had a deja vu moment.

Then I went and checked archlinux.org too. :D

---

### Post by spupy on 2009-08-29
> **Gen2ly said:**
> Looks alot like this one:

[http://bbs.archlinux.org/viewtopic.php?id=79055](http://bbs.archlinux.org/viewtopic.php?id=79055)

;)

It's actually copy-paste. :)

---

### Post by soltanis on 2009-08-29
So like dwhitney said, you should either get the Unix time in seconds since the epoch, then check the time within the range of +/- a day; or, you should use the ctime(3) functions.

If you go with functions that use struct tm, then use the tm_wday field of the struct, which represents days since Sunday in the range of [0,6]. Using simple comparisons you can determine if the day is the same, or if it falls on yesterday or tomorrow. Bear in mind you also have to compare the date (day of the month, month of the year, and year) when you do the comparisons (because day of the week obviously isn't enough).

---

### Post by spupy on 2009-08-30
This is the new code I hacked somehow together so it at least compiles.
```
char *pretty_time(const time_t *ttime)
{
    char time_buf[32];
	struct tm *tms;

	if (ttime == NULL)
		return g_strdup("(null)");

	tms = localtime(ttime);
	if (tms == NULL)
		return g_strdup("(invalid time)");

    if (strftime(time_buf, sizeof(time_buf), TIME_DATE_FORMAT, tms) == 0)
		time_buf[0]= 0;

    //MOD--------------
    time_t today_t = time(NULL);
    time_t yesterday_t = today_t - 24*60*60;
    struct tm *today_tm = localtime(&today_t);
    struct tm *yesterday_tm = localtime(&yesterday_t);
    if(tms->tm_year==today_tm->tm_year && tms->tm_yday==today_tm->tm_yday){
        // is today
        char buf[32];
        strftime(buf, sizeof(buf), TIME_TIME_FORMAT, tms);
        strcat(buf, " Today");
        return to_utf8(buf);
    }
    if(tms->tm_year==yesterday_tm->tm_year && tms->tm_yday==yesterday_tm->tm_yday){
        // is yesterday
        char buf[32];
        strftime(buf, sizeof(buf), TIME_TIME_FORMAT, tms);
        strcat(buf, " Yesterday");
        return to_utf8(buf);
    }
    //-------------------
	return to_utf8(time_buf);
}
```
TIME_DATE_FORMAT shows only the date, while TIME_TIME_FORMAT shows only the time (HH:MM:SS).
I first create two time_t for today and yesterday. From them I create tm structs, and compare the year and day-of-the-year fields of the today,yesterday and actual date structs. If I find a match for today or yesterday, I format the actual time and append "Today" or "Yesterday" appropriately. Otherwise the full time+date is returned.
This method is used by the rox file manager to print the last-modified date field of a file. This code I added compiles, but unfortunately it doesn't work. All the files in a folder have the same time with "Today" appended. Could this be some weird problem with pointers?

---

### Post by dwhitney67 on 2009-08-30
It's is not a weird problem at all.  The problem is occurring because of the defined nature of localtime().  It returns a pointer to a statically declared object, and you are referencing this object when you perform your comparisons.  So, naturally, the "tms" time will always be the same as the "today" time.

Consider using localtime_r().  This function will require your application to provide the address of the struct tm object that you have either allocated or declared on the stack.  Based on your function pretty_time(), it would appear that declaring your struct tm objects on the stack would suffice.

Something like this:
```

...
   time_t today_t     = time(0);
   time_t yesterday_t = today_t - 24*60*60;

   struct tm today_tm;
   struct tm yesterday_tm;
   struct tm tms;

   localtime_r(&today_t, &today_tm);
   localtime_r(&yesterday_t, &yesterday_tm);
   localtime_r(ttime, &tms);
...

```

---

### Post by spupy on 2009-08-30
Thanks, dwhitney67. Combining your tips with the ones I got at the archlinux forums, this is the code that does what I need:
```
char *pretty_time(const time_t *ttime)
{
    char time_buf[32];
	struct tm *tms;

	if (ttime == NULL)
		return g_strdup("(null)");

	tms = localtime(ttime);
	if (tms == NULL)
		return g_strdup("(invalid time)");

    if (strftime(time_buf, sizeof(time_buf), TIME_FORMAT, tms) == 0)
		time_buf[0]= 0;

    //MOD--------------
    time_t today_t = time(NULL);
    time_t yesterday_t = today_t - 24*60*60;
    struct tm today_tm;
    struct tm yesterday_tm;
    localtime_r(&today_t, &today_tm);
    localtime_r(&yesterday_t, &yesterday_tm);
    if(tms->tm_year==today_tm.tm_year && tms->tm_yday==today_tm.tm_yday){
        // is today
        char buf[32];
        strftime(buf, sizeof(buf), TIME_FORMAT_TODAY, tms);
        return to_utf8(buf);
    }
    if(tms->tm_year==yesterday_tm.tm_year && tms->tm_yday==yesterday_tm.tm_yday){
        // is yesterday
        char buf[32];
        strftime(buf, sizeof(buf), TIME_FORMAT_YESTERDAY, tms);
        return to_utf8(buf);
    }
    //-------------------
	return to_utf8(time_buf);
}
```

Everyone, thank you for your help. :)

---

