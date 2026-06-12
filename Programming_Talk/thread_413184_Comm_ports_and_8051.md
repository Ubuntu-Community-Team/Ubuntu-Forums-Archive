---
title: "Comm ports and 8051"
date: 2007-04-18
forum: Programming Talk
---

### Post by johnnybgood115 on 2007-04-18
Is there a HyperTerminal for Linux to communicate with a Single Board 8051 computer through a COMM port? Also, is there any type of assembly language / 8051 assembler/compiler for Linux that can produce a .obj file to be downloaded to an 8051 single board computer?

---

### Post by amo-ej1 on 2007-04-19
Well concering the serial terminal the most frequently used application is the text based application 'minicom' but personally I prefer 'gtkterm' both can be found in the default ubuntu repositories.

On the 8051 part of your question, no clue but i'm interested in an answer ;-)

---

### Post by DAharon on 2007-04-19
Take a look at [SDCC]("http://sdcc.sourceforge.net/").  It can compile for a couple uC's.
Actually transfering the program to the uC is another matter.  It depends on which kind you have.  There is one [here]("http://http://www.8052.com/users/tomi/"), but it is specific to a single chip.  You could always just write your own using the specs in the datasheet for your chip.  Prog89s52 would be helpful there, because you can take a look at it's code and compare it to the 89s52 datasheet.  The 89s52 is very easy to program, so going through the source of prog89s52 shouldn't be too hard.  It took me about 2 hours to figure the whole program out.

---

