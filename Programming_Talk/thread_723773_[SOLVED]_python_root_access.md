---
title: "[SOLVED] python root access"
date: 2008-03-13
forum: Programming Talk
---

### Post by bschleusner on 2008-03-13
How can I get my python programs to request root (gksu?) access when it is run? I would like it to be like what synaptic does..

Any help would be greatly appreciated.

---

### Post by mssever on 2008-03-13
Either you can modify the .desktop file to call gksudo yourprogram, or you can write a wrapper that calls your program with gksudo.

---

### Post by bschleusner on 2008-03-13
could the wrapper for calling gksudo be in the same source file as the rest of my program?

---

### Post by mssever on 2008-03-13
> **bschleusner said:**
> could the wrapper for calling gksudo be in the same source file as the rest of my program?

Probably. You could call your program recursively (especially if Python has an equivalent of Bash's exec; I don't know Python very well). But your code might be more readable if you use separate files. In fact, you might even write your wrapper in Bash, for example.

---

### Post by pmasiar on 2008-03-13
writing "gksudo python yourprogram" kind of bash wrappers seems to be the easiest :-)

---

### Post by themusicwave on 2008-03-13
I had a thread that did this recently...search for it...

My computer is testing a script and about to shut off so I can't go dig it up =)

---

