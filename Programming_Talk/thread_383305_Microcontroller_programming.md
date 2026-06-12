---
title: "Microcontroller programming"
date: 2007-03-13
forum: Programming Talk
---

### Post by MiCovran on 2007-03-13
Has anyone programmed microcontrollers here?

I will need a microcontroller for a very simple purpose. Programming it should not be a problem because I already know C++ (C shouldn't be a problem then). My teacher uses BACSOM in Windows, but I would prefer working in Ubuntu with C.
So, what can I use to program Atmel AT89C2051, and where can I learn it?

Thanks.

---

### Post by louis_nichols on 2007-03-13
Programming microcontrollers is, as always, quite microcontroller specific.

A quick google with words like "atmel avr programming linux" will give you a ton of useful info. Also, there are several [packages in Ubuntu ]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=avr&searchon=all&subword=1&version=edgy&release=all")specifically for AVR.

---

### Post by MiCovran on 2007-03-14
Yes, I really found a ton of useful info, but this is not AVR, it's 8051 architecture. I haven't found anything practical with Google for 8051. I'm beginning to have a feeling that this difficult in Linux, since all the howtos are for AVR.

Has anyone here programmed these microcontrollers on Linux and is it possible? Just give me the software tools I need and that is enough to get me started.

---

### Post by Shay Stephens on 2007-03-14
Does this help?
[http://www.lecad.uni-lj.si/~leon/electronics/bi2051/index.html](http://www.lecad.uni-lj.si/~leon/electronics/bi2051/index.html)

---

### Post by MiCovran on 2007-03-14
Yes, but I still need a compiler and (possibly) a debugger. Thanks anyway.

---

### Post by DAharon on 2007-03-14
I am currently trying to get into microcontroller programming with the 8051 as well.  I got myself an Atmel 89S52 chip, and all the components necessary to build myself a small dev board like this one:  [http://www.kmitl.ac.th/~kswichit%20/89S52/89S52.htm](http://www.kmitl.ac.th/~kswichit%20/89S52/89S52.htm)

I haven't owned a computer with Windows on it in 4 years, and I'm not about to install it now just so I can program some microcontrollers.

I found this compiler:  [http://sdcc.sourceforge.net/](http://sdcc.sourceforge.net/)
And this programmer:  [http://www.8052.com/users/tomi/](http://www.8052.com/users/tomi/)

I have no idea if the prog89s52 program will work for your chip.  I would recommend you do as I did and download the source for prog89s52, along with the datasheet for the 89s52 ([www.atmel.com/dyn/resources/prod_documents/doc1919.pdf)](www.atmel.com/dyn/resources/prod_documents/doc1919.pdf)).  Supposedly, the 89s52 is very easy to program via ISP.  I sat here at my comp and went through the code, comparing it to the data sheet, and in the span of about two hours gained a good understanding of how the program works.  It's a very short program.

You say you are familiar with C++, and prog89s52  is written in C.  The only thing you may be unfamiliar with are C's bit fiddling operators, but all you'll have to do is look them up.

I'm gonna try and track down the datasheet for the processor you are using and take a look at the protocol it uses for ISP.  If it's anything like the one implemented by prog89s52, then it should be trivial to modify prog89s52, or even write another one from scratch.

EDIT:  Found the datasheet here:  [www.atmel.com/atmel/acrobat/doc0368.pdf](www.atmel.com/atmel/acrobat/doc0368.pdf)
It looks like this chip isn't programmed serially, but by entire bytes at a time.  Lets see whether this is possible through the parallel port...

---

### Post by MiCovran on 2007-03-15
I'll try it out. Thanks a lot.

---

### Post by DAharon on 2007-03-15
It looks like the parallel port only has 8 data pins.  I guess you could still program your chip serially, buy using one of those data pins to feed a shift register.  Then you could strobe the shift register and use the other data pins to control the chip during programming.  That seems like it would work.

---

