---
title: "Debugging Assembly"
date: 2008-09-12
forum: Programming Talk
---

### Post by MacheteMurderer on 2008-09-12
I'm trying to debug some assembly code, i want to take a look at the registers during the program execution

C code implements assembler functions and checks it against c functions. 

When i use gbd/ddd its steps through all the c code perfectly but skips over the assembler functions( does not neter the function ) even though the disassembly-flavor is set to intel

At varisty the pcs there enter the assembler code and step though thme just like the c code... i don't know what i'm doing wrong

---

### Post by Lux Perpetua on 2008-09-13
How are you compiling/assembling your code?

```
gcc -g myprogram.s
```

---

### Post by MacheteMurderer on 2008-09-15
Thanks for the relpy

the code is compiled using a makefile, the exact commands are

$ nasm -f -elf tut3.asm -o tut3.o
$ gcc -g -Wall test3.c -o test3.o
$ ggc -g -Wall test3.o tut3.o -o test3

its translated from a very confusing makefile so i hope its right

But i don't think that has anything to do with my problem, actually i'm not sure if it even exists - its seems that its no poissble to step through your assembly code with any debuger like when you use gdb for c etc.

Firstly instead of using the next instruction you must use the stepi insruction, so on the step when the assembler function is called use stepi instead to step through the "micro instructions", which in assmebly are all in instructions :) Secondly if you are using ddd - if you use plain gdb, stop that and get the ddd front end -  open the registers on the status menu and watch the eip register - the offset in <> brackets tell you exactly where in your assembly code you are... now to the joy of debugging assembler

---

### Post by Lux Perpetua on 2008-09-15
> **MacheteMurderer said:**
> But i don't think that has anything to do with my problem, actually i'm not sure if it even exists - its seems that its no poissble to step through your assembly code with any debuger like when you use gdb for c etc.I don't know about nasm, but I've used gdb with gas before, and it works just like C code. 

I found this website; I don't know if it will help or if you've already tried it: [http://www.csee.umbc.edu/help/nasm/nasm.shtml](http://www.csee.umbc.edu/help/nasm/nasm.shtml) **Edit:** okay, it looks like it doesn't talk about stepping through a program. Sorry, I don't know. 

Good luck.

---

