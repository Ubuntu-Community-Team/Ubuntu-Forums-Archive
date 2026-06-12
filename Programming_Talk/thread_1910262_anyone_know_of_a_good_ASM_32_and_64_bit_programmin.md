---
title: "anyone know of a good ASM 32 and 64 bit programming lango book?"
date: 2012-01-16
forum: Programming Talk
---

### Post by hockey97 on 2012-01-16
Hi, I am looking for a good e-book that can teach me ASM 32 and 64 bit programming. Anyone know a great book?

---

### Post by imachavel on 2012-01-17
uh i don knaow

[http://docs.oracle.com/cd/E19455-01/806-3773/index.html](http://docs.oracle.com/cd/E19455-01/806-3773/index.html)

:guitar: maybe?

---

### Post by hockey97 on 2012-01-17
> **imachavel said:**
> uh i don knaow

[http://docs.oracle.com/cd/E19455-01/806-3773/index.html](http://docs.oracle.com/cd/E19455-01/806-3773/index.html)

:guitar: maybe?

that source is confusing and it's a manual.

I am looking for material that can help me learn ASM for the first time.

I actually do know some basics of it but still can't write a program on my own and fully understand it.

---

### Post by craigp84 on 2012-01-17
[http://www.amazon.co.uk/Programming-Ground-Up-Jonathan-Bartlett/dp/0975283847/ref=sr_1_1?ie=UTF8&qid=1326834245&sr=8-1](http://www.amazon.co.uk/Programming-Ground-Up-Jonathan-Bartlett/dp/0975283847/ref=sr_1_1?ie=UTF8&qid=1326834245&sr=8-1)

I found this book, Programming from the Ground Up v accessible, you can skim it really quickly. It only covers 32 bit.

I never read any other books before teaching myself x64 asm - i used knowledge from the above, output of gcc -S and referring to google a couple of times (e.g. first hurdle was i didn't recognise some of the register names being referred to (they began r...) e.g. %rsi. Turns out %r are 64 bit versions of the similarly named 32 bit registers.

e.g. if %al and %ah are the upper and lower bytes of the 16 bit %ax, and %eax is the 32 bit register, then %rax is the 64 bit.

Another thing is the ABI & calling convention changes with 64 bit, where in 32 bit there are various ABI / calling conventions (stdcall, fastcall, pascal) in 64 bit it's more or less the one game in town - system V amd64.

There are some other differences but i reckon these are the 2 would have been good to know for myself.

---

### Post by collisionystm on 2012-01-17
> **craigp84 said:**
> [http://www.amazon.co.uk/Programming-Ground-Up-Jonathan-Bartlett/dp/0975283847/ref=sr_1_1?ie=UTF8&qid=1326834245&sr=8-1](http://www.amazon.co.uk/Programming-Ground-Up-Jonathan-Bartlett/dp/0975283847/ref=sr_1_1?ie=UTF8&qid=1326834245&sr=8-1)

I found this book, Programming from the Ground Up v accessible, you can skim it really quickly. It only covers 32 bit.

I never read any other books before teaching myself x64 asm - i used knowledge from the above, output of gcc -S and referring to google a couple of times (e.g. first hurdle was i didn't recognise some of the register names being referred to (they began r...) e.g. %rsi. Turns out %r are 64 bit versions of the similarly named 32 bit registers.

e.g. if %al and %ah are the upper and lower bytes of the 16 bit %ax, and %eax is the 32 bit register, then %rax is the 64 bit.

Another thing is the ABI & calling convention changes with 64 bit, where in 32 bit there are various ABI / calling conventions (stdcall, fastcall, pascal) in 64 bit it's more or less the one game in town - system V amd64.

There are some other differences but i reckon these are the 2 would have been good to know for myself.

Download for free here

[http://download.savannah.gnu.org/releases/pgubook/](http://download.savannah.gnu.org/releases/pgubook/)

---

