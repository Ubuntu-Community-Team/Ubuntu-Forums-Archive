---
title: "What's the thread limit for ubuntu"
date: 2008-12-06
forum: Programming Talk
---

### Post by caonima on 2008-12-06
I am coding a thread intensive program which will create about 7800+ threads. Every time the program failed to create more than 142 threads with the error Resource temporarily unavailable. I don't think the resource referred to memory b/c I used more than 4Gb memory on that server before. So what's the thread limit for ubuntu and how to configure the limit. The kernel version is 2.6.24-16 x86-64. Thanks.

---

### Post by stroyan on 2008-12-06
First, a process should not have 7800 threads!  Why on earth would you do that?

Second, there are multiple resource limits that may prevent thread creation.
But I don't know what limit you would be reaching with 142 threads on a 64-bit kernel.

It is common to reach a pretty low limit because of thread stack size on a
32-bit kernel.  The default for the per-thread stack size is the same as the
"ulimit -s" stack size of a process.  That will chew up 3GB really quickly with
a relatively large stack limit like 8MB.  You could check "getconf LONG_BITS"
and confirm that you really are using a 64-bit kernel.

Thread creation could also fail because of exceeding setrlimit RLIMIT_NPROC.
That is visible as "ulimit -u".  But the default for that is very high.

You could also use "strace -f a.out" to see exactly what system calls are
failing when your program fails to create new threads.

---

### Post by Tuna-Fish on 2008-12-06
Yeah, unless you have 7000+ processor cores you really should set up a thread pool.

---

### Post by slavik on 2008-12-06
see if you can reuse threads, I did a test once, where creating a thread for every operation caused the thread creation to take more time than the actual calculations.

---

### Post by cszikszoy on 2008-12-07
You should research threads a bit.  There is quite a performance penalty associated with creating threads and destroying threads.  As someone else suggested, set up a threadpool and just add whatever jobs you need threads to do to some type of queue.

---

### Post by Delever on 2008-12-07
In ideal situation you would only need as much threads as processing units you have. However, few more may be needed for input/output tasks and maybe one for interface. Compare that to 7800 threads.

If you have input/output situation and your threads actually do not do any processing, try to find how to do that task in non-blocking way with less threads. There might be APIs for that already, like epool for Linux files and sockets.

If your threads do actual processing, simple solution is set it up like this:

Job input queue,
Worker threads, as many as necessary, which either work or check input queue for new job, and if there is no new job, sleep.
Job result queue - depending on task you may want to reduce output to single thread again, so you can check this queue to take results.

Both queues need to be locked when dequeuing or enqueuing information.
Avoid having i/o operations on worker threads, because they are mostly waiting and not working. Above setup is for actual processing.

There are cases, however, when you need to wait and there is no way around it. Probably some limitation of API being used, and API call is blocking (call to function stops execution until it returns). Let's say, we have call to ping other computer, which either returns quickly if computer exists, or returns after 10 seconds if it doesn't. In this case you can put that call inside a thread, and execute 255 threads at once to check 255 computers. All threads are basically waiting, and you get results after 10 seconds, and user is happy. However this is bad ping implementation :)

So, if you have threads which are waiting and not using CPU, you can have more of them. If you have threads which are doing heavy processing, keep count to processing unit count.

---

### Post by caonima on 2008-12-08
Thanks guys. A thread pool is a better solution for my problem.

---

