---
title: "Java java.util.Date Rounding Question"
date: 2010-01-31
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-01-31
I have some arbitrary time, such as 11:34:03 (hour, minute, second) stored in a java.util.date variable.  I want to know the nearest x-minute (or x-hour or x-second) time interval.  For example, if I want to know the nearest 5-minute time interval to 11:34:03, that would be 11:35:00.  The nearest 15-minute time interval to 11:34:03 would be 11:30:00.  Anyone know how to do this?  Apache.commons.lang has a rounding utility for Date class, described here: [http://www.kodejava.org/examples/257.html](http://www.kodejava.org/examples/257.html).  But that will only work for finding the nearest minute, hour, etc, not arbitrary time intervals.  Any ideas?

---

### Post by dwhitney67 on 2010-01-31
The person(s) who wrote the Apache utility probably had the same question many moons ago.

Why not try to think of the solution yourself.  I mean, off the bat, I came up with:
```

while (unit % interval != 0)
{
   int mod = unit % interval;

   if (mod > (interval / 2))
   {
      unit += (interval - mod);
   }
   else
   {
      unit -= (interval - mod);
   }
}
if (intervalUnit == MINUTES)
{
   secs = 0;
}

```
Of course, this little snip hasn't a clue of the context of the 'interval'.  If it were minutes, then you would need to zero out the seconds.  That's the little if-conditional I tacked on at the end.

P.S.  The value of 'unit' is either the seconds or the minutes.  If you need to round to the nearest hour, examine the minutes and seconds fields.  If minutes is greater-than-or equal to 30 && seconds is greater-than-or-equal to 0, round up; otherwise round down.

---

### Post by SNYP40A1 on 2010-02-01
> **dwhitney67 said:**
> The person(s) who wrote the Apache utility probably had the same question many moons ago.

Why not try to think of the solution yourself.  I mean, off the bat, I came up with:
```

while (unit % interval != 0)
{
   int mod = unit % interval;

   if (mod > (interval / 2))
   {
      unit += (interval - mod);
   }
   else
   {
      unit -= (interval - mod);
   }
}
if (intervalUnit == MINUTES)
{
   secs = 0;
}

```
Of course, this little snip hasn't a clue of the context of the 'interval'.  If it were minutes, then you would need to zero out the seconds.  That's the little if-conditional I tacked on at the end.

P.S.  The value of 'unit' is either the seconds or the minutes.  If you need to round to the nearest hour, examine the minutes and seconds fields.  If minutes is greater-than-or equal to 30 && seconds is greater-than-or-equal to 0, round up; otherwise round down.

I basically did that...

I take a Java Date instance and call getTime() on it to get a long representing the number of ms since some event in the 1970s.  Then I find the round the number to previous 5 min interval using this code:

long time = enddate.getTime();
time -= time % (1000 * 60 * 5);

I guess that will work...I could always make my own Date Utility class to clean up the code a bit.  If I do, I'll share the code here.  Thanks!

---

