---
title: "GCC - Command line option order"
date: 2012-02-03
forum: Programming Talk
---

### Post by Krupski on 2012-02-03
Hi all,

Just ran into a problem and found a solution - I want to pass it along.

Using GCC 4.6 and compiling a small program using the sin (sine) function, I got this error:

> /tmp/ccvDrF3H.o: In function `addtone':
tick.c: (.text+0x1a3) : undefined reference to `sin'
collect2: ld returned 1 exit status


Now I know about the "-lm" option to link the math library and I was using it, so what was the problem?

Strangely, I found that if the "-lm" is placed at the END of the command line the code compiles perfectly.

That is, THIS:

[FONT="Lucida Console"][COLOR="DarkGreen"]/usr/bin/gcc -Wall -lm -o tick tick.c[/COLOR][/FONT]

...which USED to work now does not and has to be instead like THIS:

[FONT="Lucida Console"][COLOR="DarkGreen"]/usr/bin/gcc -Wall -o tick tick.c -lm[/COLOR][/FONT]

(note "-lm" at the end).

FWIW... hope this saves a few headaches.

-- Roger

---

