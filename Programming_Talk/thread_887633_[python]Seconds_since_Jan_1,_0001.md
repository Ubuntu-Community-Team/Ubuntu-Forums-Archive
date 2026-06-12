---
title: "[python]Seconds since Jan 1, 0001"
date: 2008-08-12
forum: Programming Talk
---

### Post by Pyro.699 on 2008-08-12
Hello,

Ive spent since 3AM working on what at first seemed like a simple mindless task to eat up a few hours. It is not 12AM and its getting difficult to muster up the willpower to continue on.

Here is what ive gotten to so far. (The Epoch is the time since Jan 1, 0001)

[php]
from time import *
import re

re_digits_nondigits = re.compile(r'\d+|\D+')

def FormatWithCommas(format, value):

    parts = re_digits_nondigits.findall(format % (value,))
    for i in xrange(len(parts)):
        s = parts[i]
        if s.isdigit():
            parts[i] = _commafy(s)
            break
    return ''.join(parts)
    
def _commafy(s):

    r = []
    for i, c in enumerate(reversed(s)):
        if i and (not (i % 3)):
            r.insert(0, ', ')
        r.insert(0, c)
    return ''.join(r)

def isLeapYear(year):
    if year % 4 == 0:
        if ((year%100==0) and ((year%4)/100!=0)):
            return False
        else:
            return True
    return False;
    
def yearsToDays(year):
    years = range(1,year)
    days = 0
    for i in years:
        if isLeapYear(i):
            days=days+366
        else:
            days=days+365
    return days
        
def get(epoch, year, day, hour, minute, second, foreward):
    if isLeapYear
    time = (second + minute*60 + hour*3600 + (day + yearsToDays(year) - 11)*86400)

    return  time

while(True):
        ##Time since January 1, 0000, 12:00:00AM
        epoch = get("nothing", gmtime()[0], gmtime()[7], gmtime()[3], gmtime()[4], gmtime()[5], True)
                
        ##Time until August 16, 12:00:00 AM
        bday_start = get(epoch, 2008, 228, 16, 0, 0, False) 
        bday = bday_start - epoch
        
        print "[Epoch]: "+    FormatWithCommas('%i', epoch)+"  ~  "+\
              "[Birthday]: "+ FormatWithCommas('%i', bday)
        sleep(1)
[/php]

There is 11 days missing because of some event that took place in 1752 that removed them for some reason. But it seems that no matter how i modify it im off by about 2 hours. I know that python uses the system time so it shouldn't be too difficult to calculate this. I think i spoke too soon.

The function **get** works quite simply (explaining because of the first and last variables). The first variable will always be the epoch, time since jan 1, 0001 (expect where you are calculating it, which is why there is '"nothing"' there instead of a true value).The last value is there for future use but is intended to figure out if you are counting up or down, if your counting down it would set the year ahead so that you could continue the counter on to the next year without having to change the code.

Thanks for your help guys
~Cody Woolaver

---

### Post by cszikszoy on 2008-08-12
January 1, 0001 00:00:00 in epoch seconds is 
**-62135600400**


You can convert the current time to epoch seconds like this:
```

# For the local timezone
t = datetime.datetime.now()
print "Epoch Seconds:", time.mktime(t.timetuple())
#=> Epoch Seconds: 1060199000.0

# For UTC
t = datetime.datetime.utcnow()
print "Epoch Seconds:", time.mktime(t.timetuple())
#=> Epoch Seconds: 1060195503.0

```

Shouldn't be hard to subtract one from the other to get the total seconds elapsed...

---

### Post by Pyro.699 on 2008-08-12
Thanks,

From the code i have above, should everything else be correct? Like how i have it setup to countdown the seconds?

[edit]
Wouldn't that be from Jan 1, 1970?

---

### Post by cszikszoy on 2008-08-12
> **Pyro.699 said:**
> Thanks,

From the code i have above, should everything else be correct? Like how i have it setup to countdown the seconds?

I didn't look at it too thoroughly, but it looks OK.  You seem to be reinventing the wheel though, so to speak.  Python's time library has tons of functions.  Surely you don't have to rewrite functions to convert dates to seconds!  :)

---

### Post by Pyro.699 on 2008-08-12
I added 62135600400 to the epoch and got 63354155971, if you look at some sites that you can do something like this on, this number is off by a bit.

