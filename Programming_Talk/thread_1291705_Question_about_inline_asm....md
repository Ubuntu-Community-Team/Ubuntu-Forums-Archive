---
title: "Question about inline asm..."
date: 2009-10-15
forum: Programming Talk
---

### Post by kresyzig on 2009-10-15
Hi,

could someone explain me why the following does not work properly (it compiles but does not behave as expected) as an atomic "store" operation (I just want to store the value contained in val atomically in the memory pointed by ptr, without obviously modifying the value of the val variable):

#define q_store(ptr,val) __asm__ __volatile__ ("lock; xchg %1, %0" : "=m" (*ptr) : "q" (val), "m" (*ptr) : "1")

Thanks!

---

