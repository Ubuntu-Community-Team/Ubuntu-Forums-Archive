---
title: "Stop AT job scheduler emails"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by yanewby on 2008-05-16
I use AT to schedule a number of jobs.

When these jobs run they send an email stating the output of the job.

I would like to be able to stop these emails like you can when you use cron.  I know how to stop the emails with cron but how do I stop emails being sent using the AT command?

---

### Post by Het Irv on 2008-05-16
Marking for unanswered post team. 

I have no idea but this thread is kinda far back.  Or it was untill I just bumped it.

---

### Post by Oldsoldier2003 on 2008-05-16
apppending ```
>/dev/null 2>&1
``` to the end of your command will send the outputs to dev null

---

### Post by yanewby on 2008-05-16
> **Oldsoldier2003 said:**
> apppending ```
>/dev/null 2>&1
``` to the end of your command will send the outputs to dev null

I know this works for cron but it did not seem to work with at.

---

