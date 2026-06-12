---
title: "cannot debug files containing calls to String class methods"
date: 2007-06-17
forum: Programming Talk
---

### Post by vadania on 2007-06-17
I use Ubuntu 7.04, java 1.5.0 sun, Eclipse 3.2.
When I debug programs containing String constructor (new String("abc")), or toCharArray() the IDE panics and says it can not find sources for rt.jar. (java 1.5 sun was non free software, so there is no source, right?)
Program's execution stops, after it complains there are no sources.

When I run normaly (no debug), the program runs perfectly.
The idea is am just learning java I do not need to look into how java.lang.String is implemented.
So I would like Eclipse to just skip this call (no trace).

---

### Post by nitro_n2o on 2007-06-17
While debugging click on "Step Over" instead of "Step into" The two button are next to each other... just hover over the button and you'll see it's name

---

### Post by vadania on 2007-06-19
Mighty Thanks! Your answer helped me a lot.

---

