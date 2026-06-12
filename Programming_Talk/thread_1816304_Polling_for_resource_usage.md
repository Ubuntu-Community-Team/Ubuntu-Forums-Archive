---
title: "Polling for resource usage"
date: 2011-08-01
forum: Programming Talk
---

### Post by zobayer1 on 2011-08-01
I am trying to run polling on user+system time and total virtual memory used by a process which is forked from a parent process.
I used exec to run a program on the child process and poll it from the parent process.
The getrusage() method provides user+system cpu time, but I can't find total memory usage, again, from /proc/{pid}/status, I got the mem usage via vm_peak, now the problem I'm facing is using the getrusage() function, as it is not working with RUSAGE_CHILDREN as I expected. Probably it will work only when a child terminates.
Can anyone tell me a proper way to do this?

---

