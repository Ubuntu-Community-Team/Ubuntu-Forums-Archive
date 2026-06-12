---
title: "segmentation fault"
date: 2010-07-17
forum: Programming Talk
---

### Post by Milenkonslisboa on 2010-07-17
I got this,do not know how to solve it.One friend mentioned me it could be that programs try to acsess memory not alocated to it.What should I do?

---

### Post by vikas.sood on 2010-07-17
> **Milenkonslisboa said:**
> I got this,do not know how to solve it.One friend mentioned me it could be that programs try to acsess memory not alocated to it.What should I do?

Programs can crash for many reasons. segmentation fault means your application tried to access memory which it is not allowed to. SIGSEGV is raised to such application which when cause access violation. 

What exactly are trying to do?? Is it that you working on some application and it crashes abruptly and you are unable to debug?

---

### Post by era86 on 2010-07-17
> **Milenkonslisboa said:**
> I got this,do not know how to solve it.One friend mentioned me it could be that programs try to acsess memory not alocated to it.What should I do?

Check your pointers.  We can only give descriptive answers with descriptive questions.  Help us help you!
:popcorn:

---

### Post by Milenkonslisboa on 2010-07-17
I have a fortran code,try to run executable.So I have to debugg it from scratsh probably.

---

### Post by Milenkonslisboa on 2010-07-18
Image              PC                Routine            Line        Source             
eik                0000000000408367  Unknown               Unknown  Unknown
eik                000000000040527C  Unknown               Unknown  Unknown
eik                000000000040311C  Unknown               Unknown  Unknown
libc.so.6          00007FEB154B45A6  Unknown               Unknown  Unknown
eik                0000000000403019  Unknown               Unknown  Unknown
Anyone knows what do these PC values tells me?

---

### Post by Zugzwang on 2010-07-18
Try to tell your compiler to include debugging information. The PC values on its own are useless. The debugger will then tell you in which function/method the problem happened.

---

### Post by nvteighen on 2010-07-18
> **Zugzwang said:**
> Try to tell your compiler to include debugging information. The PC values on its own are useless. The debugger will then tell you in which function/method the problem happened.

Doesn't gfortran -g do that?

---

### Post by Milenkonslisboa on 2010-07-18
Actually my compiler is Intel11.1 Linux,it also offers debugging option.

---

