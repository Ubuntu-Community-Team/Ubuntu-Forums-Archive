---
title: "f77 not found - but not mentioned in the Makefile, and alias defined"
date: 2018-02-27
forum: Packaging and Compiling Programs
---

### Post by ChRaab on 2018-02-27
Hi everyone,

as far as I can tell the only thread about this issue was here: [https://ubuntuforums.org/showthread.php?t=2163353](https://ubuntuforums.org/showthread.php?t=2163353)
(which is closed by now).

I have a Makefile which originally had f77 in it. I replaced it with

FXX= gfortran
[...]
$(FXX)

but still running make resulted in it trying to use f77, which I don't have. So I set an alias, like so:
alias f77=gfortran

But the issue persisted. Eventually, it started working after I renamed the makefile, ran make -f on the renamed, named it back, and then changed FXX to FC.

Is there some subtlety of make or the shell that I'm missing?

---

