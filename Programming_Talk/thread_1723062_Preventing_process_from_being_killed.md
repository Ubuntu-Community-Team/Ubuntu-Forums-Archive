---
title: "Preventing process from being killed"
date: 2011-04-06
forum: Programming Talk
---

### Post by DBQ on 2011-04-06
Hi, I have ran an intensive program over night, just to find it killed in the morning.

I am aware that there is some mechanism which tries to kill processes to free up memory.  Is there a way to prevent a process from being killed?

---

### Post by r-senior on 2011-04-06
> **DBQ said:**
> I am aware that there is some mechanism which tries to kill processes to free up memory.
Could you elaborate?

If a process consumes so much memory that all the RAM and swap space is exhausted, something has to go, usually aforesaid process when it requests even more. But there is no mechanism that I know of in Linux that goes around seeking out and destroying processes that are just running for a long time and otherwise being perfectly reasonable.

---

