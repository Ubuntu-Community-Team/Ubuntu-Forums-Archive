---
title: "Can autotools build both 32 and 64 bit targets?"
date: 2009-09-17
forum: Programming Talk
---

### Post by emunson on 2009-09-17
I am working on converting a project from a hand rolled and fragile Makefile to autoconf and automake and I have run into a question to which I cannot find an answer.  On platforms that support it, I need to build both the 64 bit and 32 bit version of the library as well as our test suite.  can autotools handle detecting when this is possible and building both together (without build one, reconfiguring, and building the other)?

---

### Post by emunson on 2009-09-18
bump

---

### Post by emunson on 2009-09-20
anybody?

---

### Post by PandaGoat on 2009-09-20
I don't know how without researching into it, but since no one has replied I will at least answer your question.

Yes, autotools can.  When you run ./configure, you can tell it what target machine to build for.  However, you cannot build a 64 bit binary on a 32 bit machine.  So the answer is yes but with some restrictions.

---

### Post by emunson on 2009-09-21
Thanks for the reply, I have found that I need to include the AM_ENABLE_MULTILIB directive in my configure.in and write a config-ml.in script to setup the multilib dirs.  I cannot find a tutorial or anything that lays out what has to be in this script, and the only example google is turning up is gcc, which is far more complex than I need and not really useful as a starting point.  Do you know of any places that have a tutorial on writing a config-ml.in script or at least an example that is more simple than gcc?

---

