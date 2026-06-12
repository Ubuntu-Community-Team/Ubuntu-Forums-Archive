---
title: "difference in time_t between Unix and Linux"
date: 2006-04-04
forum: Programming Talk
---

### Post by Zizo on 2006-04-04
Hi all,

I am using time_t to do some measurements. There is a difference between the result of time_t on Linux and the result on Unix.

The same when I use: now = datetime.datetime.now() on Python

I need to run both python programs and C/C++ prgrams on Linux and Unix with the same time reference.

Does anyone has a solution for this?

---

### Post by hod139 on 2006-04-04
How big of a difference?  Are you running the code on different architectures?  Is the running time of the method relatively small compared to the accuracy of the clock?  

For a good read on accurate timing (at least for C++) see this page:
[http://www.cs.rpi.edu/~musser/gp/timing.html](http://www.cs.rpi.edu/~musser/gp/timing.html)

I don't know much about Python, but maybe the same techniques can be used.

---

### Post by Zizo on 2006-04-04
First thank you for the reply. 
 
Well I don't want to measure how fast is a piece of code or an algorithm, that's why I am not using clock(). 
 
I just want to have the number of seconds elapsed since the epoch. The difference is about more than 400 sec.
 
But since you asked me about the architecture. Well I guess I forgot to mention that I am running on simple Linux at one side and on a cluster of machines on the other side and the cluster is running Unix. Do you think this could be the problem? I mean the cluster architecture?
 
Thanks again

---

### Post by hod139 on 2006-04-04
Oh, I think I understand your problem.  Are you looking for something more along these lines [http://www.cplusplus.com/ref/ctime/mktime.html](http://www.cplusplus.com/ref/ctime/mktime.html)
or [http://www.cplusplus.com/ref/ctime/time.html](http://www.cplusplus.com/ref/ctime/time.html)

---

### Post by toojays on 2006-04-04
Are you sure it's not just that the timing really is that much out? Are you using NTP to keep the clocks in sync? How can you be sure that each machine in the cluster is calling time() at the same moment?

---

### Post by Zizo on 2006-04-05
I will try to make it clearer:

#python code:
now = datetime.datetime.now()
print "Epoch Seconds:", time.mktime(now.timetuple())    #this will print the epoch

// C-C++Code
time_t = time1;
time1 = time(NULL);
cout<<time1<<'\n';              // this will print the epoch as well

running these 2 piece of codes on the same machine will give the same number of seconds.

If I run the same C code for example on Linux and on the Cluster I get different values. And the program using this piece of code is not parallel so it only uses one processor.

The difference is exactly 487 seconds

---

### Post by toojays on 2006-04-06
What you are saying makes no sense to me. The epoch is a fixed time, which on UNIX (and GNU) is 1/1/1970.

In python you can see this with "  datetime.datetime.utcfromtimestamp(0)", and in C it's from "time_t = 0".

The code you have shown will show the number of seconds which have elapsed [em]since[/em] epoch. And my question for you is, once again: how do you know that the two machines have their clocks in sync, and how are you taking into account the time which elapses between running the code on one machine, and running it on the other?

---

### Post by Zizo on 2006-04-06
You are right about the clock sync, I must make sure of this issue. Can you give me any hint about using NTP?

---

