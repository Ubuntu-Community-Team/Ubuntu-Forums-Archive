---
title: "MAJOR python sqlite3 performance problem"
date: 2009-02-01
forum: Programming Talk
---

### Post by blake82 on 2009-02-01
Hi there,

I'm working on a data analysis project in python. I've stored all my data in a sql database, and am using python's sqlite3 module to move data to and from it.

My problem is that I have tens of thousands of small entries, and the sql file is something like 500MB, and growing fast, and any queries I do take FOREVER.

My bottleneck isn't disk access at all, its a 100% processing power issue, CPU0 is pegged. Which is odd because I have a pretty fast machine, leading me to think it may be a sqlite optimization issue??

What would you suggest I do to speed things along? Would it be better if I set up a proper sql server instead of using the python extension? I've got a few extra machines...

Anyway this is a hobby, and I really know next to nothing about sql, so any advice (no matter how obvious it seem to you) would be really appreciated.

Thanks!

Blake

---

### Post by Martin Witte on 2009-02-01
Have you investigated [this]("http://www.sqlite.org/cvstrac/wiki?p=PerformanceTuning") already?

---

