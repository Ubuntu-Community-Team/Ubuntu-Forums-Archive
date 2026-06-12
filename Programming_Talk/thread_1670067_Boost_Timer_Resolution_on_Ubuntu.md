---
title: "Boost Timer Resolution on Ubuntu"
date: 2011-01-18
forum: Programming Talk
---

### Post by rymjones on 2011-01-18
I wrote a timer service in C++ using the Boost 1.43(deadline_timer) w/ 1 ms resolution and unit tested in on RHEL. We switched OS to Ubuntu 10.4 now the highest resolution I can achieve is 4 ms. Even if I set the expiration time to 1 it will fire on the next closest 4 ms interval. 

I am not sure whether this is a problem in Boost or if there is some setup in Ubuntu?

---

