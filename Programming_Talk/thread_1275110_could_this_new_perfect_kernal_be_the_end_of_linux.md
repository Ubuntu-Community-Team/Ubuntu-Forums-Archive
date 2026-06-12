---
title: "could this new perfect kernal be the end of linux?"
date: 2009-09-25
forum: Programming Talk
---

### Post by adamogardner on 2009-09-25
I just read from this link:

[http://www.physorg.com/news173086905.html](http://www.physorg.com/news173086905.html) 

"Professor Gernot Heiser, the John Lions Chair in Computer Science in the School of Computer Science and Engineering and a senior principal researcher with NICTA, said for the first time a team had been able to prove with mathematical rigour that an operating-system kernel - the code at the heart of any computer or microprocessor - was 100 per cent bug-free and therefore immune to crashes and failures...."

We are curious about your opinions and thoughts on this.

---

### Post by doas777 on 2009-09-25
somthing tells me that the mathmatical correctness of this kernel will decline in direct proportion to the number of modules loaded and the number of devices supported.

theoretically it is most kewl, but until someone picks it up and makes a full system out of it, and an ecosystem starts to form, there is little likely hood that it will affect linux in the slightest. 

perhaps it will become the basis for a 3.x kernel someday. that would be kewl.

---

### Post by MadCow108 on 2009-09-25
proving the correctness of a computer program is an extremely difficult task even in pure functional programming languages like haskell and nearly impossible in languages with side effects (= nearly every non academic language in existence)
also stated in the article:
> 
Verifying the kernel - known as the seL4 microkernel - involved mathematically proving the correctness of about 7,500 lines of computer code in an project taking an average of six people more than five years.


7500 lines of code is a joke.
How big is the linux kernel? I guess a few million lines at least.

So this has not really much application in most real world application.
Their methods could be useful in very critical applications like of nuclear reactors or space shuttles but not very much more

---

### Post by Augustus Maxim on 2009-09-25
I wonder if user software can still crash it? The article doesn't go into too much detail as to what they tested it on/with. It also never mentions what platform or if it was portable.

I am more just thinking out loud, but it does sound interesting. I wish the article went into more detail.

As for it killing Linux, it would face the same challenges that Linux faces compared to MS Windows. No support, no killer applications (well, we do have some now:)), no multi-billion dollar advertising campaigns. Whats worse is that it would have the same David vs Goliath battle that we face, except with the Linux community, as Microsoft, being the self absorbed company that it is, would probably blow it off. 

In short, neat research, but won't be killing Linux anytime soon.

---

### Post by Reiger on 2009-09-25
The answer is no. Kernels are not for mathematical correctness (although having one that is will certainly be appreciated in environments that favour correctness over speed of development, e.g. mission critical code for managing equipment in aircraft etc.); kernels are for getting the doorstop to do anything much useful at all.

At the end of the day the kernel isn't the most interesting/appealing thing about your OS: the most interesting/exciting thing about your OS is how much neat stuff you can do with it. Hosting your own web server is more appealing to many than writing their own device driver, that kind of thing.

---

### Post by thk on 2009-09-25
On a related note, it turns out you can have a perfectly (100%) efficient engine if you run it infinitely slowly... :)

---

### Post by blur xc on 2009-09-25
From what I get out of that article, is that it's not intended for desktop pc's running office applications, rather dedicated computer controls for critical applications (like air craft, etc..).

A piece of equipment like that has one specific purpose, to do one simple, but extremely important job, where on failure could cause the loss of life and at least a few hundred million, or even billions of dollars of damage...

BM

---

### Post by Zugzwang on 2009-09-25
To shed some light onto the issue, I've had a look into the researcher's paper where they actually answer the questions you've imposed. It's here (currently the first paper in the list):

