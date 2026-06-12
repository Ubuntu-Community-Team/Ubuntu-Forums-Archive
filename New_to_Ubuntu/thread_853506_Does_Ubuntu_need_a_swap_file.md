---
title: "Does Ubuntu need a swap file?"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by FTBPrimeEvil on 2008-07-08
I don't have any problems, but does Ubuntu need a swap file to perform better?

deanjw@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3955        709       3245          0         14        323
-/+ buffers/cache:        371       3583
Swap:            0          0          0

---

### Post by sdennie on 2008-07-08
With 4G of RAM, you will probably never use a swap partition but, you can add one if you like (having one or not having one won't effect performance in your case).  The only real benefit would be if you had an application that started to eat all available memory.  With a swap partition you'd probably notice this before it started to do something harmful to the system because you'd noticing your drives going crazy and the system starting to become unresponsive as memory started swapping out.  You also need swap if you plan to use the hibernate ability found on most laptops.

---

### Post by ramjet_1953 on 2008-07-08
Even if you have lots of RAM, the swapfile still has a couple of uses.

1. If you happen to be running a very intensive application, like a large spreadsheet and you do a big re-calculate, the swapfile may come into play. The same if you have several processor-intensive applications all running at once it may also kick-in.

2. If you have a laptop, the swapfile is used for suspend and hibernate.

Regards,
Roger :cool:

---

