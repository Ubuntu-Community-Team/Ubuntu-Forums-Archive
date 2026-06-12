---
title: "Python stopping and creating a new timer with the same variable name"
date: 2012-10-19
forum: Programming Talk
---

### Post by PatrickD-52761 on 2012-10-19
Hi everyone,

What I'm doing is creating a GUI that updates an IP Address on a given timeframe.  My question is if the interval changes, can I cancel the first timer, and reuse that variable to create a new instance of the timer?

Something like this:
```

sleep=60000*intUpdateInterval
t=threading.Timer(sleep, IPCheck)
t.start()

#If the interval changes, stop the timer, change sleep, and then start a new thread. This would be attached to an event on the text box.

t.cancel()
sleep = 60000*intUpdateInterval
t=threading.Timer(sleep, IPCheck)
t.start()

```

If this won't work, then how would I accomplish this task? I'm fairly new to Python programming, but I have done some programming in other languages.

Have a great day:)
Patrick.

---

### Post by spjackson on 2012-10-20
Yes, that will work. However, the units for the timer interval are seconds, not milliseconds. 60000*intUpdateInterval we be 16 hours 40 minutes if intUpdateInterval is 1.

---

### Post by PatrickD-52761 on 2012-10-20
> **spjackson said:**
> Yes, that will work. However, the units for the timer interval are seconds, not milliseconds. 60000*intUpdateInterval we be 16 hours 40 minutes if intUpdateInterval is 1.

Thank you for the reply. So, if I want a minimum of one hour, I'd use 60*intUpdateInterval then right? (the code would be set up so if the intUpdateInterval < 60, it will default to 60).

So something like this:

if intUpdateInterval < 60:
   sleep = 3600
else:
   sleep = 60 * intUpdateInterval

Have a great day:)
Patrick.

---

