---
title: "Convert UTC Time to local time"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-01-09
We just had an earthquake and our [reporting service]("http://www.geonet.org.nz/quakes/latest") logs it in UTC Universal Coordinated Time.
For example
Earthquake information last modified: 2013-01-10T03:10:59.396Z (UT)

I have no idea what time this is?

Is there an app in Linux that I can paste the UTC time into and get the local time?

---

### Post by llamabr on 2013-01-09
you could just use the web:

[http://www.timeanddate.com/worldclock/difference.html](http://www.timeanddate.com/worldclock/difference.html)

---

### Post by Kevin McCready on 2013-01-10
I thought of that, but you have to do lots of calculations in your head, adjust for daylight savings, read off the difference etc etc.

I'd just like to be able to paste in the UTC and get the local time

Thanks though, amazing website!

---

### Post by Impavidus on 2013-01-10
Use date:
```
date --date="2013-01-10T03:10:59.396Z"
```This should give output in your local time zone (which I cannot demonstrate, as my system is set to UTC).

---

### Post by Zill on 2013-01-10
> **Kevin McCready said:**
> We just had an earthquake and our [reporting service]("http://www.geonet.org.nz/quakes/latest") logs it in UTC Universal Coordinated Time.
For example
Earthquake information last modified: 2013-01-10T03:10:59.396Z (UT)

I have no idea what time this is?..
It seems to me that the site you have given does the sums for you and shows both Universal Time *and* NZ Daylight Time (see screenshot).

---

