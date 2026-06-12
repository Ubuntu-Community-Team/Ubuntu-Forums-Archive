---
title: "Checkpoint/restart of an application"
date: 2009-07-17
forum: Programming Talk
---

### Post by ee_guy on 2009-07-17
I'm designing an application that has to do a lot of data processing. I would like to be able to periodically create checkpoints and restart from the last saved checkpoint if the software crashes for some reason. I've been doing some research and found mention of a Linux checkpoint/restart capability. Is there some easy way to implement this functionality with some kernel api? If not, could I get some suggestions on a general method for doing this? Thanks.

---

### Post by dwhitney67 on 2009-07-17
There are various ways to do checkpointing.  The easiest I can think of is to write to a file, or if you wish, a memory mapped file.

When committing your data to the file (or memory or whatever), you need to also bear in mind that you also need to store your application's state.

Btw, there is no reason for your program to crash if you defend against it correctly.  In the past, when I worked on applications that relied on buggy third-party libraries, I had to capture SIGSEGV signals so that I could bring my application down gracefully, thus averting a loss of data (which I committed to a database).

---

### Post by MadCow108 on 2009-07-17
> **dwhitney67 said:**
> Btw, there is no reason for your program to crash if you defend against it correctly.  In the past, when I worked on applications that relied on buggy third-party libraries, I had to capture SIGSEGV signals so that I could bring my application down gracefully, thus averting a loss of data (which I committed to a database).

there is also the possibility of hardware failure which needs to be handled in a minimal data loss way.

---

### Post by Can+~ on 2009-07-17
I might be a little spoiled by the functional paradigm, but let's say you have:

```
Tasks:
 0 => Task0
 1 => Task1
 2 => Task2
 3 => Task3
 4 => Task4
```

(A structure that maps each task to a proper function, dictionary, array, whatever)

Then a function wraps it up, first stores the task list on a file, and each time that a task is complete, stores the latest id on said file. If a problem occurs, the tasklist reconstructs the flow of the program and the checkpoint states where is. (Same could be achieved with a stack stored on a file, and popping the task completed)

I think that must be how RDBMS's work; something like a [redo log]("http://en.wikipedia.org/wiki/Redo_log").

Btw, what language are you using?

---

