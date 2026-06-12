---
title: "Impossible g++ static library linking error (Bug?)"
date: 2018-07-14
forum: Programming Talk
---

### Post by babaliaris on 2018-07-14
See the makefile and the make output (below the makefile code)


[IMG]https://i.imgur.com/GTBu9oE.png[/IMG]

cannot find **[COLOR=#ff0000]-ltest[/COLOR]**

Please tell me how is this possible. Everything is in the same directory.

Thanks :p

---

### Post by babaliaris on 2018-07-14
rename test.a to libtest.a and use -test

---

### Post by TheFu on 2018-07-14
Should the library be named libtest.a?
If you don't want to name it that, then the -l argument needs to have the patch and full name.

---

