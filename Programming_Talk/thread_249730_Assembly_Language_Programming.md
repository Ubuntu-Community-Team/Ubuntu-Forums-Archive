---
title: "Assembly Language Programming"
date: 2006-09-02
forum: Programming Talk
---

### Post by chris walters on 2006-09-02
Where do I look in the Ubuntu documentation or others to find out how to write, assembly and link assembly language programs targeted for my AMD or Intel based machines? I have done assembly language programming on much earlier hardware in the past. Also are there any commonly used debuggers? Capable of setting break points and etc. Thank you for your help. :)

---

### Post by commodore on 2006-09-03
I think assembly stuff is in the binutils package. It contains GAS (GNU assembler) which you can access with "as". Check "man as" for documentation I think. 
I don't program in assembly myself so sorry if I didn't give any useful information :D.

---

### Post by LordHunter317 on 2006-09-03
I would install and use nasm over gas and the reasons should be fairly obvious once you start to use it.  gas is really intended to assemble the output of GCC.

---

