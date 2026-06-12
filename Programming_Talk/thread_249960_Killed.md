---
title: "Killed"
date: 2006-09-03
forum: Programming Talk
---

### Post by jessexoc on 2006-09-03
I'm running a program (written in C and compiled with gcc) that is very CPU and ram intensive. When i run the program (from the command line), after a few minutes it terminates and says killed. It runs ok when it is scaled back.
What does this mean? How do i get around it?

---

### Post by LordHunter317 on 2006-09-03
> **jessexoc said:**
> I'm running a program (written in C and compiled with gcc) that is very CPU and ram intensive. When i run the program (from the command line), after a few minutes it terminates and says killed. It runs ok when it is scaled back.
What does this mean? How do i get around it?It most likely means you tripped the kernel OOM (Out-Of-Memory) killer and it terminated your process because the system was out of memory.

---

