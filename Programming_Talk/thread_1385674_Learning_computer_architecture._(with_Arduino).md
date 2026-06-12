---
title: "Learning computer architecture. (with Arduino?)"
date: 2010-01-19
forum: Programming Talk
---

### Post by tophor on 2010-01-19
I'm thinking about buying an Arduino, as I've always had an interest in micro controllers, and this is the most easily accessible one I've seen so far. No programmers, and the literature is very cool (MAKE supported) 

However, what I'm really interested in is learning computer architecture. I want to really get the primary bootloader and the secondary bootloader. To understand assembly at this level as well as possibly even understand programming at these low levels. Embedded Linux? Is this board even powerful enough to do this? MMU?

However, I don't know if the arduino would serve me. MMUless? microLinux? Anybody's ideas?

I've been reading this book:
[http://www.amazon.com/Embedded-Linux-Primer-Practical-Real-World/dp/0131679848/ref=sr_1_1?ie=UTF8&s=books&qid=1263954132&sr=8-1]("http://www.amazon.com/Embedded-Linux-Primer-Practical-Real-World/dp/0131679848/ref=sr_1_1?ie=UTF8&s=books&qid=1263954132&sr=8-1")

while helpful, its kinda high level, as well as harder to follow as some aspects of the linux kernel are dissected, and my C is rusty to begin with.

Any thoughts would be appreciated. Other platforms to buy besides Arduino. Other books? Websites?Blogs?

I know you have to start somewhere...but do I really have to start with blinking an LED with a customized C language?

I would like to get into the realm of embedded PowerPC, but it seems that these development boards are quite a bit more expensive.

---

### Post by Senesence on 2010-01-19
I too thought about getting an Arduino board, but ultimately, I think an FPGA board would be a better study platform, because not only will you be able to create your own software architecture, but you'll also have the ability to design and implement your own hardware designs (if you decide to take it that far).

A decent FPGA starter kit is a bit on the expensive side, when compared to the mid-range Arduino, but I think the flexibility is worth the additional $100 (actually, you can probably get a really good deal if you shop around).

As for running Linux on an Arduino: I don't know. I mean, I've heard people getting some variation of the kernel running on digital wristwatches, and other equally sparse devices, so I'm pretty sure it should be possible for any kind of micro-controller.

It would probably be easier to start with something like TinyOS first ([http://www.tinyos.net/]("http://www.tinyos.net/")).

In regards to programming: You should really try to clear up any confusion you may have about the C language, because that's about as low as you'll need to go (assuming you're not designing your own custom hardware....but even then, your first order of business will probably be to create the C compiler). A C compiler is virtually guaranteed to be available for almost any board you can find today. There are options to program in assembly, of course, but I think very few software people bother (compiler optimizes better, and all the dev tools are for C).

For overall OS concepts, well, you can just watch classes about it: [http://academicearth.org/courses/operating-systems-and-system-programming](http://academicearth.org/courses/operating-systems-and-system-programming)

Oh, but, as I said, you'll probably want to establish your C knowledge before doing anything else, so you might want to watch this first: [http://academicearth.org/courses/programming-paradigms](http://academicearth.org/courses/programming-paradigms)

Hope that helps.

---

### Post by tophor on 2010-01-24
Thankyou for the reply, Senesence, its greatly appreciated.

All input is helpful.

BTW: I'm finding Chapter Chapter 5 Kernel Initialization, very difficult to follow 

Embedded Linux Primer: A Practical Real-World Approach[http://www.amazon.com/Embedded-Linux-Primer-Practical-Real-World/dp/0131679848/ref=sr_1_1?ie=UTF8&s=books&qid=1264316062&sr=8-1]("http://www.amazon.com/Embedded-Linux-Primer-Practical-Real-World/dp/0131679848/ref=sr_1_1?ie=UTF8&s=books&qid=1264316062&sr=8-1")

---

