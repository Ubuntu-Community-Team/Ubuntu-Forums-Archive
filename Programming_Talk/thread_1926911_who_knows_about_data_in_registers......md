---
title: "who knows about data in registers....."
date: 2012-02-17
forum: Programming Talk
---

### Post by topscore on 2012-02-17
who knows about mov command in gas assembler?
  when there is a value in register say ,%r10= 0x3c00000000 
  and    x=12 
  when you do the following command
            movq x, %r10 
 i've got in %r10 register the value-0x3c0000000012
  
how can it be?
   why x do not extend to register size 64 bits?

---

### Post by Zugzwang on 2012-02-17
Try to disassemble your program and check if it is really compiled the way it should be.

---

