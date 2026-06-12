---
title: "gcc: Make -Werror only affect specific types of warnings"
date: 2008-03-07
forum: Programming Talk
---

### Post by flostre on 2008-03-07
Hi!

The gcc option -Werror turns *all* warnings into errors. Is there a way to only turn specific types of warnings (say, -Wreturn-type) to errors?

flostre

---

### Post by irrdev on 2008-03-07
No. I reviewed the gcc man page at [http://linux.die.net/man/1/gcc]("http://linux.die.net/man/1/gcc"), and the -Wreturn parameter has no other sub-parameters or arguments available. Your idea is good, however, and you might want to suggest it to the gcc developers on the [GCC developement mailing list]("http://gcc.gnu.org/ml/gcc/").

---

### Post by flostre on 2008-03-07
Oops, sorry, maybe I should have said that I already studied the GCC documentation on gcc.gnu.org ...

---

