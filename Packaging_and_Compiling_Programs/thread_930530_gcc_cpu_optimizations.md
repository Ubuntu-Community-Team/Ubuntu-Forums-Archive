---
title: "gcc cpu optimizations"
date: 2008-09-26
forum: Packaging and Compiling Programs
---

### Post by Benjamin_Lebsanft on 2008-09-26
Hi there,

I'm compiling optimized dcraw builds to put on my blog, currenty I'm using the following switches:

[LIST]
[*]no opt
[*]standard: -O4
[*]P2: -O4 -march=pentium2
[*]P3: -O4 -march=pentium3 -ffast-math -malign-double -funroll-loops -fomit-frame-pointer
[*]P4: -O4 -march=pentium4 -ffast-math -malign-double -funroll-loops -fomit-frame-pointer
[*]AXP: -O4 -march=athlon-xp -ffast-math -malign-double -funroll-loops -fomit-frame-pointer
[*]A64: -O4 -march=k8 -ffast-math -malign-double -funroll-loops -fomit-frame-pointer
[/LIST]

Now I'd like to know if I can optimize this further and if someone knows the relevant switches for dual/quad core cpus and newer intel/amd ones?

Thanks
Benni

---

### Post by chris200x9 on 2008-09-26
I can't see anything further but why are you 04? gcc 4 only goes up to O3 anything over it just uses 3 anyway........ oh maybe -pipe

---

