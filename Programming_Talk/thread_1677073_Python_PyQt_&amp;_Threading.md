---
title: "Python: PyQt &amp; Threading"
date: 2011-01-28
forum: Programming Talk
---

### Post by Sailor5 on 2011-01-28
Greetings!

So after a button has been pushed the appropriate deferred gets executed. At the end of such I then need to execute another deferred as a separate thread so as to carry on with more jobs and still have the UI working.

```
T3 = Thread(target=Compile(self,info,info2))
T3.start()
```However after spawning the new thread the UI freezes. Only to come back once the thread has finished. I thought a new thread would run separately? So I would be able to keep performing tasks and have the user interface still working. However that doesn't seem to be the case.

Thanks bye!

---

### Post by lavinog on 2011-02-01
Can you post the full code?

---

### Post by Sailor5 on 2011-02-01
I linked this thread in IRC and got the fix. Need to pass arguments via arg=```
T3 = Thread(target=deferred,args=(self,arg1,arg2,))
T3.start()
```

---

