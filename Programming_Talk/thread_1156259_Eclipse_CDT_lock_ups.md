---
title: "Eclipse CDT lock ups"
date: 2009-05-11
forum: Programming Talk
---

### Post by SolarBear on 2009-05-11
Hi ! Considering this is a question concerning an IDE, and not programming itself, perhaps I'm posting in the wrong forum... anyway.

I've installed Eclipse and Eclipse CDT (for C++ development) on a fresh Jaunty install. The problem I keep getting is that each time I type in something to access methods or members, like this :
```

object.
//or
object->

```
Eclipse will lock up for 5 to 10 seconds, becoming non-responsive (the screen even goes dark meanwhile). This is extremely annoying, to the least.

Does anyone familiar with Eclipse and possible CDT have any solution to this problem ? Thank you.

---

### Post by gmatt on 2009-05-11
Please download and install Eclipse from the Eclipse website. For some reason Eclipse in the Ubuntu repositories is:

-outdated
-GCJ is listed as a requirement, but GCJ does NOT work with eclipse.

Also make sure that you uninstall GCJ before you run Eclipse again, OR at least set Open-JDK or Sun Java as your default java. See
[http://ubuntuforums.org/showthread.php?t=1152336](http://ubuntuforums.org/showthread.php?t=1152336) .

---

### Post by SolarBear on 2009-05-11
> **gmatt said:**
> Please download and install Eclipse from the Eclipse website. For some reason Eclipse in the Ubuntu repositories is:

-outdated
-GCJ is listed as a requirement, but GCJ does NOT work with eclipse.


Thanks for the heads up. You're right, Ubuntu's version of Eclipse is quite outdated, which is a bit odd.

For those interested, the eclipse homepage now offers a complete C++ programming package which includes a few pre-bundled tools for C++ development, including CDT of course.

---

