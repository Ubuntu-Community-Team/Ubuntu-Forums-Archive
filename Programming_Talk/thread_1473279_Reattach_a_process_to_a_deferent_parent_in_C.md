---
title: "Reattach a process to a deferent parent in C"
date: 2010-05-05
forum: Programming Talk
---

### Post by SIGTERMer on 2010-05-05
hi. Can anyone tell me how to attach a forked process to init so that the forked process doesn't get killed when the parent dies?

---

### Post by MadCow108 on 2010-05-05
setsid() should be what your looking for

---

### Post by juzzlin on 2010-05-05
If you have only one child process, then one simple trick is to treat the parent as the child and the child as the parent :) So just swap the roles.

---

### Post by SIGTERMer on 2010-05-05
madcow: Thank you. exactly what I needed :)

juzzlin: that's another way to skin a poor cat. thanks for bringing that up.

---

