---
title: "Java: class Object, wat(), notify()"
date: 2009-03-09
forum: Programming Talk
---

### Post by andrew222 on 2009-03-09
Does anyone know why the thread operations methods wait() and notify are in the (superclass of all classes) class Object and not in class Thread?  Does it have to do with the lock on the object?

---

### Post by CptPicard on 2009-03-09
Yes. It's because each object instance has it's own "monitor", exclusive control of which can be obtained through the synchronized keyword. The monitor also has an associated wait queue in which threads can wait and/or notify others to wake up when desired conditions occur.

---

