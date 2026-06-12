---
title: "assembly (nasm)"
date: 2009-08-03
forum: Programming Talk
---

### Post by niiize on 2009-08-03
Have started to get into assembler again after many years. This time in a new environment. Linux and not DOS.. Was never an advanced asm programmer but,.. it seems we use the count register (CX) for storing the offsets for strings in linux. Didn't we use to have another pointer for that, DS (data segment) in DOS. The CX register I recall was only used for loops and such numretic values. It confuses me abit.

---

### Post by lisati on 2009-08-03
linux is a 32-bit operating system: finding DS (data segment) used in a program for Linux is unlikely since the "segments" in a 32-bit program are usually organized differently to those in a 16-bit program. I'm surprised that you're finding CX being used, it's more likely to be ECX. And if they're using (E)CX as an offset, tut tut tut! I'd be confused too, and would expect (E)SI, (E)DI or (E)BX instead.

---

### Post by niiize on 2009-08-03
thnx for info.

---

