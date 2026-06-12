---
title: "Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0."
date: 2008-07-11
forum: New to Ubuntu
---

### Post by jagannath on 2008-07-11
Hi guys,

I'm getting the following error message while installing skype:

sudo python /home/jagannath/Desktop/skysentials-1.0.1/skysentials.py
skysentials.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

What should I do, please?

I am using Hardy Heron.

Thanks a million,

Jagannath

---

### Post by LinuxRocks713 on 2008-07-31
It says exactly what the error message says: resource temporarily unavailable. Wait a few hours/days/years and try again. If it still doesn't work, try resetting and then try again.

---

### Post by artships on 2009-12-27
I know this is an old thread, but just in case this helps anybody:  I was getting ```
Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
``` which went away when, in an xterm, I executed:```
xhost +
```

---

