---
title: "how do i escape console mode?"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by jonabark on 2012-10-10
How do I gracefully exit console mode and return to the desktop?

---

### Post by jerrrys on 2012-10-10
Ctrl + Alt + F7

---

### Post by lisati on 2012-10-10
Try:
```
exit
```
or
```
logout
```

---

### Post by jonabark on 2012-10-10
Thanks for both answers I spose all 3 work.

---

### Post by DuckHook on 2012-10-11
lisati's answer was based on the assumption that you were referring to a graphical console running within the graphical environment. jerrrys' answer was based on the assumption that you had inadvertently switched from the graphical environment residing on<Ctrl> <Alt> <F7> to one of the pure command line consoles which Ubuntu uses as "spare" or extra shells and which reside from <Ctrl> <Alt> <F1> to <Ctrl> <Alt> <F6>. The two solutions address completely different problems and will not do the same thing.

---

### Post by lisati on 2012-10-11
> **DuckHook said:**
> lisati's answer was based on the assumption that you were referring to a graphical console running within the graphical environment. jerrrys' answer was based on the assumption that you had inadvertently switched from the graphical environment residing on<Ctrl> <Alt> <F7> to one of the pure command line consoles which Ubuntu uses as "spare" or extra shells and which reside from <Ctrl> <Alt> <F1> to <Ctrl> <Alt> <F6>. The two solutions address completely different problems and will not do the same thing.

Good call: sometimes the "correct" (or best) answer depends on context.

---

