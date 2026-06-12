---
title: "Maximum number of threads allowed"
date: 2012-04-10
forum: Programming Talk
---

### Post by dland on 2012-04-10
I have a web service running on an amazon cloud m1.small box, which has the following stats:

Ubuntu 10.04.4 LTS
32-bit
1.7 GB memory

The service is written using the cyclone async web server and talks to a MySQL database using twisted's adbapi library. The important thing about that is that each request to the web server spins off a new thread to talk to the database.

I'm doing some load testing using grinder and I'm starting to get thread related errors at around 150 concurrent requests to the web server. The error is

```

thread.error: can't start new thread

```

I did some reading on the subject, and most people seem to agree that there is no concept in linux of a setting for the maximum allowed number of threads per process. Apparently, how many threads are allowed is based on how much memory you have and how much memory is allocated per thread ([http://stackoverflow.com/questions/344203/maximum-number-of-threads-per-process-in-linux](http://stackoverflow.com/questions/344203/maximum-number-of-threads-per-process-in-linux)). However, I'm not seeing support for that in my testing. I put together a simple python script that starts up some configurable amount of threads and keeps them all running. I ran it several times until I determined the exact amount of threads that the system will support before giving me the error. That number turns out to be 382. Kind of an odd number. The other odd thing about it is that I can run multiple instances of that app, each spinning up 382 threads and none of them will give me the thread error. However if I run a single instance that tries to create 383 threads, I get the error. To me that points to a process specific maximum on threads, contrary to what I've been reading.

So my question is, how does ubuntu cap the number of threads you can generate and is there a way to increase this number through some kind of system config?

---

### Post by Tony Flury on 2012-04-10
> **dland said:**
> I have a web service running on an amazon cloud m1.small box, which has the following stats:

```

thread.error: can't start new thread

```

So my question is, how does ubuntu cap the number of threads you can generate and is there a way to increase this number through some kind of system config?

I haven't done any testing myself - but what does your test thread do ? could it be something simple like the memory consumed by your process - have you been able to track memory usage as it grows as you start more threads up ?

It could be that there is limit on the memory per process - and that is limiting your threads per process.

---

### Post by dland on 2012-04-10
> **Tony Flury said:**
> I haven't done any testing myself - but what does your test thread do ? could it be something simple like the memory consumed by your process - have you been able to track memory usage as it grows as you start more threads up ?

It could be that there is limit on the memory per process - and that is limiting your threads per process.


Interesting idea, but I doubt it's the cause. In the real app, the threads connect to a MySQL database and either pull back or push in a small amount of data. One or two small transactions per thread. In the my test app, the threads pretty much do nothing. They sit in a loop and sleep. I just wanted to get them spun up and running. Top shows this after the test app started up one too many threads.

```

Mem:   1757264k total,   474728k used,  1282536k free,   100180k buffers
...
PID     USER       PR   NI   VIRT      RES    SHR    S  %CPU  %MEM    TIME+    COMMAND                                                                                                  
5803    ubuntu     20   0    3050m     8180   2104   S  0.3   0.5     0:00.30  python

```

---

### Post by MadCow108 on 2012-04-10
382 is not a surprising number for a 32 bit machine.
each thread has its own stack space, which is by default 8mb (see ulimit -a)
382*8mb = 3GB which is approximatly the limit of adressable space per process on a 32 bit machine (2-3.5gb depending on kernel)

try decreasing the thread stack size and you should be able to create more.
via ulimit -s or threading.stacksize(X)

also its likely that the stack memory of each thread is just copy-on-write memory mapped, so you can create more processes as long as you have enough swap and it won't really show up as used in top
(java behaves very similar and has the -Xssn flag to adjust the thread stack size)

---

### Post by dland on 2012-04-10
> **MadCow108 said:**
> 382 is not a surprising number for a 32 bit machine.
each thread has its own stack space, which is by default 8mb (see ulimit -a)
382*8mb = 3GB which is approximatly the limit of adressable space per process on a 32 bit machine (2-3.5gb depending on kernel)

try decreasing the thread stack size and you should be able to create more.
via ulimit -s or threading.stacksize(X)

also its likely that the stack memory of each thread is just copy-on-write memory mapped, so you can create more processes as long as you have enough swap and it won't really show up as used in top
(java behaves very similar and has the -Xssn flag to adjust the thread stack size)


Well, decreasing the stack size did, in fact, work. I'm not that familiar with copy-on-write as it applies to memory sharing across processes, but I'll take your word for it and assume that explains why I can run multiple copies of the script at once without thread errors.

Thanks for the help.

---

### Post by MadCow108 on 2012-04-10
its probably more related to overcommiting than copy-on-write (which is indeed more relevant for processes):
try setting /proc/sys/vm/overcommit_memory to 2 and it will fail as soon as you have used up everything.
see man proc

---

