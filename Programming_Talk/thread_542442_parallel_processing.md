---
title: "parallel processing"
date: 2007-09-03
forum: Programming Talk
---

### Post by josesanders on 2007-09-03
I garbage-picked an old machine that was being thrown out by the CS department at my university, and when I opened it up, much to my surprise, I found two 500MHz PIII's on the same motherboard.  My research work at my university involves writing a lot of computationally intensive applications that are very parallel in nature, so I've been experimenting with some very rudimentary distributed processing, using a multi-treaded application running on Windows (I'm stuck with that because the system has to integrate into existing software), to divide the processing up to remote Ubuntu servers via SSH.

I would really like to try to experiment with the parallel machine, maybe eventually moving all of the computations onto a linux server and using Windows only to run the GUI, but I really don't know anything about operating systems (I'm an electrical engineer, not CS).  Can I even install Ubuntu on such an old, strangely configured system?  Would it be able to divide a multi-threaded application between the two processors automatically?  I don't even know where to begin, so any ideas would be appreciated.

---

### Post by slavik on 2007-09-04
yes you can (install and use ubuntu on such a system)

dividing the work to parallelize cannot be done automatically, even in functional languages (you have to tell the compiler/interpreter what can be parallel).

the quickest/dirties way to get into parallel programming is with fork (read the manpage) although there are things it makes inconvenient (depending on application). there is also pthread library. just google for each and you should be able to get some tutorials.

be prepared, parallelizing code can be very difficult because it is almost impossible to debug.

---

### Post by fct on 2007-09-04
Linux has load balancing for threads, so yes, as long as the application is programmed in a multi-threaded way, both processors will be used.

If you want to really use distributed processing, you might want to look into setting up a cluster and using the MPI library.

---

### Post by public_void on 2007-09-04
You might want to take a look at GCC 4.2. It now supports [OpenMP]("http://www.openmp.org/drupal/")(Open Multi Processing).

Do a server install of Ubuntu. I installed successfully on a 533Mhz AMD,  128MB RAM.

---

### Post by fct on 2007-09-04
While we are on new advances, this might be interesting to you:

[http://www.intel.com/cd/software/products/asmo-na/eng/294797.htm](http://www.intel.com/cd/software/products/asmo-na/eng/294797.htm)

---

