---
title: "gprof problems"
date: 2008-01-11
forum: Programming Talk
---

### Post by hateregistering on 2008-01-11
I'm running the gprof tool on Montavista linux, but I'm getting erroneous values on the times. For instance, I have a response to a gui action which takes more than one second, but the total time amount in the profiling output is about 30 ms. What could be wrong? How can I fix the problem? Please, I'm not very well experienced with linux - don't assume that I know much when you reply.

---

### Post by Zugzwang on 2008-01-11
Note that 30ms could be the right answer because the application might be waiting for some result from another thread, for some data from the disk or the network or something like that. When the application is inactive, the time elapsed is not taken into account (unless it is running some loop of the form "while(!isReady()) {};").

Another possibility is that in parallel, you have a lot of other programs running not connected to your profiling work which also need some CPU time.

---

