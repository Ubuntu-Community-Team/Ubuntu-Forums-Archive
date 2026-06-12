---
title: "Should Ubuntu default to sun java once it's completely GPLed?"
date: 2007-04-07
forum: Programming Talk
---

### Post by marcelloba on 2007-04-07
I believe that once Sun's Java becames completely open-source (should happen by half of 2007), Ubuntu should ship with it instead of the glorious, but severely limited GNU Classpath. I was just wondering what other people think.

---

### Post by samjh on 2007-04-07
Agreed.

GCJ and other alternative distros have their respective merits, but Sun's Java implementation is the most feature-rich and stable of them all.  The only barrier was that Sun's Java was not truly "free and open-source".  Once Sun finishes the open-sourcing project, there shouldn't (theoretically) be any objections to Sun's Java becoming the default Java package.

---

### Post by DC@DR on 2007-04-07
Strongly agree!

---

### Post by treak007 on 2007-04-07
there really isn't much of a reason to keep using gcj. Wasn't the whole purpose of gcj was to provide an open source alternative to java?

---

### Post by russell.h on 2007-04-08
I'm no expert (I gave up on trying to understand all the crap surrounding Java) but my understanding was that GCJ can actually compile a java program to a standalone executable, which could lead to a speed increase. I'm not sure if thats even true, but if so it would be about the only reason I can think of to choose CCJ over Sun Java.

And of course if you are compiling to a non crossplatform standalone executable in order to get a speed boost you might as well be using C or C++ (or pretty much any language except java).

---

### Post by samjh on 2007-04-08
> **russell.h said:**
> I'm no expert (I gave up on trying to understand all the crap surrounding Java) but my understanding was that GCJ can actually compile a java program to a standalone executable, which could lead to a speed increase. I'm not sure if thats even true, but if so it would be about the only reason I can think of to choose CCJ over Sun Java.

And of course if you are compiling to a non crossplatform standalone executable in order to get a speed boost you might as well be using C or C++ (or pretty much any language except java).

According to some benchmarks, integer and float calculations are slightly faster with GCJ, but object and method handling are much faster on Suna Java.  I'd say for real applications, Sun Java would be superior.

Performance isn't the real consideration for using GCJ, though.  Ease-of-distribution comes to play.

---

### Post by Wybiral on 2007-04-08
Java isn't installed by default, so... Why can't we have both of them?

---

