---
title: "NASM (intel syntax) disassembler."
date: 2007-09-24
forum: Programming Talk
---

### Post by happysmileman on 2007-09-24
I've been learning ASM for a few days, and would like to know if there's anywhere I could get a disassembler that will output to the Intel syntax, for looking at small files I've written in C/C++ so i can understand how it gets compiled (I know I probably wouldn't be good enough to understand most of it, but that's what reference ooks are for)

Any would do, just list any you know and I'll look at each, googling didn't really find anything and everything seems to use GAS(AT&T) syntax.

Is there any option i could use to make GDB do this? As it would be immensely useful.

I'd love to use the Intel syntax as it seems so much clearer that AT&T (and since it uses same commands it doesn't seem to cause too much problems), but most tools on linux appear to assume GAS syntax

And yes I've tried NDISASM but it gives what appears to be COMPLETELY random ASM code, whereas OBJDUMP give the same code I entered, except in AT&T syntax

---

### Post by Wybiral on 2007-09-24
It's not hard to look at AT&T and see Intel... Just flip the parameters around and change the indexing system. I usually just use object dump when I need to check something (or a hex editor, but that requires some knowledge of the machine code and the elf executable format).

But you'll always get some junk code with disassemblers (at least all the ones I've used) because they often have trouble differentiating between data and code. Suppose you store an array of constant data at some point in the executable... Your code can jump around it, the assembler doesn't always know not to read that as machine code.

It's really up to you to be able to differ between them. But you should really learn the basics of assembly, then learn GAS syntax (you could learn GAS syntax first, but it really doesn't matter... It's all the same).

---

### Post by happysmileman on 2007-09-24
> **Wybiral said:**
> It's not hard to look at AT&T and see Intel... Just flip the parameters around and change the indexing system.

Yeha but it's slightly easier, or at least more familiar, and if I could get it without having to switch around it might stop me making stupid mistakes, I can understand the AT&T syntax, but don't see the point, it's the same code but Intel syntax seems to make more sence when you're reading it.

> Suppose you store an array of constant data at some point in the executable...


You could do that in the ".data" segment? Or am i missing something?

> 
It's really up to you to be able to differ between them. But you should really learn the basics of assembly, then learn GAS syntax (you could learn GAS syntax first, but it really doesn't matter... It's all the same).

Again, is there a real reason to learn GAS syntax, or is it just because it became a standard?

---

### Post by LaRoza on 2007-09-24
> **happysmileman said:**
> 
Again, is there a real reason to learn GAS syntax, or is it just because it became a standard?

"It is standard" is a reason to learn it in most cases.

---

### Post by Wybiral on 2007-09-24
> **happysmileman said:**
> 
You could do that in the ".data" segment? Or am i missing something?


Yeah, but I've noticed a lot of disassemblers aren't good at differing which section of the executable the non-code data is in.

> **happysmileman said:**
> 
Again, is there a real reason to learn GAS syntax, or is it just because it became a standard?

It's part of GCC... And GCC is pretty standard in Linux. If you want to work with compiler generated assembly in Linux, you should learn GAS.

I too prefer NASM because it's clean and more logical (IMO), but you can't really escape learning GAS if you really want to do some Linux assembly.

---

### Post by happysmileman on 2007-09-24
> **Wybiral said:**
> 
I too prefer NASM because it's clean and more logical (IMO), but you can't really escape learning GAS if you really want to do some Linux assembly.

Suppose, So i'll probably just look at AT&T syntax when debugging and put up with it, I suppose if I eventually ewant to do anything useful with it I could easily change anyway

---

### Post by LaRoza on 2007-09-25
> **happysmileman said:**
> Suppose, So i'll probably just look at AT&T syntax when debugging and put up with it, I suppose if I eventually ewant to do anything useful with it I could easily change anyway

In my wiki, under Assembly, there is an article on AT&T syntax for people familiar with Intel syntax. It isn't hard.

---

