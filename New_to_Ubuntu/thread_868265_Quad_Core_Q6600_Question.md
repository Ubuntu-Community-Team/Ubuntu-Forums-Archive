---
title: "Quad Core Q6600 Question"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Amarsingh0793 on 2008-07-23
Hi. I am going to get a new computer with Intel Quad Core Q6600, 3GB RAM, 500GB Hard Disk and NVidia 8600 GS. I just want to know whether the Q6600 is a 32 bit or a 64 bit processor, so that I know which Ubuntu I should install :). 

Thanks in Advance :)!

---

### Post by InfinityCircuit on 2008-07-23
It is 64-bit so you can use either.  Are you aware that a C2D E8400 is faster than a C2Q Q6600 is almost every situation?

There is also no CPU frequency scaling driver for quad cores yet.

---

### Post by Amarsingh0793 on 2008-07-23
Thank You very much for your quick reply :)

!I am aware that the E8400 is faster, but as far as I know, that is Dual Core isn't it? The Quad Core happens to be more future proof. What is a CPU Frequency Scaling Driver?

Thanks again :)

---

### Post by ET! on 2008-07-24
using a cpu scaling driver you can reduce the clock frequency of cpu whenever it stays idle... cpu scaling is useful for saving power in laptop

---

### Post by ET! on 2008-07-24
iam personally using a quad core q6600..its an awesome value for money(cheapest quad core solution) and it seems to crunh anything you throw up to it....check out this link

[http://www.techreport.com/articles.x/14756](http://www.techreport.com/articles.x/14756)

---

### Post by Canis familiaris on 2008-07-24
All Intel Core based processors and newer Pentium 4 and Pentium Ds are 64bit processors capable of running both 32 and 64bit versions of OS.

BTW I would recommend Q9300.

---

### Post by ET! on 2008-07-24
> **Anurag_panda said:**
> All Intel Core based processors and newer Pentium 4 and Pentium Ds are 64bit processors capable of running both 32 and 64bit versions of OS.

BTW I would recommend Q9300.

some of the dual core proccesors(some of pentium d) are 32 bit!!! and pentium 4 processors from prescott and above are only 64 bit

---

### Post by eldragon on 2008-07-24
instead of spending your money on quadcores, have some developer fix xorg to be multithreaded :D

seriously. if the dualcore solution beats the crap out of a quadcore solution, why go for the latter?

you will take more advantage of the dual core than the quad core anyway.

since you are going to be running on a 64bit environment, i would suggest more ram and less cores. and maybe have a dualcore which will have more cache.. (Havent checked on those cpu specs...but i guess the Dcore has more cache per core).

---

### Post by Canis familiaris on 2008-07-24
> **ET! said:**
> some of the dual core proccesors(some of pentium d) are 32 bit!!! and pentium 4 processors from prescott and above are only 64 bit

I said "newer" Pentium 4 and Pentium Ds

---

### Post by Methuselah on 2008-07-24
I got the quad core too.
IMO, it's great value.
Twice the processors for nothing near double the price?
I couldn't say no.

Also, Linux tends to run many little programs all the time.
I think one benefits from four cores whether the individual programs are multi-threaded or not since the OS will have more CPUs on which to schedule concurrent processes to run.

Also, some applications benefit more from additional cores than slightly faster clock speed. 
A multi-threaded raytracer comes to mind. This was actually one reason I opted for the quad core.

However, single application benchmarks won't usually show the full picture unless they are programmed to use all cores.
Obviously, a program that runs sequentially on a single core will perform faster on a higher clocked Core2 than on a slower Quad.
However, if four such programs needed to be run, that Quad should be able to do it in about half the time of the Duo.

---

### Post by Vivaldi Gloria on 2008-07-24
> **eldragon said:**
> seriously. if the dualcore solution beats the crap out of a quadcore solution, why go for the latter?

Q6600 will beat any intel core 2 duo in any multithreaded application. For example, two programs I use frequently are these:

**dvd::rip** for dvd ripping (you need to setup clusters in the settings to get multi-cpu ripping)

**foobar2000** for sound conversion (it cannot multi-thread a single track but it can distribute different tracks among cpus. Use it with wine).

There are a lot of other multi-threaded apps there: Deep Shredder chess, john the ripper for pwd cracking (google for the multi cpu version) and so on. If you intend to use your computer as a server then a quadcore will destroy the core 2 duo.

Also I can do a lot of single threaded things at the same time with Q6600.

So which one is better: Quadcore or core2duo? It depends which apps you use and how you use them. Saying "dualcore beats the crap out of a quadcore" is misleading at best.

---

### Post by Vivaldi Gloria on 2008-07-24
To answer the op, you can use both 32bit and 64bit versions of ubuntu. I suggest you install the 64bit version of ubuntu unless you are going to install programs not available in the repositories. Programs not available in the repos may be 32bit only.

---

### Post by ET! on 2008-07-25
> **Anurag_panda said:**
> I said "newer" Pentium 4 and Pentium Ds

even some "newer" core2s are 32 bit(mobile processors)and you also have some core2solo processors which are 32 bit

---

### Post by Nepherte on 2008-07-25
Maybe you should have a look at the Q9300, or even better, the Q9450 as said above. The Q9xxx series is the next generation of quad cores. The price is acceptable.

---

