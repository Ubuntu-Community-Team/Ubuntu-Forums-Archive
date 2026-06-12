---
title: "Cursor positionning / GNU Assembler"
date: 2009-05-03
forum: Programming Talk
---

### Post by 1029384756 on 2009-05-03
Hi
i am using the gnu assembler and i wonder how i could set the cursor position.
if it is possible, i dont want to use any external libraries, the best solution would be an interrupt.
The only thing i want to do is moving the cursor to the upper-left corner (without tricks like writing 24 empty lines), because i want to get off the flickering that appears when redrawing the screen multiple times per second.

Any ideas?

thanks and best regards
max

---

### Post by NathanB on 2009-05-03
You will want to use syscall 54 - ioctrl

You can find the reference material here:

[http://linuxassembly.org](http://linuxassembly.org)

---

