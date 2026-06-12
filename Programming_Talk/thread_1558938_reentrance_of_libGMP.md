---
title: "reentrance of libGMP"
date: 2010-08-22
forum: Programming Talk
---

### Post by rybu on 2010-08-22
Hi, 

I have some software and I'm experimenting making aspects of it multi-threaded, using pthreads. 

I'm having some problems making the software compatible with pthreads, in particular I'm getting some segmentation faults.  gdb and valgrind have been some help in localizing the problem but it's still a little foggy to me what the exact problem is. 

I apologize if this isn't the right forum for these questions. 

One question that I have that's Ubuntu-specific is that I'm using the GNU MP library.  In the documentation it specifies whether or not GMP is compatible with multi-threading:

[http://gmplib.org/manual/Reentrancy.html](http://gmplib.org/manual/Reentrancy.html)

In particular it's talking about how the GNU MP library is compiled. 

Ihave libgmp3c2 installed (via apt/synaptic, standard repositories), version: 2:4.3.2+dfsg-1ubuntu1.  

Does anyone know whether that was compiled in a reentrant-compatible way?  How would one check? 

If you're curious, I have more details on my experiment with pthreads, here: [http://stackoverflow.com/questions/3543921/segmentation-fault-using-pthreads-which-disappears-when-running-in-gdb](http://stackoverflow.com/questions/3543921/segmentation-fault-using-pthreads-which-disappears-when-running-in-gdb)

Thanks for any information.

---

