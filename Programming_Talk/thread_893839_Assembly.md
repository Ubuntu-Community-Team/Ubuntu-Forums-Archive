---
title: "Assembly"
date: 2008-08-18
forum: Programming Talk
---

### Post by Jeremywilms on 2008-08-18
Can anyone redirect me to some good books for programming assembly in linux, I can't find many with good ratings, let alone one for linux. Anyway, I'm looking for a good beginners book, thank you.

---

### Post by jimi_hendrix on 2008-08-18
i believe assembler is 100% portable so you can run it on your microwave OS...just curious what are you making when you learn it?

---

### Post by Titan8990 on 2008-08-18
I was under the impression that assembly had different variants depending on the type of hardware. I believe the most popular is ASM.

---

### Post by Jeremywilms on 2008-08-18
I just want to learn more about computers, I always found programming fun. Anyway, I must of forgot to mention I'm using an AMD processor if that matters. Thanks, do you have any books you'd like to recommend?

BTW : ASM is the short term for assembly, or from what I understand it is. There are different ways of programming assembly depending on the processor your computer uses. As assembly is basically translated Machine Code.

---

### Post by rianjs on 2008-08-18
> **Jeremywilms said:**
> I just want to learn more about computers, I always found programming fun. Anyway, I must of forgot to mention I'm using an AMD processor if that matters. Thanks, do you have any books you'd like to recommend?

BTW : ASM is the short term for assembly, or from what I understand it is. There are different ways of programming assembly depending on the processor your computer uses. As assembly is basically translated Machine Code. There's all kinds of assembly. If you're looking to learn it, you're better off doing non-x86 assembly in an emulator, rather than trying to do x86 right on the metal. At least at first.

Something like MIPS would be a better starting place. It's nicer than x86.

---

### Post by mike_g on 2008-08-18
Theres a thread with some asm tutorial links [here](http://dbfinteractive.com/forum/index.php?topic=83.0) that I was planning to go over one day; at least to play around with the MMX/3dnow registers; dont know if I'll ever get around to it, but you may find something in there useful. Its not specifically for linux tho.

---

### Post by jinksys on 2008-08-18
> **Jeremywilms said:**
> Can anyone redirect me to some good books for programming assembly in linux, I can't find many with good ratings, let alone one for linux. Anyway, I'm looking for a good beginners book, thank you.

There are two major syntaxes out there, At&t syntax that GNU uses, and Intel syntax that NASM and Microsoft assemblers use.  I recommend learning both, once you learn one the other will be no trouble to pick up.  I'd start by reading this free ebook : [http://www.drpaulcarter.com/pcasm/](http://www.drpaulcarter.com/pcasm/)

I also recommend [Professional Assembly](http://www.amazon.com/Professional-Assembly-Language-Programmer/dp/0764579010)

The book assumes you are using linux and uses At&t syntax.

You'll be able to do all the examples in either book in a plain terminal window, so there's no need for an emulator.  You aren't going to hurt anything without root access by talking to the "bare metal".

My best advice would be not to listen to any of the posts before me, that is unless you enjoy misinformation.
Edit: ( except mike_g)

Good Luck!

---

### Post by loganwm on 2008-08-18
And Also I believe the sticky that LaRoza touts has some links to ASM related pages.

I'm not entirely sure, but if there are I'm sure that they're decent, the sticky hasn't failed me yet :)

Good luck mate!

---

