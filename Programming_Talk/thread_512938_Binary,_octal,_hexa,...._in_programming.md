---
title: "Binary, octal, hexa,.... in programming"
date: 2007-07-29
forum: Programming Talk
---

### Post by mocqueanh on 2007-07-29
Yeah, i've learned them when i'm a pupil. But now, my job (accoutant) doesnt concern to them, so i forgot.
I'm learning Python just for fun. But when i learn Python, i have to face them.
my ebook teach me about them, but not enough, it just show me how to convert decimal, octal, hexadecimal number to decimal number, not show me how to opposite.
Example: how to convert 253 to 1111 1101
And how to perform operator of binary, octal, hexa ?
0001 1101 + 0010 1011 ?
And the multiply, division , .......
can you teach me ?

P/S:  I hate it, the 100001111111ABEF,......... too jumble for me eyes, and for my brain. Is it important for programmer ?

---

### Post by AlexThomson_NZ on 2007-07-29
It's fairly important, well some bits (excuse the pun) are anyway.

I haven't had to touch octal math.  It's fairly important to know about binary, and the basic operator (espeically AND, OR, XOR, NAND).  Hex is important too, especially for color-values and byte values.

A summary of the most important bits to know (IMHO)
 * Binary operators (AND, OR, etc.)
 * Converting decimal & hex to binary & vise-versa
 * Recognising basic hex values (0x10 = 16, 0xFF = 255, etc.)

---

### Post by pmasiar on 2007-07-30
> **mocqueanh said:**
>  Is it important for programmer ?

It depends what kind of tasks you want to solve. It is pretty important to someone hacking kernel or drivers. It is pretty useless for say accountant just playing with Python for fun :-)

If task you want to solve (play with) requires it, learn it. If not, don't bother, don't waste your time. I did not used those hex constants for years: all of them have decent readable names, ready to be imported from some module provided by knowledgeable expert

---

### Post by Wybiral on 2007-07-30
Python... I highly doubt you will need to know much about binary (aside from boolean logic).

Assembly/C/C++... Probably at some point. Depends on the applications you're developing.

But, it's never a bad idea to learn about how things work, it's just that languages like python do their best to not make you use low level elements.

---

### Post by mocqueanh on 2007-07-30
I learn programming to code some app for my self, such as software for economy, accoutant, or some multimedia player (Music player), Python is the my first language, but i will learn details on them, can you show me how to convert decimal number to binary, hexadecimal number ? I just know converting binary to decimal

---

### Post by lisati on 2007-07-30
As others have pointed out, binary and hexadecimal are useful mainly for system-type stuff and logic, otherwise ordinary decimal will normally suffice. The only time I've come across a use for octal is in system-type stuff; with the x86 family of processors, however, hexadecimal is probably more useful. 

Again, as has previously been pointed out, choose the kind of problems you need to solve, and learn whatever is useful in that context, and don't sweat the other stuff. If you're getting into processing music data, hex might be of some value for interpreting the contents of the "tags" in the file.

---

### Post by pmasiar on 2007-07-30
You need to bookmark couple URLs:

Main doc page is: [http://docs.python.org/index.html](http://docs.python.org/index.html) (for current 2.5)
Library ref: [http://docs.python.org/lib/lib.html](http://docs.python.org/lib/lib.html)
Build-in functions: [http://docs.python.org/lib/built-in-funcs.html](http://docs.python.org/lib/built-in-funcs.html)
you can find there: 
hex(  	x):     Convert an integer number (of any size) to a hexadecimal string.  
oct(  	x):     Convert an integer number (of any size) to an octal string.

---

### Post by steve.horsley on 2007-07-30
Lots of good info here:

[http://www.google.co.uk/search?hl=en&q=hex+binary+tutorial](http://www.google.co.uk/search?hl=en&q=hex+binary+tutorial)

---

