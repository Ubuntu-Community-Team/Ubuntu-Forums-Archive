---
title: "Fork in a callback routine"
date: 2008-10-03
forum: Programming Talk
---

### Post by occhiverdi1987 on 2008-10-03
Hi,
I had to make an exercise in C. A process, the father, has to schedule many other processes, the sons. The exercise had to be a local environment model implementation with message exchange communication so NO shared memory structures could be used (except for the message queue of the kernel).The father made n fork (n variable) creating the sons which waited in queues and the same father left start one at a time each son until his end.
Everything was made with fork(), wait(), _exit().
My professor asked me to implement a graphical interface for this exercise using gtk+ library.
Now I have created a buttom which calls a callback routine.
This routine is the father of my program and makes the forks to create the sons. Each son has to add a line in a tree-view ,created in the main, but something is wrong because if I use wait() and exit() like in C ...no line is added...while if I don't use exit() 1 line is stamped (only 1 ...).
I think it is a problem of callback routine, maybe it is a thread and the problem is linked to the attempt to fork a thread...
What do you think? Can you help me?

---

