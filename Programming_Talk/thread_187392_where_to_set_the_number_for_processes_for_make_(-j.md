---
title: "where to set the number for processes for make (-j) ?"
date: 2006-06-02
forum: Programming Talk
---

### Post by JoWilly on 2006-06-02
Hi,

Where can I set the env variables for the number of processes that make should start (-j)... in ubuntu. It should be something like make.conf, but I cant find it.

---

### Post by LordHunter317 on 2006-06-03
I'm confused.  Pass the argument to make via -j.  The argument tells make how many concurrent targets to run (not processes, there's no way to control that).

---

### Post by JoWilly on 2006-06-03
[QUOTE=LordHunter317]I'm confused.  Pass the argument to make via -j.  The argument tells make how many concurrent targets to run (not processes, there's no way to control that).[/QUOTE]

Yes sorry, arguments not processes.

So there is no way to set this globaly as an env variable so that it is always used, like in gentoo ?

---

