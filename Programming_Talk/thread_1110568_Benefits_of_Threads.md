---
title: "Benefits of Threads"
date: 2009-03-29
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-03-29
I am wondering what benefit there would be for multiple threads (for one process) on a non-multiple core system. Is their a speed benefit, or is it just ideological and philosophical.


And using POSIX threads, how do you change the priority within C.

Also, do the multiple threads show on a system monitor, or are they bundled under the process?

---

### Post by slavik on 2009-03-30
1. easy way to use more than one CPU (not with all pthread implementations, see below). on a single CPU, you don't win much unless you want to separate your code out and you want to schedule threads on your own.

2. priority of threads? no idea, never done it.

3. depends: in Linux, ps will show them if you give it the -L flag, on solaris they won't as threads are userspace (part of the process).

---

### Post by Reiger on 2009-03-30
A process can schedule logically independent threads itself, without the OS having to load copies of the original code to accomplish the same.

---

### Post by sujoy on 2009-03-30
threads can also be usefull in certain cases where you have to wait for two things simultaneously. like user input and network activity for example

---

### Post by jespdj on 2009-03-30
One benefit of using threads, even on a single core / single CPU system, is with GUI applications.

Suppose you have an application with a GUI that performs some calculation or processing that takes time. You don't want to do it all in one thread, because that would mean the UI would be blocked while the program is calculating. So what you'd to is kick off a background thread to do the calculation when the user clicks for example a button to start the calculation. You could give the GUI thread a higher priority than the worker thread, so that the GUI stays responsive even when the calculation is running in the background.

---

### Post by dwhitney67 on 2009-03-30
> **slavik said:**
> 1. ... on a single CPU, you don't win much unless you want to separate your code out and you want to schedule threads on your own.
...

This is such a non-committal statement, that I do not know what to make of it.

Many single-core systems run multi-threaded applications, and for good reason.  When there is more than one task to be accomplished, and sometimes one task needs to be handled at a higher-priority than another.  Receiving data from an external system may have a higher priority, for instance, than the thread needed to process the data.

On a system that I am currently supporting, a separate thread is used to issue (via UDP) timing metrics for the processing loop of a main-thread, but at a much lower priority.  This is done with the hopes that the time-reporting task does not interfere too much with the main-thread.

Linux offers the ability to prioritize threads, however I have not spent much time looking into whether the default scheduling scheme (SCHED_OTHER) offers this.  The round-robin scheduler (SCHED_RR), however does offer this, but requires root-privileges for an application to employ this scheduler.

Anyhow, multi-threading has been around a lot longer than multi-core systems.

---

