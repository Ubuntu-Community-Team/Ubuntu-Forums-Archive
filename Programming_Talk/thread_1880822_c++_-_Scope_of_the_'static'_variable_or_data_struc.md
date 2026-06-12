---
title: "c++ - Scope of the 'static' variable or data structure in multithreaded environment"
date: 2011-11-14
forum: Programming Talk
---

### Post by akvino on 2011-11-14
If you declare 'static' variable it will be shared between the instances of the same class. 

What happens if the 'static' data structure is loaded as the part of the object from the shared object library(dll), and then different instance of the object is instantiated on a different thread? 
Is the answer the same if additional instance lives on a different process in a multicore environment?

---

### Post by karlson on 2011-11-14
> **akvino said:**
> If you declare 'static' variable it will be shared between the instances of the same class. 

What happens if the 'static' data structure is loaded as the part of the object from the shared object library(dll), and then different instance of the object is instantiated on a different thread?
Is the answer the same if additional instance lives on a different process in a multicore environment?

I think you seem to be confused about threads vs. processes.  The static variable has only one instance throughout the process execution.  Threads while they do have IDs like processes they are not processes they share in the process execution space, so between threads the static variable will be the same.  Between processes different.

---

### Post by akvino on 2011-11-14
> **karlson said:**
> I think you seem to be confused about threads vs. processes.  The static variable has only one instance throughout the process execution.  Threads while they do have IDs like processes they are not processes they share in the process execution space, so between threads the static variable will be the same.  Between processes different.

See I was not confused. I know that threads share same address space while processes do not. That is why I asked the second question, just to be sure. 

However Karlson, thanks very much for the answer.

---

### Post by karlson on 2011-11-14
Any time. :)

---

