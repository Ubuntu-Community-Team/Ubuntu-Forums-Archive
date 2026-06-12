---
title: "How to make python prog to wait some time"
date: 2008-03-05
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-03-05
How do I make my python program to wait some time (several seconds)?
Like this:
```

print & do stuff
...

wait 6 seconds

...
continue doing stuff

```

---

### Post by WW on 2008-03-05
You can use the **sleep** function in the **time** module. E.g.
```

import time

print "This"
time.sleep(6)
print "and that."

```

---

### Post by crazyfuturamanoob on 2008-03-06
Thanks. It works.

---

### Post by crazyfuturamanoob on 2008-07-25
> **WW said:**
> You can use the **sleep** function in the **time** module. E.g.
```

import time

print "This"
time.sleep(6)
print "and that."

```
Oh wait, how can I do that in milliseconds? If I want it to sleep for 200 milliseconds, will I type in 0.2?

---

### Post by kpkeerthi on 2008-07-25
```

sleep(...)
    sleep(seconds)

    Delay execution for a given number of seconds.  [B][COLOR="Blue"]The argument may be
    a floating point number for subsecond precision[/COLOR][/B].

```

---

### Post by The Cog on 2008-07-25
> Oh wait, how can I do that in milliseconds? If I want it to sleep for 200 milliseconds, will I type in 0.2?
Yes. I guess the resolution depends on the OS though.

---

