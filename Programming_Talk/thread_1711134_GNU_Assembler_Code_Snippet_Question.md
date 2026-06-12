---
title: "GNU Assembler Code Snippet Question"
date: 2011-03-20
forum: Programming Talk
---

### Post by Banana Slug on 2011-03-20
Hello,  I'm new to the format of the GNU assembler.  Please see snippet below: The third entry of the IVT is the software interrupt vector.  It points to _software_interrupt vector.  What I'm not clear on is what the following statement does:

_software_interrupt:  .word software_interrupt

I'm assuming that it is assigning the label _software_interrupt with the value of the software_interrupt label which is where the actual ISR is located.    Couldn't this have been does as follows in the IVT without the interim step?

ldr pc, software_interrupt


Code snippet:

/** Interrupt vector Table (IVT) **/
.globl_start
_start:    b       reset
    ldr    pc, _undefined_instruction
    ldr    pc, _software_interrupt
    ldr    pc, _prefetch_abort
    ldr    pc, _data_abort
    ldr    pc, _not_used
    ldr    pc, _irq
    ldr    pc, _fiq
.
.
_software_interrupt:    .word software_interrupt
.
.
.align    5
software_interrupt:
    get_bad_stack
    bad_save_user_regs
    bl     do_software_interrupt

---

