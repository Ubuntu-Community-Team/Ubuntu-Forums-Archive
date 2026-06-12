---
title: "[C/C++ shared libs] References cause pointer relocations too?"
date: 2014-04-05
forum: Programming Talk
---

### Post by kangaba on 2014-04-05
Hi,
"How to write shared libraries" generally says a pointer (the * sign) will cause a relocation at runtime (load time? - whichever), but does a reference (the & sign) also cause a relocation?

---

### Post by ofnuts on 2014-04-05
Under the hood there is very little difference betwen references and pointers (all compiler implement references as pointers), so I would expect both to behave the same way in your case.

---