[http://ertos.nicta.com.au/publications/](http://ertos.nicta.com.au/publications/)

They describe that they have verified the functional correctness a micro-kernel (that means, unlike in Linux, device drivers are *not* part of the kernel). The kernel seems to have all the features (virtual memory management, threads, etc) you would expect from a kernel. "Correctness" is defined in terms of following some formal model of the behaviour of the kernel. The kernel runs on an ARMv6 processor and has been ported to x86, but this port has not been verified (no surprise, as there, for example, does not exist a formal model of the x86 instruction set). They also have to assume the correct functioning of the hardware, the correctness of the boot-loader and so on. The kernel is usable in the current state, but of course not Linux- or Windows-compatible, so mainly usable for embedded devices you build from scratch.

---

### Post by froggyswamp on 2009-09-25
There is no such thing as 100% proof. (Scientific) people like proving something and later explaining why that wasn't really a (scientific) proof.

---

### Post by MadCow108 on 2009-09-25
yes you can mathematically prove that a algorithm works under all circumstances
what they have done was not only prove that an algorithm works but a whole kernel
so it is a scientific proof, of course with certain assumptions but those are always present in mathematical proofs

but mathematics (and this is part of it) is the only scientific area where you can actually prove some general truth and not only a rule under a certain model

---

### Post by ve4cib on 2009-09-25
> **froggyswamp said:**
> There is no such thing as 100% proof. (Scientific) people like proving something and later explaining why that wasn't really a (scientific) proof.

But therein lies the difference between a scientific proof and a mathematical proof.  You can prove via mathematical induction with 100% certainty that there is an infinite number of prime numbers for example.  Mathematical proofs are inherently unscientific because they cannot be tested and validated experimentally; they are simply true or they are not.  They're true if the equations balance out, and they're false if the equations are wrong.  Simple as that.

Back on topic, I read about this a few weeks back.  From what I understand the microkernel is intended for use in avionics and similar single-purpose systems where errors or bugs could have disastrous consequences.  It's not intended for general-purpose computers.

Given another few years of research I wouldn't be surprised if we start seeing mathematical tests of more mainstream kernels though.  I think the techniques employed in the paper in question likely fall apart for larger kernels, so they'll need to be refined before they can be applied to any arbitrary OS kernel.  But the foundation work is there for now.

---

### Post by Can+~ on 2009-09-25
> **MadCow108 said:**
> 7500 lines of code is a joke.
How big is the linux kernel? I guess a few million lines at least.

2.6.30 was 11,590,971 lines of code and 27,911 files.

---

### Post by shadylookin on 2009-09-25
Mathematically proven and perfection are not the same thing. I'd rather have awesome features with the potential for bugs than wait around for them to be mathematically proven.

---

### Post by phrostbyte on 2009-09-25
Well this is a microkernel (meaning no drivers). Wouldn't a driver by it's inherent nature of interacting with character/block devices incur side effects and thus fail under inductive verification methods? 

AFIAK In order to prove the correctness of some function, that function must always return the same value when called with the same input. This is called a pure function. Unfortunately this is a constraint that is impossible to meet in a complete system with drivers and everything.

---

### Post by matthew.ball on 2009-09-25
Hey awesome, this comes from my school.

---

### Post by Krupski on 2009-09-25
> **adamogardner said:**
> I just read from this link:

[http://www.physorg.com/news173086905.html](http://www.physorg.com/news173086905.html) 

"Professor Gernot Heiser, the John Lions Chair in Computer Science in the School of Computer Science and Engineering and a senior principal researcher with NICTA, said for the first time a team had been able to prove with mathematical rigour that an operating-system kernel - the code at the heart of any computer or microprocessor - was 100 per cent bug-free and therefore immune to crashes and failures...."

We are curious about your opinions and thoughts on this.

A "bug free kernel" won't mean the death of anything. It will just leave more time to write cool apps...

---

### Post by uljanow on 2009-09-26
In the real world a kernel has millions lines of code. In this case only a small microkernel is proven to be correct which has little practical benefits. Consider drivers or services in userspace that need to be restarted because they crashed.

---

