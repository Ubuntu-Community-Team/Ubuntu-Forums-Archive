---
title: "[SOLVED] Which packages should I install for OpenMP programming?"
date: 2008-02-28
forum: Programming Talk
---

### Post by Ryozanpaku Tiger on 2008-02-28
Dear all,

Which packages should I install in addition to *build-essential*, if I would like to use advantages of Core 2 Duo?

Thank you!

---

### Post by olejorgen on 2008-02-28
Installing openmpi wont automatically parallallize anything. You're also probably better of using threads than MPI for just dual core. That beeing said I think all you need is openmpi-dev

---

### Post by Ryozanpaku Tiger on 2008-02-28
Thank you! Yes, sure nothing will be parallilized automatically, but I need to install an parallel programming tool anyway,:)

But I don't see *openmpi-dev* in the Synaptic Package Manager! Where should I look for it?

---

### Post by WW on 2008-02-28
The [openmpi packages](http://packages.ubuntu.com/search?keywords=openmpi&searchon=names&suite=gutsy&section=all) are in the **universe** repository.

---

### Post by matja on 2008-02-28
Hi guys,

Just to make sure there isn't a misunderstanding, there's a difference between OpenMP and OpenMPI.

In my world, OpenMP is used by processors (cores) with shared-memory (like the Core 2 Duo), while MPI is a more general interface for communication between processors used mainly in computer clusters (probably together with OpenMP on recent multi-core clusters).

Of course you can use MPI even if the memory is shared between the processors, but OpenMP might be simpler and was what the OP mentioned in this thread's title. gcc should have support for OpenMP from version 4.2.

If you already knew this, please disregard this post,
Cheers!

---

### Post by gururise on 2008-02-28
**libgomp** is what you need for OpenMP.

Haven't tried it out yet, as I've been using pthreads and/or the thread abstraction layer provided by Glib.

---

### Post by olejorgen on 2008-02-28
ah.. I'm taking a parallell programming class using mpi so my brain automatically added a "i". :) Sorry.

---

### Post by matja on 2008-02-28
I don't know which came first, but you'd think the other one could've made the name a bit more different! ;)

---

### Post by Ryozanpaku Tiger on 2008-02-29
**matja**, you are right! I need OpenMP, so thank you for your post. I guess I should install *libgomp*, not *openmpi-dev*, if the last one deals with OpenMPI.:)

---

### Post by bonzi on 2009-07-10
Is it still libgomp?? I cant find that package :(

---

### Post by TheStatsMan on 2009-07-10
openmp has been apart of gcc since version 4.2.4. Just add -fopenmp as a compiler flag

---

### Post by nash_p on 2011-09-20
thanx...
it was helpful

---

