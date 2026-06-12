---
title: "Boot time"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by philliptweedie on 2008-06-24
I ran bootchart today (see attached) it has my boot time at 0:26.

I timed my boot up using a stopwatch 2:06. Any idea whats going on?

Any idea why it's so slow?

Any help would be really appreciated.

---

### Post by aquavitae on 2008-06-24
I assume the two times are for the same boot...

It looks like bootchart only records the actual boot, not the start of the xserver. Did you time to the same point or to the login screen?

---

### Post by shad0w_walker on 2008-06-24
Boot chart only tracks the time it takes Linux to boot up. It doesn't and can't track the boot up time of the system before Linux starts loading.

---

### Post by philliptweedie on 2008-06-24
I timed the whole thing from switching on to seeing the desktop.

I knew bootchart wouldn't measure the whole time, I assumed that for it to be only 25% of the boot time, there must be another problem. Does anyone else have this sort of ratio of linux boot time to actual boot time?

---

