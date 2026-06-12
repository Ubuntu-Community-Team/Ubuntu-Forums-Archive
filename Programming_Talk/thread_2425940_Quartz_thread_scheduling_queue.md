---
title: "Quartz thread scheduling queue"
date: 2019-09-02
forum: Programming Talk
---

### Post by Drenriza on 2019-09-02
Hi all!

I have a question i hope someone can help me with.

**The scenario**
If i have a recurring job that runs every 2 minutes and a method that the job runs as follows
```
public void runSomething (){execute... takes 1 minute}
```

At some point the runSomething method needs to handle an exception and it now takes 3 minutes to finish.
How will Quartz react?

Will it try to start a new thread on top of the one already running?
Or will Quartz say "**I started runSomething(), 2 minutes have now passed but the job is not done, do nothing, try and run the job again in two minutes**"

**The question**
If Quartz try to start a new thread on top of the one already running, how can i prevent this?

Thanks on advance
Best regards!

---

### Post by Drenriza on 2019-09-02
DisallowConcurrentExecution was the answer

```
@DisallowConcurrentExecution
public class JobOne implements Job() {
   ...
}
```

---

