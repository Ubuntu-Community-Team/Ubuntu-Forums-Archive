---
title: "time measure in c++"
date: 2009-02-19
forum: Programming Talk
---

### Post by Ferrat on 2009-02-19
Well been looking around and can't find any real function to match time get time that windows has, I need something accurate down to milliseconds for my game engine and can't really seem to find anything accurate enough, well time.h or ctime is said to have nano seconds in clock_t but that seems to be some debate over how accurate it really is and how to use it? 

I just need something that can return time in milliseconds, anyone?? also preferably portable and not OS specific, needs to compile it on both Ubuntu and later for linux ARM version on Pandora :)

Any help would be great :)

---

### Post by dwhitney67 on 2009-02-19
Consider using gettimeofday().  It's usage is documented in the man-pages.  It offers time resolutions down to the microsecond range.

---

### Post by Ferrat on 2009-02-19
Ah thx :) seems to be just what I'm looking for :)

---

### Post by jimi_hendrix on 2009-02-19
you could also use the SDL timer...

---

### Post by Ferrat on 2009-02-19
> **jimi_hendrix said:**
> you could also use the SDL timer...

If I was using SDL I guess I could but I'm not :P 
SDL will mess up the port to Pandora because of problems with initializing OpenGL ES via SDL (last time I checked anyway, of I could use it just for the timer but prefer not to) :) 

but seem to have a problem with gettimeofday(), it returns in microseconds which is great but seems that it loops too often for time comparison, at least the way I do it so if it hits a high number on init time say "999" millisecond then it loops back to 0 making timing hard for a simple newTime > lastTime + X check :/ 
guessing I could add the second part of the struct and put a loop around the original one checking that seconds are the same or something then moving the numbers around but that seems like a lot of extra work, anyone got a simpler idea? :)

---

### Post by tmccubbin on 2009-02-19
The following isn't POSIX.1-2001 conforming, but works on most BSD derivatives as well as linux of course according to the manpage.

gettimeofday is most likely what you want. To calc time intervals, clear and compare the resulting struct timevals there are several predefined macros:

timeradd
timersub
timerclear
timerisset
timercmp

see the man page for timeradd

#> man timeradd

It is mentioned at the bottom of the gettimeofday man page

If you need high resolution timer callbacks then the answer would be very different...

hope this is helpful!

cheers,

-t

---

### Post by Ferrat on 2009-02-19
Thanks for the add function but solved it with a easy if function added checking the seconds, got it working down to a +-1ms :) that will do 

Thanks everyone for the help :)

---

