---
title: "gcc 3.4.1 using custom assembler instructions"
date: 2006-03-07
forum: Programming Talk
---

### Post by Mordred on 2006-03-07
Hi,

I'm running linux (not Ubuntu) on a Xilinx FPGA (ML403 board).
This board has a PowerPC processor.
I have a crosscompiler to compile my programs. It worked fine
for compiling my kernel but now I need to compile a program
that makes use of *special* assembler instructions.
By special I mean that they are not in the standard ppc instruction
set.

gcc complains about that:

#Error: unrecognized opcode: 'ldfcmx'

ldfcmx is the custom ppc instruction.

The processor knows how to handle that instruction. I just need to
make the compiler to ignore the fact that he doesn't know that
instruction.

Is there someone who can help me?
Pieter

---

### Post by toojays on 2006-03-07
I saw something like this a long time ago in some powerpc kernel code. IIRC you need to get asm to output the raw opcode, and not use the mnemonic at all. You may be able to write a macro to make this easier for yourself (this would be a combination of C-preprocessor macro and GNU assembler macro). I suggest asking your question on the GNU binutils mailing list, someone there will know what to do.

---

