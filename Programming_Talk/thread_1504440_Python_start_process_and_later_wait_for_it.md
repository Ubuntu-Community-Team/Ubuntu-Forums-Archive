---
title: "Python start process and later wait for it"
date: 2010-06-08
forum: Programming Talk
---

### Post by DBQ on 2010-06-08
Hi, I am trying to a program from python to run in the background and then do some computations in the parent, but at some point I want to wait for the child.  I tried using subprocess and os modules but no luck. Any ideas?

Thank You!

---

### Post by DanielWaterworth on 2010-06-08
This isn't really my area of expertise, but you could create a thread and run the child within it synchronously. Then join on the thread when you need to wait.

---

### Post by StephenF on 2010-06-08
The approach depends on whether you need both processes to talk to one another and whether you need both processes to be of the same or a different program. Have you considered the threading module?

---

