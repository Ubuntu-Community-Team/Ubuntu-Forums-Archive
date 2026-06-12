---
title: "Assemblers for Ubuntu"
date: 2009-02-19
forum: Programming Talk
---

### Post by Jack Shankle on 2009-02-19
I am very disappointed with what I have seen so far with FASM.
Here is what I should be able to do with an Assembler with ease:

1. Have the ability to click on an Icon to assemble my program and create an executable module that I can pass on to a user. Or at least have a way to create an executable module.

2. I should not have to use segment registers to do far jumps. A flat assembler is the only sensible way.

3. Be able to put a text character anywhere on the screen.

4. Be able to change the size of a text character.

5. Be able to change the color of a text character.

6. Be able to draw a line. (not a series of pixels).

7. Be able to draw a circle. (not a series of pixels).

8. Be able to generate a bit map.

9. Would be nice to have GUI capability.

MASM32 does all this and more with ease but with the penalty of Windows.
I hate the thought of being stranded with Windows because of lacking
Assemblers in Linux.

Your thoughts would be appreciated.

---

### Post by Zugzwang on 2009-02-19
I guess you are mixing some things up.

> **Jack Shankle said:**
> 
1. Have the ability to click on an Icon to assemble my program and create an executable module that I can pass on to a user. Or at least have a way to create an executable module.

So you want to create an executable. Using MASM/TASM, I would first of all compile the program and then link the result. With NASM in Linux, I would do the same. I don't see a difference. How do you execute your programs if you don't have an executable?

> **Jack Shankle said:**
> 
2. I should not have to use segment registers to do far jumps. A flat assembler is the only sensible way.

This only depends on the machine and not on the assembler. Maybe you used MASM to program DOS real-mode programs? There, it is of course different. However, in protected mode (Linux, Windows 3.11+), there should be no difference between the assemblers.

> **Jack Shankle said:**
> 
3. Be able to put a text character anywhere on the screen.

4. Be able to change the size of a text character.

5. Be able to change the color of a text character.

6. Be able to draw a line. (not a series of pixels).

7. Be able to draw a circle. (not a series of pixels).

8. Be able to generate a bit map.

9. Would be nice to have GUI capability.

These functions have nothing to do with the assembler, but rather with what library functions you are accessing from your programs. There are libraries to do all this, you just have to interface them.

---

