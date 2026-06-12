---
title: "deadlock in producer-consumer problem"
date: 2013-03-17
forum: Programming Talk
---

### Post by 3v3rgr33n on 2013-03-17
Hi

I'm just wondering, is it possible to get deadlock in a properly done solution of the producer-consumer problem using semaphores?

I'm supposed to give an example of such and I can't see how that's possible as deadlock arises from circular dependecies (cannot happen in producer-consumer)

Regards,

A

---

### Post by spjackson on 2013-03-18
This sounds like homework. Doesn't the [Wikipedia page]("http://en.wikipedia.org/wiki/Producer-consumer_problem") help?

---

### Post by 3v3rgr33n on 2013-03-18
lol It was homework. I read that page numerous times. I then realized that I'm supposed to give a sloppy solution to the producer-consumer problem. I made one process try to acquire the lock twice and I did get deadlock. (note that the lock is not re-entrant).

---

