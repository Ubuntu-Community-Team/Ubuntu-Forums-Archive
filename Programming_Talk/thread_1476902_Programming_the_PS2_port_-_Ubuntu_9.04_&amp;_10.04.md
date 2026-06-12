---
title: "Programming the PS/2 port - Ubuntu 9.04 &amp; 10.04"
date: 2010-05-08
forum: Programming Talk
---

### Post by grackleman on 2010-05-08
Hi
I have an application where I have to send an alphanumeric code out the PS/2 port so an Atmel AVR (plugged into he PS/2) can return an appropriate one as a keyboard input.

Does anyone have any info or links that would help? My programming experience is fairly limited.
Thanks

---

### Post by tookyourtime on 2010-05-08
Seeing as no one else has answered. I'm going to attempt.
Maybe...

You need to find the hardware address of your ps/2 port. 
[http://en.wikipedia.org/wiki/Input/Output_Base_Address](http://en.wikipedia.org/wiki/Input/Output_Base_Address)

If it even has one. Which it should though. Then in a similar way to writing to parallel ports and things...

From [http://www.epanorama.net/circuits/parallel_output.html#linuxprogramming](http://www.epanorama.net/circuits/parallel_output.html#linuxprogramming)
But change the address to what you want. And be careful. Obviously.
```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <asm/io.h>

#define base 0x378           /* printer port base address */
#define value 255            /* numeric value to send to printer port */

main(int argc, char **argv)
{
   if (ioperm(base,1,1))
    fprintf(stderr, "Couldn't get the port at %x\n", base), exit(1);

   outb(value, base);
}

```

All of what I just said may be wrong...

---

### Post by Zugzwang on 2010-05-08
Doing a google search found the following user-space keyboard driver for PS/2:

[http://www.informatik.uni-freiburg.de/~danlee/fun/psaux/](http://www.informatik.uni-freiburg.de/~danlee/fun/psaux/)

Perhaps you can modify it to do what you want?

---

### Post by radeon21 on 2010-05-08
What is sending data over the PS/2 port?  Is the AVR doing all of the output or is a PC?

---

### Post by grackleman on 2010-05-10
Thanks for all the replies.
The PC has to send information to the AVR which then responds by sending information to the PC (as keyboard input).

---

