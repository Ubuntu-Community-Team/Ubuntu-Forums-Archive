---
title: "PyQt: Closing GUI"
date: 2011-02-25
forum: Programming Talk
---

### Post by Sailor5 on 2011-02-25
Greetings!

So currently when the GUI is exited the process carries on. To fix this all that needs to be done is when the GUI has been told to close we raise SystemExit. But how could I do this? Could someone give thee an example?

Thanks bye!

---

### Post by Chameco on 2011-02-25
I don't have much experience, if at all, with QT, but if it's event based, you could connect a function like the following to the "quit" event, or something like it.
```

def onquit():
    *Insert whatever cleanup you need*
    sys.exit()

```

---

