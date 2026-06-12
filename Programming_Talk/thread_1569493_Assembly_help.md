---
title: "Assembly help"
date: 2010-09-06
forum: Programming Talk
---

### Post by xefix on 2010-09-06
Hi, everyone

I'm very new to assembly and am trying to figure out what it means when I have a memory location followed by parentheses with multiple comma-separated arguments, kind of like this:

memorylocation(,%eax,2)

Additionally, if anyone knows any good assembly resources/tutorials, I would very much appreciate it if you could point me to them. Thanks!

---

### Post by Wybiral on 2010-09-07
In GAS assembly? It's address arithmetic.
If you've ever used NASM, think: [offset + eax * 2]

Here: [http://en.wikibooks.org/wiki/X86_Assembly/GAS_Syntax#Prefixes](http://en.wikibooks.org/wiki/X86_Assembly/GAS_Syntax#Prefixes) (read the "Address operand syntax" section)

EDIT:

As a side note, I despise having to edit GAS assembly. AT&T syntax is much cleaner looking and IMO easier to visually parse through. If you haven't used an AT&T syntax (such as NASM) I'd recommend starting there. It's easier to learn the quirks of GAS after you learn the basics of assembly in AT&T syntax.

---

### Post by nvteighen on 2010-09-07
> **Wybiral said:**
> 
EDIT:
As a side note, I despise having to edit GAS assembly. AT&T syntax is much cleaner looking and IMO easier to visually parse through. If you haven't used an AT&T syntax (such as NASM) I'd recommend starting there. It's easier to learn the quirks of GAS after you learn the basics of assembly in AT&T syntax.

Uh?

You got it inverted: GAS is AT&T and NASM is Intel :P But yes, NASM is more gentle for beginners.

---

### Post by foxmuldr on 2010-09-07
> **xefix said:**
> Hi, everyone

I'm very new to assembly and am trying to figure out what it means when I have a memory location followed by parentheses with multiple comma-separated arguments, kind of like this:

memorylocation(,%eax,2)

Additionally, if anyone knows any good assembly resources/tutorials, I would very much appreciate it if you could point me to them. Thanks!

Assembly is a low-level programming tool which allows direct writes to memory locations using things called registers.  Registers point to locations in memory, and when you use commands like mov (move), add, sub, dec (decrement), inc (increment), xor, and, et cetera, it will operate on those locations.

If you want to learn AT&T syntax, which is very awkward and clumsy, then there are tutorials for it online.  If you want to learn the more standard and easily read Intel syntax, then I would recommend finding the old Pentium II programming manuals, and beginning there.  They are available for download at various locations.

I have put them up on my website for download as well. Visit [www.TheTomatoReport.com](www.TheTomatoReport.com), and the audio tutorials there on assembly programming may be of help too:

[http://www.thetomatoreport.com/page_00000003.html](http://www.thetomatoreport.com/page_00000003.html)

If you have specific questions, please do not hesitate to ask me. I will be more than happy to help you through anything Intel-syntax related, or in general knowledge areas about assembly programming.

---

### Post by Bachstelze on 2010-09-07
> **foxmuldr said:**
> Registers point to locations in memory, and when you use commands like mov (move), add, sub, dec (decrement), inc (increment), xor, and, et cetera, it will operate on those locations.

Not necessarily. You can also operate on the values stored in the registers (as opposed to the memory areas those values point to).

---

### Post by Wybiral on 2010-09-07
> **nvteighen said:**
> Uh?

You got it inverted: GAS is AT&T and NASM is Intel :P But yes, NASM is more gentle for beginners.

Ha, I did get them mixed up. Mind you, I haven't touched an assembler in years :) The only time I ever touched GAS at all was while working with GCC output. But I did do my fair share of NASM/FASM code.

---

