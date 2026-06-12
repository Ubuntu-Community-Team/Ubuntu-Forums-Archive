---
title: "Assembler for Ubuntu? Know one?"
date: 2008-09-14
forum: Programming Talk
---

### Post by extruct on 2008-09-14
Hey people what's up?
Well we started to learn assembly in college and under WinXP we used Tasm from Borland. But since I'm trying to totally move to Linux I'm looking for assembler to Linux. As far as I know we use 286 assembly (or maybe also referred as 80286).
So any one know one?

Thanks :)

---

### Post by rnodal on 2008-09-14
[NASM]("http://nasm.sourceforge.net/"). I believe that there is a package for it so installing it should not be an issue. Take care,

-r

---

### Post by rplantz on 2008-09-14
> **extruct said:**
> Hey people what's up?
Well we started to learn assembly in college and under WinXP we used Tasm from Borland. But since I'm trying to totally move to Linux I'm looking for assembler to Linux. As far as I know we use 286 assembly (or maybe also referred as 80286).
So any one know one?

Thanks :)

You should ask your instructor. The syntax can differ between assemblers, especially assembler directives.
I see two potential problems:
1. If you are submitting your programs for grading, you certainly want your instructor to be able to run your programs. If he/she is using a different assembler, this may not work.
2. When the syntax differs between your assembler and the instructor's, you will have to learn both syntaxes and probably keep them straight in your head when taking exams.

I'm a retired CS professor. Grading sucks! Do whatever you can to help your professor grade your work. You want him/her to be in a good mood when reading your programs! :-)

---

### Post by tuffguy45 on 2008-09-14
Crap, I just noticed this topic after I made mine... I'll go close it now...

---

### Post by extruct on 2008-09-14
rnodal
Thanks seems like this one is what I need!

rplantz
Yea I know, as far as I know we use Intel syntax for 286.

tuffguy45
Happen sometimes :p

---

### Post by slavik on 2008-09-14
you can use nasm, which uses intel syntax (gas uses at&t syntax). keep in mind that calling system calls will be different (you need to call interrupt 80h instead on 21h and 10h or whatever they are in DOS). You also want to look up Assembly in Linux tutorials to know what to expect.

But before you do all of that, ask your professor if it would be fine.

---

### Post by rplantz on 2008-09-14
> **extruct said:**
> 
rplantz
Yea I know, as far as I know we use Intel syntax for 286.


You may not have learned about them yet, but its the directives that differ even though the instruction syntax is the same. For example, look at [http://rs1.szif.hu/~tomcat/win32/intro.txt](http://rs1.szif.hu/~tomcat/win32/intro.txt)

The directives guide the assembler in doing things like allocate memory for constants, set aside global data areas, etc. The instructions tell the CPU what to do when the program is executing.

Intel and AMD manuals suggest the instruction syntax but not a syntax for the directives.

I find it easier to move back and forth between Intel/AMD versus AT&T instruction syntax than moving between various assemblers' directives. There is many more differences in the directives.

---

### Post by cb951303 on 2008-09-14
[http://www.flatassembler.net/](http://www.flatassembler.net/)

cross-platform, it supports MMX, SSE, SSE2, SSE3 and 3DNow! extensions and x86-64 instructions,

---

