---
title: "ls -ltr output in cron job"
date: 2008-08-02
forum: Programming Talk
---

### Post by nofrieka on 2008-08-02
hii all

I execute ls -ltr command in terminal and produce some output like this:
-rw-r--r-- 1 kaka kaka 2752152 **2008-08-02 21:03** C20080802.2100+0700-20080802.2115+0700

but if I execute this command via cron, the output is:
-rw-r--r-- 1 kaka kaka 2729901 **Aug  2 22:23** C20080802.2100+0700-20080802.2115+0700

What should I do, if I want to get cron job output for ls -ltr exactly same as I do it manually in terminal ??

Please help..
Sorry for my bad english..

---

### Post by Martin Witte on 2008-08-02
On my system with my profile I don't have this. Usually if cron jobs do something different than the same job des in a terminal it is due to the environment, as cron jobs are run withe the standard shell - sh, rather than the linux shell bash

---

### Post by nofrieka on 2008-08-02
thanks Martin..

I solved this problem by adding LC time in my cron..

LC_TIME="en_US.UTF-8"

---

