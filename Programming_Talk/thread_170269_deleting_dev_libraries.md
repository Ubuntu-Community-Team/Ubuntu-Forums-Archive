---
title: "deleting dev libraries"
date: 2006-05-04
forum: Programming Talk
---

### Post by flapane on 2006-05-04
Hi
after having compiled lot of times into these months (learning and using purpose), can I delete those tons of -dev libraries I see in apt manager? Do they are useful only while compiling, or I need them always?
p.s I thought to leave only the dev libraries for kernel compiling (ncurses etc etc)

---

### Post by simplyw00x on 2006-05-04
They're only the development headers; you can delete them after you've compiled that package.

---

### Post by flapane on 2006-05-04
great, thanks!
If I would leave only dev for kernel ricompile, what should I leave? libncurses-dev and?

---

### Post by asimon on 2006-05-05
[QUOTE=flapane]If I would leave only dev for kernel ricompile, what should I leave? libncurses-dev and?[/QUOTE]
Yes, libncurses-dev is enough for the cursed-based kernel config. That and build-essential should be enough.

---

### Post by flapane on 2006-05-05
thanks again

---