[Example Site](http://www.timeanddate.com/date/durationresult.html?m1=8&d1=12&y1=2008&h1=0&i1=0&s1=0&m2=1&d2=1&y2=1&h2=0&i2=0&s2=0)

Thanks again
~Cody Woolaver

---

### Post by cszikszoy on 2008-08-12
> **Pyro.699 said:**
> I added 62135600400 to the epoch and got 63354155971, if you look at some sites that you can do something like this on, this number is off by a bit.

[Example Site]("http://www.timeanddate.com/date/durationresult.html?m1=8&d1=12&y1=2008&h1=0&i1=0&s1=0&m2=1&d2=1&y2=1&h2=0&i2=0&s2=0")

Thanks again
~Cody Woolaver

I'm not quite sure I understand what you mean.  The "epoch" is time 0.0.  So adding anything to the "epoch" should still be the same.  The epoch refers to the date 00:00:00 UTC on January 1, 1970.

Also note that the number I gave you earlier was negative!  -62135600400The negative tells you that it is some time before January 1, 1970.

---

### Post by cszikszoy on 2008-08-12
actually, just look here:

Python already has a function to compute the difference between two dates.

[http://docs.python.org/lib/datetime-timedelta.html](http://docs.python.org/lib/datetime-timedelta.html)

---

### Post by Pyro.699 on 2008-08-12
> **cszikszoy said:**
> I didn't look at it too thoroughly, but it looks OK.  You seem to be reinventing the wheel though, so to speak.  Python's time library has tons of functions.  Surely you don't have to rewrite functions to convert dates to seconds!  :)
I was under the impression that epoch was the time from January 1, 0001 as that is what im trying to calculate.

---

### Post by dwhitney67 on 2008-08-12
The epoch can be anything you want it to be.  For *nix systems, the epoch is denoted to be Jan 1, 1970.  The C-library, which Python probably uses for some applications, returns the number of seconds since midnight of this date.

As mentioned earlier, try not to reinvent the wheel.  There are (presumably) Python libraries already available that allow you to perform date arithmetic.

Btw, in case you are not well versed in history, the catholic church mucked with the dates back in the late 16th century.  Nowadays the typical calendar we (in most countries) use is more properly known as the "gregorian" calendar.  Dates prior to the gregorian epoch don't jive with the calendar we use today.

---

### Post by cszikszoy on 2008-08-12
> **dwhitney67 said:**
> Btw, in case you are not well versed in history, the catholic church mucked with the dates back in the late 16th century.  Nowadays the typical calendar we (in most countries) use is more properly known as the "gregorian" calendar.  Dates prior to the gregorian epoch don't jive with the calendar we use today.

Right.  The website that the OP linked to contains this not:

```

**Note:**The From date is a Julian calendar date. The current Gregorian calendar was adopted in United States where Thursday, September 3, 1752 was the first of [11 days that were skipped]("http://www.timeanddate.com/calendar/monthly.html?year=1752&month=9&country=1").  This has been accounted for in this calculation. Read more about the [Julian and Gregorian calendars]("http://www.timeanddate.com/date/leapyear.html")

```

---

### Post by pmasiar on 2008-08-12
BTW, if you want to be really exact, are you aware that astronomers occasionally add or remove a second, to be compatible with earth rotation? Not sure if mentioned libraries take that into account (and if you care), just FYI.

---

### Post by dwhitney67 on 2008-08-12
You are referring to leap-seconds that "top" scientists add to the "official" UTC time.  The Earth's rotation is approximately 23'56" (or something like that) per day, not the exact 24 hours everyone is raised to believe.

Our clocks, calendars, and even our libraries (Python, C++, Java, etc) are written with the notion that there are exactly 24 hours (or 86400 seconds) per day.  The leap-seconds do not effect this whatsoever.

Btw, the _measurement_ of time was invented by man.  This concept can be redefined at anytime to fit man's needs.  For instance, in a few weeks when I step off the plane in Thailand, the year will be 2551 or something like that.  Talk about leaping into the future!

---

### Post by pmasiar on 2008-08-12
Yes, [http://en.wikipedia.org/wiki/Leap_second](http://en.wikipedia.org/wiki/Leap_second)

---

