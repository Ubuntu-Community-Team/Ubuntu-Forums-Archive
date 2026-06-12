---
title: "Tools for learning ARM assembly"
date: 2010-02-16
forum: Programming Talk
---

### Post by Judo on 2010-02-16
In the past, I decided to learn MIPS assembly on a whim thinking I could learn general CPU concepts and RISC.  I think I've thoroughly accomplished that goal.

Skip to today and I have an interest in ARM (ARMv7).  However, I'm not quite sure where to go from here.  I used SPIM while learning MIPS and loved it, but I can't seem to find anything like it for ARM.  Now I'm merely looking for anything that will allow me to test any ARM assembly I write.  Is there anything that could help me learn/run ARM assembly on my desktop?

---

### Post by Lux Perpetua on 2010-02-16
> **Judo said:**
> In the past, I decided to learn MIPS assembly on a whim thinking I could learn general CPU concepts and RISC.  I think I've thoroughly accomplished that goal.

Skip to today and I have an interest in ARM (ARMv7).  However, I'm not quite sure where to go from here.  I used SPIM while learning MIPS and loved it, but I can't seem to find anything like it for ARM.  Now I'm merely looking for anything that will allow me to test any ARM assembly I write.  Is there anything that could help me learn/run ARM assembly on my desktop?I think qemu can emulate an ARM processor with no problem. It's been a while since I used it, but IIRC it comes with an ARM assembler (to assemble your program) as well as the emulator itself (to run the resulting binary).

**[Edit]** Actually, I looked into it a bit more, and it seems you may have to get the assembler separately. Sorry, like I said, it's been a while. I don't know if there's an Ubuntu package for it, but I think you can get it here: [http://www.gnuarm.com/](http://www.gnuarm.com/)

You can also build a cross-assembler yourself by compiling the GNU binutils from source, making sure to configure for an ARM target. I've never done that, but it might be fun.

---

