---
title: "assembly - devices accessing"
date: 2010-09-06
forum: Programming Talk
---

### Post by aracky on 2010-09-06
hi all,
 
my question is if anyone can direct me to reading material about how to write directly to peripherals memory locations using gnu assembler.
 
i conducted numerous searches for books and even read 2 but still couldn't find a tutorial that teaches how to directly access hardware memory.

---

### Post by nebu on 2010-09-06
from my experience when you want to read something from a peripheral device... send the data over a serial/parallel line.... so you will have to copy the required register/s to the transmission register on the peripheral and then send it!

---

### Post by aracky on 2010-09-06
hi,
to tell you the truth' i'm new to assembly programming.

i want to know how to draw a pixel with direct access to the screen address, how to access the hardisk directly and go through its sectors, how to create sounds by sending data directly to the sound card etc.

can anyone help with some reference to an adequate tutorial/book?
thanks

---

### Post by worksofcraft on 2010-09-06
Sadly I don't think you can under Linux. Those parts of the computer are mapped into Kernel space and protected. A long time ago I used to write a lot of code that interfaces the hardware directly. I used Zortech/Borland/Watcom C++ mostly with some inline assembler, but you needed a dumb operating system like MSDOS that won't get in the way.

However I am also very interested in finding an answer because I have lots of cool libraries for controlling PC hardware. I would like to port it to GNU C++ and need a platform to run on, so I'm lurking on this thread...

p.s. I wonder if it would be worth developing an open source "dumb" operating environment specifically for developing embedded applications.

---

### Post by nebu on 2010-09-06
the framebuffer access is possible.... i used to play around with my old geforce fx card..... [http://en.wikipedia.org/wiki/ARB_(GPU_assembly_language](http://en.wikipedia.org/wiki/ARB_(GPU_assembly_language))

then later they moved onto a c like syntax for shaders.... which was much much easier to manage :P

as for the sound.... u need a little idea of digital signals and how analog waves are stored in pcm format and then send ur own pcm to the io port which is connected to ur sound card.... but like worksofcraft said... the kernel by default does not allow you access to io ports.... so u need to use the ioperm call to change the permissions on the port for the process


try this....
[http://books.google.ch/books?id=pbB8Z1ewwEgC&printsec=frontcover&hl=en#v=onepage&q&f=false](http://books.google.ch/books?id=pbB8Z1ewwEgC&printsec=frontcover&hl=en#v=onepage&q&f=false)

it is old but it can be useful to understand what is going on behind the scenes

@worksofcraft: if u want to port sound related stuff.... oss might be a nice place to start looking
and for gpu processing something like glsl might be a nice place to start

---

