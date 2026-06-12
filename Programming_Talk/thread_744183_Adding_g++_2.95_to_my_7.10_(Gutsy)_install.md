---
title: "Adding g++ 2.95 to my 7.10 (Gutsy) install"
date: 2008-04-03
forum: Programming Talk
---

### Post by negated on 2008-04-03
Hello,

Could anyone enlighten me on how to install (and subsequently run) g++ 2.95 on my 7.10 (Gutsy) x86 Ubuntu install? 

What I would like to do is have the current g++ installed (this was installed with the OS) as well as g++ 2.95 for times when I need to compile with it instead. 

Is this possible? Can they co-exist? Can install g++ 2.95 and then specify to compile using it instead of the current g++ when I need it, or will installing g++ 2.95 remove the current g++ as the default g++?

Thanks!

-S

---

### Post by WW on 2008-04-03
Install the package [g++-2.95](http://packages.ubuntu.com/gutsy/g++-2.95); it is in the universe repository.  The compiler command is g++-2.95.

---

