---
title: "Checkpointing a console application"
date: 2007-11-20
forum: Programming Talk
---

### Post by GeneM on 2007-11-20
I have a long running console app that I want to stop from time to time and then resume from where I left off.  I have some global data that will not be any problem saving and restoring.  The problem is that this app relies on recursion a lot and I don't know how to save all that state.  The stack is something I have never directly accessed before.  Also the cpu registers would need to be saved.  Anyone know of any libraries that help with this or somewhere that has some detailed directions.  I spent a bunch of hours searching the web over the last couple of day and only found some academic research papers that were of not practical help.

Edit:  This is a C/C++ application.

Thanks,
Gene

---

### Post by colo on 2007-11-20
By "saving and restoring", I take it you mean to actually terminate the process your binary executeable spawned, and having another, new and indeptendent process take up the work where its predecessor left off later - right?

---

### Post by dwhitney67 on 2007-11-20
I'm sure where there's a will there's a way.  However, I generally always thought of checkpointing as an operation where an application stores only the volatile memory that is directly under it's control.  I would not even know how to begin copying the entire program stack, or even how to deduce at what level a program is in within a recursive loop.

Is there a way to make you application defer the termination request until it is done with a critical section of the code?  It would not be that difficult to receive the kill signal and set a binary semaphore that the main thread can examine.

---

### Post by NathanB on 2007-11-20
> **GeneM said:**
> I have a long running console app that I want to stop from time to time and then resume from where I left off.  I have some global data that will not be any problem saving and restoring.  The problem is that this app relies on recursion a lot and I don't know how to save all that state.  The stack is something I have never directly accessed before.  Also the cpu registers would need to be saved.  Anyone know of any libraries that help with this or somewhere that has some detailed directions.  I spent a bunch of hours searching the web over the last couple of day and only found some academic research papers that were of not practical help.

Edit:  This is a C/C++ application.

Thanks,
Gene

Hi Gene,

The number one rule in problem-solving is to remember the K.I.S.S. {Keep It Simple Smarty} principle.  All you need to do is have your application periodically check for the existence of a particular file... if that file is detected, do nothing... if it is not detected, continue normal operation.

Now, you can stop your application like so...
```

$ touch checkpoint

```
...and start it again like so...
```

$ rm checkpoint

```

---

### Post by dwhitney67 on 2007-11-20
> **NathanB said:**
> Hi Gene,

The number one rule in problem-solving is to remember the K.I.S.S. {Keep It Simple Smarty} principle.

I agree that this principle often forgotten by the newbie/inexperienced developers, however when it comes to checkpointing, there are times where "simple" is not the answer.  Checkpointing may have to be done periodically in case the application crashes due to some unexpected case, and recovery from a last-known stable point is desired.

I supported the development efforts on the software systems on a DOD satellite that had to perform checkpointing for the event that a system reset occurred due to either a software fault, or a space anomaly such as solar radiation burst, or even an EMP (from a nuclear explosion in the atmosphere).  The checkpointing was done periodically for the memory pool managed in volatile RAM and copied to non-volatile storage.  This task ensured that the satellite could be reconfigured to it's last known/sane state; of course, there was the possibility and it was acceptable that some data would be lost.

---

### Post by GeneM on 2007-11-21
> **colo said:**
> By "saving and restoring", I take it you mean to actually terminate the process your binary executeable spawned, and having another, new and indeptendent process take up the work where its predecessor left off later - right?

 Colo,

You are correct in your assumption.

Gene

---

### Post by GeneM on 2007-11-21
> **dwhitney67 said:**
> I'm sure where there's a will there's a way.  However, I generally always thought of checkpointing as an operation where an application stores only the volatile memory that is directly under it's control.  I would not even know how to begin copying the entire program stack, or even how to deduce at what level a program is in within a recursive loop.

Is there a way to make you application defer the termination request until it is done with a critical section of the code?  It would not be that difficult to receive the kill signal and set a binary semaphore that the main thread can examine.

dwhitney,

I am already using signals in the program.  Stopping the program is not the problem.  It is saving all the state that has accumulated in the recursive calls over weeks of time.  The only way to get all that state back without saving the stack is to rerun the program with the same data set and that would take exactly as long as the first time.  That is what I am trying to avoid.

Gene

---

### Post by GeneM on 2007-11-21
Nathan,

I am using signals in my program so that stopping it is no problem.  And I can pause it by using system monitor.  But if I reboot my machine while the program is running, stopped or paused I will loose all the state in the program and will have to start all over.  If I do that after the program has been running for several weeks or months I will have to run it that long again just to get back to where I was.  This means I loose all that time.

Gene

---

### Post by NathanB on 2007-11-21
Gene,

Rather than "re-invent the wheel", I suggest you review the source code from a few grid-computing projects {things like seti@home, prime search, etc.}.  These type of applications have a good track-record of being able to recover even when faced with power-outages.

Places to start looking:

[http://www.mersenne.org/](http://www.mersenne.org/)

[http://www.distributedcomputing.info/projects.html](http://www.distributedcomputing.info/projects.html)

---

### Post by CptPicard on 2007-11-21
It sounds like you should refactor your program to use an explicit stack on a block of RAM you just simply copy out periodically. Much nicer than reading your implicit call stack. :)

---

