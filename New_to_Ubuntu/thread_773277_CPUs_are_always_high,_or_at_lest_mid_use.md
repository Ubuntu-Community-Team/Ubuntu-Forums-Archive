---
title: "CPUs are always high, or at lest mid use"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by mecanologo on 2008-04-28
Hey all!
I start my Ubuntu, with a Core 2 Duo at 1.8 ghz, and 2 gigs RAM, and my CPU cores seem to be ALWAYS, at least 800 mhz in use.
Any way to reduce it?

---

### Post by alexforcefive on 2008-04-28
If you open system monitor, you can sort the list by cpu usage. Take a look at what's causing the high load and see if it's something you could remove/optimise/replace

---

### Post by Helios1276 on 2008-04-28
our specs are pretty similar and my cpu is quite high as well but ive never had a problem.

---

### Post by bikeboy on 2008-04-28
It might be helpful to first find out what's using your CPU time. The best way is to open a terminal (Applications > Accessories > Terminal) and type *top*. The terminal and top use very little CPU themselves, so it gives a good indication of what's going on.

---

### Post by skymera on 2008-04-28
Type "top" into the terminal without the "".

I prefer htop, clearer to undertsand and you can sort easily.

But either one should shed light onto yuor CPU usage.

---

### Post by mecanologo on 2008-04-28
Look, as you can see, my demand is 100%, yet
there's nothing taking it....

---

### Post by bikeboy on 2008-04-29
Are you getting a lot of disk access? I might be wrong, but I think the load averages take I/O into account, not just CPU use. Not sure how to hunt for programs that are causing a high I/O load though.

edit: Actually, your load averages aren't particularly high anyway. It was only the last 1 minute where it was above 1. What is leading you to conclude that CPU use is high?

---

### Post by mecanologo on 2008-04-29
I wonder... My HDDs are off on a while, and even that way!

---

