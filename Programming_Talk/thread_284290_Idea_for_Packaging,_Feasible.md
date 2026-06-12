---
title: "Idea for Packaging, Feasible?"
date: 2006-10-25
forum: Programming Talk
---

### Post by bmbommarito on 2006-10-25
I fancy myself a bit of a coder, C mostly, and some C++ if I have to.

What I wonder, is would it be feasible given the current state of Linux, to build a packaging system similar to OS X? Meaning, you have a folder that Gnome/KDE see as a program. In that folder is all the libs/executables needed for an application to run, and that can simply be downloaded and dropped wherever, and run.

I really like this style of packaging, it does away with lib hell since everything is included and would make it really simple for new users to get into Linux.

Possible? Needed? Lemme know.

---

### Post by po0f on 2006-10-25
bmbommarito,

When you compile your binary, just statically link it with the libs.  You will have a stand-alone, albeit much larger, binary.

---

