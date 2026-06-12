---
title: "GTK on windows without runtime?"
date: 2008-05-23
forum: Programming Talk
---

### Post by Peter Great on 2008-05-23
Is it possible to build GTK applications for Windows which only require some .dll files in the same directory but do not require the GTK runtime environment installed?

---

### Post by Peter Great on 2008-05-23
Kind of stupid question, I figured out myself. I just need to distribute the compiled .exe program with all the .DLLs in MinGW/bin and MinGW/lib. Put them in the same folder on the destination machine and it will run smoothly.

---

