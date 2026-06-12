---
title: "Stepping Debugger for ELF binaries"
date: 2007-09-02
forum: Programming Talk
---

### Post by Carl Hamlin on 2007-09-02
Does anyone know of a debugging utility for ELF binaries with a reasonably solid stepping function and decent support for register, stack and memory polling?

I've about had it with trying to twist gdb to my purposes.

---

### Post by peabody on 2007-09-02
I know of none that are free.  I believe there are commercial alternatives such as Borland Klyx (sp?).

Out of curiosity, what is gdb not providing?  Have you tried using it with a graphical frontend such as ddd?

---

### Post by Carl Hamlin on 2007-09-02
gdb seems like it's geared toward the high-level programmer. I'm writing ASM and need to know how each instruction is affecting every register.

gdb wants to talk to me about symbolic debugging. My code doesn't lend itself well to that.

Ugh. Migraine headache brewing.

---

### Post by peabody on 2007-09-02
Not sure if this helps, but here's a page describing how to use gdb with nasm.

[http://www.csee.umbc.edu/help/nasm/nasm.shtml](http://www.csee.umbc.edu/help/nasm/nasm.shtml)

---

### Post by the_unforgiven on 2007-09-02
You might want to try the [ddd]("http://en.wikipedia.org/wiki/Data_Display_Debugger") frontend to gdb - it allows you to display memory and regs in separate windows. IIRC, it also displays the affected memory locations/regs in a different colour.

gdb can automatically detect the level of language used to write the code - if debugging information/frames are included (i.e. compiled with -g option to gcc/g++/GNU as which includes the DWARF2 and/or COFF debugging frames); otherwise, it falls back to default ASM debugging just like any other debugger.

For more information, please refer to the man page of gdb.

HTH ;)

---

### Post by Carl Hamlin on 2007-09-02
Thanks, everyone. I've come to the conclusion I was having one of those 'stupid' days that immediately precede a migraine headache. During those periods, confusion reigns and simple things don't make any sense.

---

