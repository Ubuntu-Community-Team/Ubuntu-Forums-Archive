---
title: "threads and sleeping."
date: 2008-05-25
forum: New to Ubuntu
---

### Post by mashamoo on 2008-05-25
Hi,

I didn't know where else to post this, and it looks like this section is reasonably active.

I am writing a multithreaded c++ program using pthreads lib. 

I am trying to make my threads sleep for less than 10ms, but it seems to sleep for approx 10ms regardless. 

I read something about linux scheduler waiting 10ms before switching control over to a new thread. Is there any way of getting around this? Why do they offer a usleep function if you can't even get microsecond accuracy?

Of course I could make my own loop that does nothing for the time I want, but then it eats the CPU time and defeats the purpose of sleep functionality.

Help please!

---

