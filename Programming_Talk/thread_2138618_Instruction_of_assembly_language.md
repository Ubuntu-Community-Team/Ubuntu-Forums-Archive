---
title: "Instruction of assembly language"
date: 2013-04-24
forum: Programming Talk
---

### Post by hatsoff on 2013-04-24
What is the instruction to invert content of a register?

I'm using these two instructions to do a AND logical operation b/w two registers and store its result in 3rd seprate register:
have a look!

  [COLOR=black][FONT=TimesNewRoman]and ax, dx      ; AND operation b/w ax and dx register and storing its result in ax first then -> [/FONT][/COLOR]

  [COLOR=black][FONT=TimesNewRoman]mov bx, ax      ; storing result in bx

Cant it happen simultanously (Imean and operation and storing result in seprate register) in one instruction?
I'm using NASM assembler and AFD debugger.

Thanks
[/FONT][/COLOR]

---

### Post by MG&amp;TL on 2013-04-24
I'm not going to give an answer in code, (partially because I'm not comfortable with the dialect of assembly I know, let alone NASM) but if you XOR the bits with 1, it'll invert them. [http://en.wikipedia.org/wiki/Bitwise_operation#XOR](http://en.wikipedia.org/wiki/Bitwise_operation#XOR)

---

### Post by schragge on 2013-04-25
I'd be surprised if NASM didn't have the NOT instruction.
[highlight]Edit[/highlight] Sorry, I didn't read your question right. If you want to store the result of inversion elsewhere then **MG&TL** is right: just use XOR.

---

