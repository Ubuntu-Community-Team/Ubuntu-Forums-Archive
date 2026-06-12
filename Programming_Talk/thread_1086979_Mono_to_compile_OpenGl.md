---
title: "Mono to compile OpenGl"
date: 2009-03-04
forum: Programming Talk
---

### Post by Shady3D on 2009-03-04
hi all, can anyone tell me how can i add "-lglut" to mono while compiling, also can the CTRL+Space show a description beside the commands, functions or whatever it is.

---

### Post by directhex on 2009-03-04
-l is a C compiler flag. The Mono runtime itself won't gain much from GLUT, so why do you want to recompile it with linkage against that lib?

---

### Post by Shady3D on 2009-03-05
because it didn't work in the first place, but any way i figured it out.
i should add "glut" to the library under the debugging section in mono

---

