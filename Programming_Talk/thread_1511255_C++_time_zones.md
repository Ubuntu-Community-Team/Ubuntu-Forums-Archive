---
title: "C++ time zones"
date: 2010-06-16
forum: Programming Talk
---

### Post by jw37 on 2010-06-16
Hi all,

I'm trying to
1) get access to the time zones in tzdata package (which is of course installed;) and
2) convert any local time of any time zone to universal time.

Any ideas how to do that?

---

### Post by dwhitney67 on 2010-06-16
Before you attempt to re-invent the "wheel", look here:
[http://www.boost.org/doc/libs/1_38_0/doc/html/date_time.html](http://www.boost.org/doc/libs/1_38_0/doc/html/date_time.html)

---

### Post by jw37 on 2010-06-17
Thanks! I begin studying that. Seems very useful for time calculations in general, too. :)  I'll be back when I get stuck...

---

### Post by jw37 on 2010-06-28
Well the time zones in the Boost library are good but they lack sense of history, that is, there is only one (or zero) daylight saving time rule per one time zone. In reality, the daylight saving started around 1980 and the rules have changed in many cases since then. So in reality, there are many rules per one time zone.

I need to use a time zone database that knows the difference "local time - universal time" for every location and every moment since the estabilishment of time zones. In practice, that means knowing the dayligt saving time rules on every time zone.

The Olson database (=tzdata) is the only one I know that seems to fullfill these requirements. Feel free to inform me if you know another!

So back to the first question: how to access the tzdata in C++?

I downloaded the C code mentioned in the -> [tzdata documentation]("http://www.twinsun.com/tz/tz-link.htm") from [ftp://elsie.nci.nih.gov/pub/](ftp://elsie.nci.nih.gov/pub/) . I've been staring at the code files but don't know where to start. I don't understand C very well. What are the functions needed for what I told above? If someone is familiar with that code please give me a hint.

---

### Post by nullie on 2011-11-14
You probably need to use set environment variable TZ and use glibc functions mktime and localtime.

---

### Post by ehmicky on 2011-11-14
Hi,

For the fact that time_zone in Boost doesn't take into account the fact that DST is only a recent move, changed over time, and depends on the country :
You can create a method which takes a local_time as a parameter and returns another local_time.
Inside the method you examine the posix_time_zone associated with the parameter, fix it if there was no DST at that time (or if DST rule were different) and returns a new local_time based on the fixed posix_time_zone.
The big part would be to deduce the country from for example the std_abbrev_name attribute of posix_time_zone, and to actually make all the checks and fixes for any country at any time of history.
But it should fix your issue, and you'll still be able to use local_time, time_duration, etc. without any additional change. I think boost::date_time is quite powerful once learned (although it's the only time library I know), so it's worth sticking with it I guess.

For the tzdata, did you look at boost::local_time::tz_database ?

---

