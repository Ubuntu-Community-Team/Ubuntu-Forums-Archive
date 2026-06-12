---
title: "Anjuta C error"
date: 2008-04-16
forum: Programming Talk
---

### Post by Miles111 on 2008-04-16
When I try to compile a hello world program in anuuta, I get this error:
"No rule to make target 'c.o, needed by 'c'. Stop.'"

---

### Post by MeURi on 2008-04-16
Well, it's a long long time since I don't use Anjuta

For what I remember, it uses makefiles to compile and build your code, so maybe it's just a matter of a typo in the makefile. Or even a missing makefile :-P

---

### Post by Feelout on 2008-04-16
Try lauching ./configure script from Build menu.

---

### Post by Miles111 on 2008-04-17
When I launch the configure script it does it's work, and the error persists.

---

### Post by Daswebmastri on 2008-04-17
I'm in the same boat. Anjuta worked like a charm in Ubuntu 6.06, but since I've switched to 7.10, it is the only thing that doesn't work.

---

### Post by Zugzwang on 2008-04-18
> **Miles111 said:**
> When I launch the configure script it does it's work, and the error persists.

Please paste the output of ./configure here and see if a Makefile is generated. If this is the case, please paste it here as well.

---

