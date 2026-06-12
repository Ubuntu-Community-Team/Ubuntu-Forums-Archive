---
title: "[ASSEMBLY LANGUAGE] Little-endian problem"
date: 2011-12-19
forum: Programming Talk
---

### Post by das86 on 2011-12-19
Hi everyone,
I have recently started learning on assembly language and i am using *Jeff Duntemann's* book *Assembly* Language Step By Step. There is one example in the book:

MOV AX,067FEH
MOV BX, AX
MOV CL, BH
MOV CH, BL

When I use insight to debug the program, I see that in eax the data shown is 67FEH, but if it is little endian, isnt it supposed to be FE67H?
From what I got, AH will keep FEH and AL will keep 67H.
                           BH - FEH and BL - 67H
Hence,               CH - 67H  and CL - FEH, thus CX will be FE67H. 
right?
But when I step until the 3rd instruction , ecx shows 67H when it is supposed to be showing FEH....:confused::confused:

---

### Post by trent.josephsen on 2011-12-19
Okay.  I can handle this one.  *crack knuckles*

I'm assuming x86?

Endianness doesn't affect how numbers are stored in registers like ax, bx, cx.  Even if it did, it would be transparent to you -- the assembler will do the right thing when you copy a 16-bit value into a 16-bit register.

Numbers in your assembly source code are assumed to be big-endian, to avoid screwing with your mind -- imagine every time you used a value larger than 255 you had to manually swap the high and low bytes just to write the code!  So when you write 'mov ax,67FEh' it puts 67h in the high byte of ax and FE in the low byte.  Similarly, 'mov cl,bh' takes the high byte of bx (still 67h) and puts it in the low byte of cx, so cx now contains 0067h.  You're seeing expected behavior; endianness doesn't come into play at all.

---

### Post by das86 on 2011-12-20
thanks for the reply!

---

### Post by Oliver Scantlebury on 2013-04-02
> **trent.josephsen said:**
> Okay.  I can handle this one.  *crack knuckles*

I'm assuming x86?

Endianness doesn't affect how numbers are stored in registers like ax, bx, cx.  Even if it did, it would be transparent to you -- the assembler will do the right thing when you copy a 16-bit value into a 16-bit register.

Numbers in your assembly source code are assumed to be big-endian, to avoid screwing with your mind -- imagine every time you used a value larger than 255 you had to manually swap the high and low bytes just to write the code!  So when you write 'mov ax,67FEh' it puts 67h in the high byte of ax and FE in the low byte.  Similarly, 'mov cl,bh' takes the high byte of bx (still 67h) and puts it in the low byte of cx, so cx now contains 0067h.  You're seeing expected behavior; endianness doesn't come into play at all.Actually, you're both wrong. ecx will NOT contain 67h. That's one byte; ecx is a 32-bit register. Also, cx will NOT contain 0067h. It will contain FE67h. In addition, the Assembler will NOT "do the right thing." It is the processor that will do the move at run time. The Assembler will only produce the machine code to tell the CPU do the work.

---

### Post by xb12x on 2013-04-03
Endianess problems are sometimes the result of looking at word data as bytes or byte data as words.

A word viewed in 16-bit word form looks like this: 67FEh

That same word viewd in 8-bit byte form looks like this: 0FEh 67h xx xx 

And so on for dwords and qwords, etc.

---

