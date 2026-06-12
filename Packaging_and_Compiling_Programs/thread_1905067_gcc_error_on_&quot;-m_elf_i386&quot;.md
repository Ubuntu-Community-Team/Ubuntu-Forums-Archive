---
title: "gcc error on &quot;-m elf_i386&quot;"
date: 2012-01-05
forum: Packaging and Compiling Programs
---

### Post by bfoote on 2012-01-05
I'm trying to build simple kernel-mode hello example found everywhere using the ubuntu system makefile, which generates 
"-m elf_i386" (space between "-m" and "elf_i386") option in call to gcc.  But gcc does not recognize "-m" option.  Is gcc configured incorrectly?  I can't figure out how to eliminate this option from the make system.

---

