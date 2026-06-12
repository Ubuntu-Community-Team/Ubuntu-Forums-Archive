---
title: "Programming i-series processors on Ubuntu Linux"
date: 2012-09-15
forum: Programming Talk
---

### Post by resander on 2012-09-15
PCs nowadays often ship with Intel i3, i5 or i7 processors. These have two or more on-chip cores (autonomous processing units) and also support threads on-chip.

Is allocation of C/C++ threads to hardware cores/threads programmable?
If so how is the mapping done? Where can I read about it?

Ken

---

### Post by ofnuts on 2012-09-15
> **resander said:**
> PCs nowadays often ship with Intel i3, i5 or i7 processors. These have two or more on-chip cores (autonomous processing units) and also support threads on-chip.

Is allocation of C/C++ threads to hardware cores/threads programmable?
If so how is the mapping done? Where can I read about it?

KenOn the whole, the basic idea of threads is that they will run on any "core". There are cases where (mostly at the OS level) you want a thread to run on a specific core (so it can reuse data still in the cache from its previous time slice, for instance). This is called "[processor affinity]("http://en.wikipedia.org/wiki/Processor_affinity")" .

---

### Post by trent.josephsen on 2012-09-15
> **resander said:**
> Is allocation of C/C++ threads to hardware cores/threads programmable?

Short answer: No. At least, not in the sense you probably mean.
Long answer: Yes, everything is programmable if you go deep enough. (Insert your favorite Inception joke here.)

In general, the job of deciding what threads get run when and where (on a typical PC) falls to the kernel. There might be some cases where firmware gets involved. As an applications programmer, you probably don't know and almost certainly don't care; that's an implementation detail.

When you're writing software for standalone embedded systems, that's a different story and it's pretty much up to you, although I can't think of a convincing reason to run a particular thread on any particular core, since most of the time the cores are symmetric and none would offer any advantage over the others... but I'm getting out of my league and straying from the topic.

If you're specifically interested in systems programming and how the kernel allocates resources, you probably want to look into buying a book on OS development and another one on computer architecture. Maybe find one on multiprocessing too. You've asked a very broad question and you should expect to do a LOT of work if that's the answer you want.

---

### Post by resander on 2012-09-16
I agree that scheduling is best handled by the kernel certainly for single-cpu systems.

Occasionally it would be tempting to allocate processes/threads one-to-one to cores for predictability and performance, e.g. for video-conferencing, pattern recognition, searching huge documents etc. I now understand that the taskset command or sched_setaffinity call can be used for this. Thanks for letting me know.

---

