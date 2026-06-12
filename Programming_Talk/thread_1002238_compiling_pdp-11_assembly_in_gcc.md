---
title: "compiling pdp-11 assembly in gcc"
date: 2008-12-04
forum: Programming Talk
---

### Post by glederfein on 2008-12-04
Hey all!
I understand there is a way of compiling pdp-11 assembly code in gcc. Can someone please give me the exact command in order to do this? Also, What file extension should the assembly code have?

Thanks in advance,
glederfein

---

### Post by wmcbrine on 2008-12-04
Do you have a PDP 11?

If not, you're looking for an emulator.

---

### Post by glederfein on 2008-12-04
I see.
What i basically want to do is turn the assembly file into an object file and then use an emulator to simulate it. I've heard simh can simulate the pdp11.
Can someone please give me simple instructions on how to do this?
I'm kind of new to this field...

Thanks

---

### Post by Cracauer on 2008-12-05
I never heard of a PDP-11 frontend for gcc and I'm too lazy to google.

In general, what are you going to do about the system and library calls? There aren't programs that don't use any OS and then you need those libs.

---

### Post by glederfein on 2008-12-05
> **Cracauer said:**
> I never heard of a PDP-11 frontend for gcc and I'm too lazy to google.

In general, what are you going to do about the system and library calls? There aren't programs that don't use any OS and then you need those libs.

Well, first of all, I found [this page]("http://books.google.com/books?id=wQ6r3UTivJgC&pg=PA462&lpg=PA462&dq=gcc+pdp-11+guide&source=bl&ots=EJUrRk4EFy&sig=x6xwmJuTpOjNormNswCHmv6Rg4o&hl=en&sa=X&oi=book_result&resnum=1&ct=result#PPA462,M1") in "The Definitive Guide to GCC".
Unfortunately, I don't yet know what system and library calls are. All I know is that I'm looking for a Linux alternative for the PDP-11 simulator given in [this site]("http://webcourse.cs.technion.ac.il/234118/Winter2008-2009/en/ho_Software%20(The%20PDP-11%20Simulator).html"). It receives the assembly code, translates it to PDP-11 machine code and then simulates the code given.

---

### Post by Cracauer on 2008-12-05
> **glederfein said:**
> Well, first of all, I found [this page]("http://books.google.com/books?id=wQ6r3UTivJgC&pg=PA462&lpg=PA462&dq=gcc+pdp-11+guide&source=bl&ots=EJUrRk4EFy&sig=x6xwmJuTpOjNormNswCHmv6Rg4o&hl=en&sa=X&oi=book_result&resnum=1&ct=result#PPA462,M1") in "The Definitive Guide to GCC".
Unfortunately, I don't yet know what system and library calls are. All I know is that I'm looking for a Linux alternative for the PDP-11 simulator given in [this site]("http://webcourse.cs.technion.ac.il/234118/Winter2008-2009/en/ho_Software%20(The%20PDP-11%20Simulator).html"). It receives the assembly code, translates it to PDP-11 machine code and then simulates the code given.

All right, so first of all a compiler doesn't give you the OS and the libraries. So even if it did compile PDP-11 assembler to any GCC backend such as x86 you still can't run it.

Second, you completely mistake what the above page is about. It is about a *backend*, not a frontend. You use it to compile C or other gcc-supported languages so that they can run on a PDP-11.

---

### Post by snova on 2008-12-05
> **glederfein said:**
> All I know is that I'm looking for a Linux alternative for the PDP-11 simulator given in [this site]("http://webcourse.cs.technion.ac.il/234118/Winter2008-2009/en/ho_Software%20(The%20PDP-11%20Simulator).html"). It receives the assembly code, translates it to PDP-11 machine code and then simulates the code given.

Why not just use that program? At least for now, it'd be easy just to run that program under Wine.

If I am interpreting your question correctly, you have PDP-11 assembly code you wish to run on Linux. GCC is the wrong way to go, it doesn't compile assembly code. You need an assembler. Specifically a PDP-11 assembler. And then you need an emulator to run it.

The above program appears to already do all of this...

---

### Post by mmix on 2008-12-06
There is pdp-10 online course, so it is not pdp-11, yet.

[http://pdp10.nocrew.org/](http://pdp10.nocrew.org/)

HTH

---

