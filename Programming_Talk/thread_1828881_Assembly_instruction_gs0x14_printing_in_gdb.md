---
title: "Assembly instruction gs:0x14: printing in gdb?"
date: 2011-08-19
forum: Programming Talk
---

### Post by gnometorule on 2011-08-19
I'm working through understanding the canary value smash protection for Ubuntu, as a relative beginner to it, good C and some assembly knowledge. I usually find what I need googling, but have a hard time finding a source to explain what exactly in intel assembly the line

move eax, gs:0x14

does: it's clear you load into the accumulator, from the location referenced in gs:0x14, a random canary value. I also believe to remember segment registers were used to extend address space in formats such as

(16 bit address:16 bit address) -> 20 bit address.

(1) As $gs = 51d = 33h, would the result be 314h? 

(2) Any more color on that (or the correct) location?

(3) And how do i print a value such as 'gs:14' using gdb (both its address & value)? (not via letting the instruction execute, then check eax, but directly). I'm working with set disassembly-flavor intel.

Many thanks.

P.S.: This isn't about understanding the use of a canary value, how it's xored at frame end to prevent stack smashing. Really only about understanding the above syntax and how to handle it with gdb.

---

### Post by Bachstelze on 2011-08-19
> **gnometorule said:**
> 
(1) As $gs = 51d = 33h, would the result be 3314h? 


Nope. ;) That only works in real mode. In protected mode, if you try to access that address in gdb, it will tell you 'Cannot access memory", because the value of a segment register is not used directly to compute an address, but instead is the index of the segment descriptor in the GDT or LDT.

[http://en.wikipedia.org/wiki/X86_memory_segmentation](http://en.wikipedia.org/wiki/X86_memory_segmentation)

If you want to get the value, you would need to find the location of the GDT or LDT, and get the base address from there. There is no way that I know of to do that.

---

### Post by gnometorule on 2011-08-19
Ah. Thank you very much. But out of curiosity, could I print a similar construction (reg:hex) for another reg in gdb, and how?

---

### Post by Bachstelze on 2011-08-19
> **gnometorule said:**
> Ah. Thank you very much. But out of curiosity, could I print a similar construction (reg:hex) for another reg in gdb, and how?

Not that I know of. What would you expect such a construct to print?

---

### Post by gnometorule on 2011-08-20
I have no idea. :) So I take it as just a special little construct used in implementing canaries. Many thanks for clarifying.

---

### Post by Bachstelze on 2011-08-20
This is not just for canaries, the general construct is %*segment_register*:offset, but it works only in assembly code, not in gdb. The opcode for this move instruction is 0xA1, you can look it up in [the manual](http://www.intel.com/content/dam/doc/manual/64-ia-32-architectures-software-developer-vol-2a-2b-instruction-set-a-z-manual.pdf).

---

