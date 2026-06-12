---
title: "[C++] Queue and iterators, maybe I need a list?"
date: 2013-09-26
forum: Programming Talk
---

### Post by erotavlas on 2013-09-26
Hi,

I want to implement a FIFO memory so I need a queue. Sometimes I need to iterate over the FIFO to remove a subset of elements. The queue of STL does not allow to use iterators. So I think about a list or a set. I want that the elements in the memory are stored by maintaining the arrival order.
Do you have a better suggestions?
Thank

---

### Post by dwhitney67 on 2013-09-26
I think a set would be your best best, however if you plan to sort "complex" data, you will need to define your own compare function (perhaps using insertion time?).

As for insertions, I believe, they are quicker than using a list.  Also, using the upper/lower bound methods, you could easily jump to specific locations within the set that you want to manage (e.g. delete).

---

### Post by trent.josephsen on 2013-09-26
> **erotavlas said:**
> I want to implement a FIFO memory so I need a queue.
Ok. So far, so good.

> Sometimes I need to iterate over the FIFO to remove a subset of elements.
This requirement means it's no longer "just" a FIFO... What exactly does this mean? Usually queues are for tasks that need to be completed in a particular order. FIFO queues yield tasks in the order they came in, but there are other kinds of queue, like priority queues. When you remove elements, does that mean you process them immediately, or are they deleted and disregarded entirely, or do they get moved to a different queue, or something else?

---

### Post by dwhitney67 on 2013-09-28
> **trent.josephsen said:**
> 
This requirement means it's no longer "just" a FIFO... What exactly does this mean? Usually queues are for tasks that need to be completed in a particular order. FIFO queues yield tasks in the order they came in, but there are other kinds of queue, like priority queues. When you remove elements, does that mean you process them immediately, or are they deleted and disregarded entirely, or do they get moved to a different queue, or something else?

FIFO - first in, first out.

An analogy could be a queue of people at bank, waiting to see a teller.  If a person decides to leave the queue because the wait is too long, the other people in the queue still have to follow the FIFO rule.

Similarly, if an application can only process requests one at a time, it should be possible to cancel (delete) any particular request still waiting to be processed.  Again, the remaining requests will still follow the FIFO rule.

---

