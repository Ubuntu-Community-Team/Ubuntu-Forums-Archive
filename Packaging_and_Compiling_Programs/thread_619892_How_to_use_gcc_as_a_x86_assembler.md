---
title: "How to use gcc as a x86 assembler"
date: 2007-11-21
forum: Packaging and Compiling Programs
---

### Post by sshahir on 2007-11-21
Hi all,

I have developed the following simple assembly program for x86 and called it "Assem_Test1.s":

> .MODEL SMALL
.CODE

MOV AH,2
MOV DL,5A
INT 21
INT 20

I have tried the following there commands to generate the .obj file using C compiler as the X86 assembler:

[LIST]
[*]gcc Assem_Test1.s

[*]gcc -assembler Assem_Test1.s

[*]g++ -assembler-with-cpp Assem_Test1.s m_Test1.s
[/LIST]

however, I haven't been able to generate the .obj file; instead, the following  error messages are thrown:

> [COLOR="Red"]Assem_Test1.s:1: Error: unknown pseudo-op: `.model'
Assem_Test1.s:2: Error: unknown pseudo-op: `.code'
Assem_Test1.s:4: Error: too many memory references for `mov'
Assem_Test1.s:5: Error: too many memory references for `mov'
Assem_Test1.s:6: Error: suffix or operands invalid for `int'
Assem_Test1.s:7: Error: suffix or operands invalid for `int'
a[/COLOR]

I am wondering how I can use the C compiler (either gcc or g++) to generate .obj files. Please let me know if you have any comments or suggestions.

Regards,
sshahir

---

### Post by amingv on 2007-11-24
Hi,

I may be wrong, but I think you can't compile Assembly source with gcc (gcc as the C compiler, I mean), they are different and some keywords just won't fit (for instance, in your source you use int, but int in C serves as an **Int**eger declaration, and in assembler it stands for **Int**errupt, and transfers control of execution to another proccess). Maybe try this command:

To compile (or better said, assemble):

```
as Assem_Test1.s -o Assem_Test1.o
```

To link:

```
ld  Assem_Test1.o -o  Assem_Test1
```

Asuming everything goes right, that should give you an executable named  Assem_Test1.

---

### Post by NathanB on 2007-11-24
The example you are attempting to assemble is MASM code for 16-bit DOS.  The gcc back-end (g)as assembler expects a different syntax and also expects either 32- or 64-bit code.  You should study the material, tutorials, and examples available for Linux ASM programming:

[http://linuxassembly.org/](http://linuxassembly.org/)

[http://members.save-net.com/jko@save-net.com/asm/links.htm](http://members.save-net.com/jko@save-net.com/asm/links.htm)

---

