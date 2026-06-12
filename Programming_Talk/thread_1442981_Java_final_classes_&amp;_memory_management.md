---
title: "Java: final classes &amp; memory management"
date: 2010-03-30
forum: Programming Talk
---

### Post by andrew222 on 2010-03-30
If we declare a Java class as final, would it effect Garbage collection or any other memory management issues?

---

### Post by CptPicard on 2010-03-30
No, not that I am aware of. Final is an inheritance related keyword, it has nothing to do with the actually allocated objects.

---

### Post by LKjell on 2010-03-30
**final** means that you cannot make subclasses of the class. The words you might want to look is **static**. Try search for singleton if you want only one class object to be created.

---

