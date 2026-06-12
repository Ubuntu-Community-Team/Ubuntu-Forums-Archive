---
title: "Can two threads read the same data?"
date: 2009-05-29
forum: Programming Talk
---

### Post by night_fox on 2009-05-29
Can two threads read the same data at the same time?

I believe an error occurring because of this might be quite unlikely given the proportion of time spent reading the memory, but do I need to protect against this happening?

Answers appreciated!

---

### Post by doas777 on 2009-05-29
ok, this is on the theory level, since i have no details about your implementation,
but yes, you can arrange "multiple read/single write semantics" if you try. the problem comes in when one of the threads attempts to lock the resource for write access. if that happens you will either need to fork the resource, or establish a blocking/synchronization routine (but beware deadlock conditions).

HTH

---

### Post by The Cog on 2009-05-29
This tutorial explains it quite well, and its principles probably apply to most languages:
[http://java.sun.com/docs/books/tutorial/essential/concurrency/interfere.html](http://java.sun.com/docs/books/tutorial/essential/concurrency/interfere.html)

In short - you absolutely MUST guard against interference between threads or your software will be unreliable and troublesome. Trust me - software somehow knows when the worst possible time to misbehave is.

---

### Post by night_fox on 2009-05-29
Thanks for the quick replies. So two threads probably can read the same data at the same time, but if I want to write to it with a third thread, then the reads might give non-deterministic (within each thread) results.

Would thank you electronically if it was working.

---

