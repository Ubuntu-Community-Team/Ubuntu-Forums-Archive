---
title: "gprof - no time accumulated"
date: 2007-12-13
forum: Programming Talk
---

### Post by mehturt on 2007-12-13
I'm trying to profile my application but I'm not getting times, they are all 0.
From what I've found on the web - the common cause is application not running long enough or having multithreaded application, which is not my case.
What can be other cause of execution times not being reported by gprof?
Thanks
(using 7.10 on x86_64)

---

### Post by hod139 on 2007-12-14
I don't have a solution to your problem, but I do have an alternative.  IMO callgrind (a valgrind tool) is a much better profiler than gprof, and I have never had any problems with it.  Use callgrind to profile, and kcachegrind to view the results.

---

### Post by mehturt on 2007-12-14
Yes, callgrind / kcachegrind is nice indeed, I've been using it before but totally forgot about it.
Thanks for reminding me.

---

### Post by mitch_feaster on 2008-11-27
I know this post is quite old but I'm posting anyways in case anyone runs into this page searching.

I don't have a solution to your problem either, but (perhaps) an explanation.
gprof measures your program's *run time*, so any calls into kernel space don't get counted (so something like sleep(10) would look like it took 0 time to gprof).

Check out [http://www.ibm.com/developerworks/library/l-gnuprof.html#listing6]("http://www.ibm.com/developerworks/library/l-gnuprof.html#listing6").

Hope this helps (someone).

---

### Post by Nosferax on 2010-03-22
No matter. My program runs in user space entirely and I never get time estimates.

Using 9.10 x32.

---

