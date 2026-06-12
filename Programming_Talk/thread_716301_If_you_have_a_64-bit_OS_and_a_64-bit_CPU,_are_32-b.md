---
title: "If you have a 64-bit OS and a 64-bit CPU, are 32-bit operation still faster?"
date: 2008-03-05
forum: Programming Talk
---

### Post by Envergure on 2008-03-05
If you have a 64-bit OS and a 64-bit CPU, are 32-bit operation still faster?  What if you have a 64-bit CPU but only a 32-bit OS?

---

### Post by kool_kat_os on 2008-03-05
> **Envergure said:**
> If you have a 64-bit OS and a 64-bit CPU, are 32-bit operation still faster?  What if you have a 64-bit CPU but only a 32-bit OS?

i hear that 32bit apps are slower?

EDIT: to answer your question...i dont think so

---

### Post by jespdj on 2008-03-06
> **Envergure said:**
> If you have a 64-bit OS and a 64-bit CPU, are 32-bit operation still faster?  What if you have a 64-bit CPU but only a 32-bit OS?
Your question is a little vague.

For some technical details: See [this page](http://en.wikipedia.org/wiki/X86-64) to learn about the details of 64-bit mode on x86 processors. In 64-bit mode, you get more performance, mainly because the processor has more internal registers available, so it does not need to get data from memory (which is relatively slow) as often as in 32-bit mode. Also, the [calling convention](http://en.wikipedia.org/wiki/Calling_convention) for calling subroutines is different in 64-bit mode than in 32-bit mode: in 64-bit mode, arguments are passed via registers, while in 32-bit mode, arguments are passed via the stack (which is slower). So subroutine calls are also faster in 64-bit mode.

Conclusion: 64-bit software running on a 64-bit processor is faster than 32-bit software running on a 64-bit processor.

---

### Post by naugiedoggie on 2008-03-06
> **Envergure said:**
> If you have a 64-bit OS and a 64-bit CPU, are 32-bit operation still faster?  What if you have a 64-bit CPU but only a 32-bit OS?

What I have been told is that there is an interoperability layer required  in the OS to run 32-bit apps in a 64-bit environment and having to interact with this layer has a negative impact on operational speed.  However, since the 64-bit hardware and environment is itself faster than 32-bit environments, you do get some net speed of operations gain.  64-bit software is quite a bit faster, provided you have plenty of RAM available.

Thanks.

mp

---

### Post by jpkotta on 2008-03-07
> **naugiedoggie said:**
> What I have been told is that there is an interoperability layer required  in the OS to run 32-bit apps in a 64-bit environment and having to interact with this layer has a negative impact on operational speed.  However, since the 64-bit hardware and environment is itself faster than 32-bit environments, you do get some net speed of operations gain.  64-bit software is quite a bit faster, provided you have plenty of RAM available.

Thanks.

mp

I assume you're refering to ia32-libs and similar packages.  It's not so much an interoperability layer, it's more like a minimal 32-bit system within a 64-bit system.  x86-64 processors have all the 32-bit instructions that x86-32 processors have, so there's nothing like emulation going on.  The need for ia32-libs is simply because 32-bit binaries don't know how to deal with 64-bit libraries.  ia32-libs implement the same functionality as their 64-bit counterparts, the only difference is the interface is recognized by 32-bit programs.

The only slowdowns I've heard of with 64-bit systems is due to the fact that the pointers are bigger.  I read somewhere that gcc is about the same speed as on 32-bit, because it apparently uses pointers quite a lot and any speed gains from 64-bit were offset by having to move more data, keep fewer things in cache, etc.

---

### Post by CptPicard on 2008-03-07
I often get the impression that people take a very trivialistic view of what it means to have 64 vs. 32 bits in your CPU's registers. It's not as simple as many seem to imagine -- it's just a register/address length after all. 64bit architectures are also just simply newer than 32bit ones, so there is speedup because of that.

Having 64 bits per register will (roughly) let you 

1) address more memory
2) lets you have twice as many 32bit registers, should you choose to go down this route (you could just as well have more registers on a 32bit architecture)
3) have things like longer bit vectors manipulated at the same time (think of processing a whole chessboard in one go, instead of two)

Otherwise, as far as speed goes, doubling your bits is not equivalent to, say, doubling your clock speed...

---

### Post by naugiedoggie on 2008-03-07
> **jpkotta said:**
> I assume you're refering to ia32-libs and similar packages.  It's not so much an interoperability layer, it's more like a minimal 32-bit system within a 64-bit system.  x86-64 processors have all the 32-bit instructions that x86-32 processors have, so there's nothing like emulation going on.  The need for ia32-libs is simply because 32-bit binaries don't know how to deal with 64-bit libraries.  ia32-libs implement the same functionality as their 64-bit counterparts, the only difference is the interface is recognized by 32-bit programs.

The only slowdowns I've heard of with 64-bit systems is due to the fact that the pointers are bigger.  I read somewhere that gcc is about the same speed as on 32-bit, because it apparently uses pointers quite a lot and any speed gains from 64-bit were offset by having to move more data, keep fewer things in cache, etc.

Yes, 'interoperability' was a poor choice of words.  I actually just had this conversation at a client's the day before -- I am in the process of helping them move some software from 32-bit to 64-bit systems and the software, of course, is 32-bit.  So I am retailing somewhat what I was told during that conversation -- except that I inserted the bad word in there.

Thanks.

mp

---

