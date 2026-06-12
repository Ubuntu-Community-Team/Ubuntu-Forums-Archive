---
title: "does the x86 on AMD matter"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by creedless_egey on 2008-04-25
what if i have AMD and i put ubuntu x86 on it would that f... my laptop up or what?
plz if some 1 can explaine to me. that would be greate
what i understand is that x64 doesnt come with 32ibt is that right??only x86?
i dk 
thanks

---

### Post by Joeb454 on 2008-04-25
x86 is a 32 bit system

amd64 is a 64 bit system, it's just that AMD designed the processor architecture, and Intel adopted it later on :)

If you are unsure, go for the 32 bit (x86) install. :)

---

### Post by oloapota on 2008-04-25
x86 is a 32bit operating system
the other is a 64bit operating system

the choice is up to you
Until a few months ago choosing 64 bit would have implied some problems with some software, but that seems to be a thing of the past
If you have a pc with less than 1gb of ram, I would choose 32bit
64bit programs use more memory
If in doubt, go for 32bit

---

### Post by caravel on 2008-04-25
x86 = 32bit Architecture

x64 = 64bit Architecture

The amd64 kernel is for 64 bit and the i386 kernel is for 32 bit.

If you have a 64 bit CPU then you can download either the i386 iso image or the amd64 one.  If you have a 32 bit CPU then you're restricted to the i386 one.

Post up the specs of your system and someone will be able to help you.

---

### Post by creedless_egey on 2008-04-26
ooo ok thanks now i get it
also does it make any diff if i have x64 and im running x32 like performance wise or does it run slower or faster 
what i heard that that x32 using lower things(so it can rin on low performance pc)right and x64 uses higher things 
i just started this linux stuff lol so plz excuse me for asking a lot
thank you

---

### Post by amohanty on 2008-04-26
There are some fundamental differences and then there are offshoots:

1. x32 kernels can only support files and memory upto 4GB 2^32, so you cannot really use more than 4G RAM or larger than 4G file (there are ways to deal with >4G files - so this is not entirely true)

2. OS's typically use and restrict a certain amount of RAM (per process) which makes your 2G x32 laptop have less memory available fo individual processes which means more swapping can occur if you have an inordinate amount of processes running. The usage pattern does not apply to x64 machines.

3. Primitive data types occupy more space in 64 bit archs which means code compiled on a 64 bit OS will take up more memory than the same code compiled on a 32 bit OS

4. x64 will be faster at running programs but ymmv, depending on what applications you use, and whether or not it actually uses the fact that it is running on a 64 bit machine to do more in single ops.

There are lots more, but these are some of the main ones. Now if all you do is browse the web, see DVDs, listen to music, use OOo (plain old desktop use) you are not necessarily going to see any performance boost. Video editing on the other hand, will see a definite boost.

HTH
AM

---

### Post by creedless_egey on 2008-04-26
ok got thanx a lot

---

