---
title: "Shared Library Development question: Shared Memory"
date: 2012-01-23
forum: Programming Talk
---

### Post by Fubini on 2012-01-23
Hello all,

I've got a question for an advanced Linux dev! I'm writing a shared library for multi-threading in multiple processes within a single system.

I want all processes linking to my shared library to have access to a few global variables that will be shared and arbitrarily modified by other processes.

A simple use-case of this would be to maintain a count of all running processes that are currently linked against the shared library.

My current thought is that whenever a new process runs it will execute a method that looks something like:

```
volatile libraryStarted;
//Get library-global version of libraryStarted
//If no currently running process has linked against the library
//then it should be FALSE

if ( ! libraryStarted ){
    //Initialize shared data structures for library
    libraryStarted = TRUE;
} else { //Library has already been started
    //Get shared data
}
```

Of course, with the appropriate locks and whatnot. Each individual piece of shared data shouldn't need to be larger than a size_t, as it's no problem to write thread-safe data structures.

Any suggestions are greatly appreciated! I recognize there are a LOT of sticky issues to consider (e.g. thread crashing) but I'm just trying to get an idea of the mechanisms that could work here.

---

### Post by karlson on 2012-01-24
> **Fubini said:**
> 
Of course, with the appropriate locks and whatnot. Each individual piece of shared data shouldn't need to be larger than a size_t, as it's no problem to write thread-safe data structures.

Any suggestions are greatly appreciated! I recognize there are a LOT of sticky issues to consider (e.g. thread crashing) but I'm just trying to get an idea of the mechanisms that could work here.

You will probably need to look at the semaphores if you want to implement shared structures between processes but I would consider using a shared server that will keep track of your processes rather then a shared library because a process crash won't release anything in shared memory.

---

### Post by Fubini on 2012-01-24
I'm very familiar with parallel programming in general, but this is the first time I've tried to do multi-process programming. I suppose my approach is me just really wanting to treat multiple processes as multiple POSIX threads or something.

I thought about a server approach, but I'm not terribly familiar with that style of programming so it seems like you'd introduce a lot of overhead. At the very least, you need an extra thread hanging out in the background acting as a master instead of a nicely distributed solution.

The problem (for me, at least) is that the linker will automatically make a copy of the shared library's data section for every process that links against it. Normally this is what you want so that all variables can be thought of as local to each process that connects to the library... but for my specific case I want the exact opposite behavior- every process that links against the library gets the exact same set of variables (for a subset of the library's variables).

:(

---

### Post by karlson on 2012-01-25
> **Fubini said:**
> 
I thought about a server approach, but I'm not terribly familiar with that style of programming so it seems like you'd introduce a lot of overhead. At the very least, you need an extra thread hanging out in the background acting as a master instead of a nicely distributed solution.


What is a nicely distributed solution when it comes to a system with multiple processes?  When you are within a single process and memory space is shared among threads your synchronization while still complex is somewhat simpler.

> 
The problem (for me, at least) is that the linker will automatically make a copy of the shared library's data section for every process that links against it. Normally this is what you want so that all variables can be thought of as local to each process that connects to the library... but for my specific case I want the exact opposite behavior- every process that links against the library gets the exact same set of variables (for a subset of the library's variables).
:(

Ok.  Then think about this:  Each process will need to gather the state of the variable in the shared space.  One process when started in general will not know what other processes have or have not done so what you would do is initialize the variable to get it in a known state in a multi-process system it will mess up things if the variable have been updated from its initial state.  So normally only 1 process is allowed to update the shared space and others are simply reading from it.

Of course you can always have the processes identical to each other and just fork as many copies as you want and do things similarly to what apache does.

---

