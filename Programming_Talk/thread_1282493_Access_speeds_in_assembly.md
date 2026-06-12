---
title: "Access speeds in assembly"
date: 2009-10-04
forum: Programming Talk
---

### Post by falconindy on 2009-10-04
**Short version:** I'm curious as to the order in which these access methods rank in assembly: registers, stack, and memory (via direct addresses). I have a funny feeling that's the hierarchy right there, but I'm still fairly new to assembly...

**Long version:** I'm taking an x86 assembly class (much to my dismay using MASM), and our last assignment was to write the first 24 terms of the Fibonacci sequence. We were asked to write it with registers so I did, with gratuitous use of the xchg instruction.

Then, I had a thought. Why not write it using a pointer in memory (essentially an array)? I thought I was really clever when I was able to do it without using a 'mov' operation, and only arithmetic.

After that, I figured that there had to be a way to abuse the stack to store values, but ditched the idea with the suspicion that I would just be rewriting the xchg instruction (and likely less efficiently).

So I got to wondering which of these methods was the fastest, but found myself at a loss. M$ provides junk for gauging performance with MASM, and this is also a really small amount of code to be measuring execution time. Anyone have any experience with assembly to know which access methods are the quickest?

---

### Post by froggyswamp on 2009-10-04
Your hierarchy is correct. I'd suggest getting a (thin) book on (x86) assembly if you're planning to do anything with it in the future.

---

### Post by cszikszoy on 2009-10-04
The access speeds depend on both the operation and the operands (and the architecture).  Typically, operations between 2 registers are very fast.  The x86 architecture is an example of a pipelined architecture so most operations will take more than one clock cycle.  Compare that to the MIPS architecture where operations typically perform in fewer clock cycles.

For reference, I found [this website]("http://www.penguin.cz/~literakl/intel/intel.html") that lists the x86 ASM operations.  If you click on  them it will tell you the number of clock cycles the operation takes to complete depending on what the operands are.

---

### Post by falconindy on 2009-10-04
> **cszikszoy said:**
> For reference, I found [this website]("http://www.penguin.cz/~literakl/intel/intel.html") that lists the x86 ASM operations.  If you click on  them it will tell you the number of clock cycles the operation takes to complete depending on what the operands are.
That's excellent! Thank you!

---

### Post by wmcbrine on 2009-10-04
The stack *is* in main memory. The stack instructions I suppose are quicker to decode than pointer-style instructions, but any RAM access is slow. Registers are much faster.

cszikszoy, that's a nice reference, but it's very outdated. Most instructions on a modern x86 do *not* take more than one cycle; in fact, it's more like instructions per cycle than cycles per instruction now, what with simultaneous, partial, out-of-order execution.

Cache hits are the big thing now. The cache is much faster than RAM, so you try to keep your algorithms running within the cache.

---

### Post by falconindy on 2009-10-04
> **wmcbrine said:**
> The stack *is* in main memory. The stack instructions I suppose are quicker to decode than pointer-style instructions, but any RAM access is slow. Registers are much faster.

cszikszoy, that's a nice reference, but it's very outdated. Most instructions on a modern x86 do *not* take more than one cycle; in fact, it's more like instructions per cycle than cycles per instruction now, what with simultaneous, partial, out-of-order execution.

Cache hits are the big thing now. The cache is much faster than RAM, so you try to keep your algorithms running within the cache.
True, but the stack is treated separately and access to it generally seems to be faster (at least based on a 80486).

Correct me if I'm wrong, but the general trend in assembly seems to be: the more rules and/or the more limited your access, the faster it is. You only have a few registers, your stack access is limited in the way you can access it (FILO) but storage is broader, and then RAM access is sort of do-what-you-want and in almost unlimited quantities.

Is there a specific way to ensure instructions stay within the cache? Or, will instructions just default to the cache, and once they exceed the size, overflow to RAM?

---

### Post by Can+~ on 2009-10-04
> **falconindy said:**
> True, but the stack is treated separately and access to it generally seems to be faster (at least based on a 80486).

It's still memory. It will probably take more than one atomic instruction to access it, like lw, decrease stack pointer (unless the cpu provides a single instruction).

> **falconindy said:**
> Correct me if I'm wrong, but the general trend in assembly seems to be: the more rules and/or the more limited your access, the faster it is. You only have a few registers, your stack access is limited in the way you can access it (FILO) but storage is broader, and then RAM access is sort of do-what-you-want and in almost unlimited quantities.

Everything has a tradeoff. The ideal scenario would be to have all you need on registers and process it without even going to ram, or even issuing an interruption (no I/O, no storing anywhere).

The tradeoff of having everything in registers is that you're limited, and you'll probably have to use more instructions to swap around data to make space for new things.

IMO. This kind of fine-grained optimization is utterly useless. Why would you ponder so much on this, if eventually the scheduler will do a context switch and throw everything into memory? In other words, there are system-wide operations that have a major impact on how programs run, that you can achieve by coding. It's almost like trying to fine tune a sports car, putting in inside a truck and have it carried around to show off to friends. It will be fine tuned, but in the end it won't matter, the truck will be the one that decides your ultimate speed.

Have fun with assembly, but don't let it get over your head.

---

### Post by falconindy on 2009-10-04
> **Can+~ said:**
> The tradeoff of having everything in registers is that you're limited, and you'll probably have to use more instructions to swap around data to make space for new things.
...and out of my own self interest, I'd like to understand the trade-offs.
> **Can+~ said:**
> IMO. This kind of fine-grained optimization is utterly useless. Why would you ponder so much on this, if eventually the scheduler will do a context switch and throw everything into memory? [etc etc etc]
And you're certainly entitled to your own opinion. With each new generation of processor, its effectively harder and harder to write something in assembly that will be a burden on the CPU (without intentionally doing something to chew up cycles). I think of assembly as being the ultimate programatical puzzle -- as many ways as there are to concoct a solution in a high level language, there's far more solutions in assembly because of the fine-grain control you're allowed. Again, out of self interest, I choose to spend time on this "useless" optimization. You obviously enjoy coding for reasons other than I do.

> **Can+~ said:**
> Have fun with assembly, but don't let it get over your head.
Too late. I had a dream the other night... cut to the chase, I woke up at 2am to write assembly.

---

### Post by Can+~ on 2009-10-04
> **falconindy said:**
> I think of assembly as being the ultimate programatical puzzle

Really? It was the exact same opposite for me, I thought of it almost like a by-product of a higher level language (C for instance), something that is so trivial that the computer could figure it out for itself and wasn't worth of wasting time thinking on it that much.

> **falconindy said:**
> as many ways as there are to concoct a solution in a high level language, there's far more solutions in assembly because of the fine-grain control you're allowed. Again, out of self interest, I choose to spend time on this **"useless"** optimization. You obviously enjoy coding for reasons other than I do.

Don't get me wrong, I also learnt Assembly for pretty much the same reasons, plus giving you a more deeper view on the Programming Abstractions as a system. The thing is that I never sought for ultimate speed, because I knew that this problem is already solved by a compiler+assembler, and it's underlying optimizations.

> **falconindy said:**
> Too late. I had a dream the other night... cut to the chase, I woke up at 2am to write assembly.

I wonder what Freud would've said about that.

---

### Post by cszikszoy on 2009-10-04
> **wmcbrine said:**
> cszikszoy, that's a nice reference, but it's very outdated. Most instructions on a modern x86 do *not* take more than one cycle; in fact, it's more like instructions per cycle than cycles per instruction now, what with simultaneous, partial, out-of-order execution.

Sorry, but that's just wrong.  The x86 architecture is a perfect example of a pipelined architecture.  It's true that many operations will complete in one clock cycle, The commonly used operations are usually implemented with gates so that they do complete in one clock cycle.

Operations per cycle can't happen.  With a pipelined architecture, it is true that several operations may complete on the same clock cycle, but it depends on the stream of instructions.  But still, the first stage of the architecture is the fetch and decode.  This happens in exactly one clock cycle, and it happens sequentially (meaning the CPU doesn't fetch the next 10 instructions at the same time, it fetches them one by one).

Furthermore, to the OP, you'll find a lot of people here that don't like or don't know how to really use ASM because python & the like are generally what's accepted and used in this forum.  Speak to someone outside the Computer Science realm and you'll see that ASM is incredibly useful, and incredibly powerful.  I work for a government contractor and use ASM extensively in systems where timing is absolutely critical.  ASM is required in these situations because if you have the datasheet for the particular CPU you're working with, you know *exactly* how long a particular set of instructions will take.  Higher level languages just won't work in these situations.

---

### Post by wmcbrine on 2009-10-04
> **cszikszoy said:**
> Furthermore, to the OP, you'll find a lot of people here that don't like or don't know how to really use ASM because python & the like are generally what's accepted and used in this forum.  Speak to someone outside the Computer Science realm and you'll see that ASM is incredibly useful, and incredibly powerful.Oh, please. There's a very narrow range of applications for which ASM is still appropriate.

I've spent a lot of time counting cycles. In retrospect, I think most of that time was wasted.

---

### Post by falconindy on 2009-10-04
> **Can+~ said:**
> Don't get me wrong, I also learnt Assembly for pretty much the same reasons, plus giving you a more deeper view on the Programming Abstractions as a system. The thing is that I never sought for ultimate speed, because I knew that this problem is already solved by a compiler+assembler, and it's underlying optimizations.
Ahh, but a compiler won't give you a more efficient program if you used a heap sort when a shell sort or a quicksort would have been better. If you scale that sort of optimization down to an assembly level, that's really what I'm looking to accomplish. Perhaps I'm going about it the wrong way?

> **Can+~ said:**
> I wonder what Freud would've said about that.I'm sure almost **any** psychologist would have a field day with me.

---

### Post by cszikszoy on 2009-10-04
> **wmcbrine said:**
> Oh, please. There's a very narrow range of applications for which ASM is still appropriate.

Sure, in your industry / line of work.  But as I've stated, it's not in mine (and many others).

---

### Post by Can+~ on 2009-10-05
> **falconindy said:**
> Ahh, but a compiler won't give you a more efficient program if you used a heap sort when a shell sort or a quicksort would have been better.

And it isn't supposed to. That wasn't my point, at all. The boring things about instructions are managed by the compiler, choosing the correct algorithm and/or data structure is what makes your code better, independent of the programming language.

> **falconindy said:**
> If you scale that sort of optimization down to an assembly level, that's really what I'm looking to accomplish. Perhaps I'm going about it the wrong way?

Not sure about that. In my mind, I picture that once you have everything up in memory, however it gets processed won't matter, or if it does, it will be minimal using the same algorithm.

This kinda remind me of the [gentoo crowd]("http://funroll-loops.info/").

But more importantly, it reminds me of myself. I used to be the "DIY" kid. If I wanted a linked list, I would code it myself, to get a specialized list, that does what I want, and does it optimal for my solution.

But then again, the solution I built is "too specific", later I find myself wanting to have a more generic list, a list that can do other things, so I code them accordingly, and end up having a completely generic list.

On the process of having a generic list, I dumped everything that made the list specialized, therefore, I removed the single advantage I thought I would gain by making my own list.

And this is nothing wrong, abstractions exist for a reason, someone, somewhere, realized that a single problem was repeating way too much, so decided that he would do a generic solution trying to satisfy every possible scenario, therefore, providing a solution to the problem and creating a more abstract construct.

A set of abstract constructs that can speak to each other on the same level (for instance, not going lower, eg. Imagine that a java function suddenly wants a int *pointer, it would break the abstraction layer). Then the whole abstraction shifts to a higher one.

Your idea of moving algorithms to lower level languages is not wrong, but the whole point of Programming languages is that they build a layer on top of an older one, being the most basic one, the hardware. So pushing algorithms closest to hardware, implies a gain in speed, but a decrement in genericness, and losing touch with higher-level interfaces that would probably make a better use of said functions on the long run.

And how do I know this much about abstractions? Or where this theory comes? From the [Systems Theory]("http://en.wikipedia.org/wiki/Systems_theory"). I embraced the Hollistic viewpoint of things.

---

### Post by phrostbyte on 2009-10-05
GCC is basically a dude with a long UNIX beard. He has an expert knowledge of the internals of modern CPUs. He has been studying assembly optimization for years. And he lets you write code in C and he will put his expertise to work for you hand optimizing all that C code into very performant assembly code. :P

---

### Post by ibuclaw on 2009-10-05
> **phrostbyte said:**
> GCC is basically a dude with a long UNIX beard. He has an expert knowledge of the internals of modern CPUs. He has been studying assembly optimization for years. And he lets you write code in C and he will put his expertise to work for you hand optimizing all that C code into very performant assembly code. :P

... and yet the Intel C Compiler is far most adept at optimising for the Intel Architechtures. ;)

Even then, autogenerated assembly still isn't good enough, as there will always be unneeded instructions put in place.

Regards
Iain

---

### Post by phrostbyte on 2009-10-05
> **tinivole said:**
> ... and yet the Intel C Compiler is far most adept at optimising for the Intel Architechtures. ;)

Even then, autogenerated assembly still isn't good enough, as there will always be unneeded instructions put in place.

Regards
Iain

Yes, the Intel compiler is more likely to spontaneously use SIMD instructions via auto-vectorization. GCC 4.4 has much improved in this regard.. I think if you will benchmark GCC against Intel's compiler suite you might be surprised.

Regardless I believe there are very few places where a programmer even one needing to do optimization will ever need to write assembly. 

There exists libraries such as AMD's Math Library, or Intel's performance primitives, which are written with extremely optimized assembly routines and cover a wide scope of mathematical algorithmic primitives. Open source libraries like FFWT or the GNU Scientific Library are similar.

These numerical libraries or GNU/Intel compilers are written by experts who understand processor optimization very well. It's unlikely unless you too are an expert that you will outdo them. :)

As long as you write in C or Python improvements to the tooling will ensure your programs can continue to run faster. Can you say the same for assembly?

Look at PyPy or unladen-swallow: completely unmodified Python programs run faster. I believe that because you have richer metadata. In theory you have more to work with, for optimization. I believe in 10-20 years from now people might be rewriting their assembly routines in Python or Ruby for optimization purposes. :)

---

### Post by grayrainbow on 2009-10-05
At first one little note: assembly is mainly useful in order to understand how computer works(which is a must if one wants to call himself/herself programmer), after that one can always use "asm" block in C/C++ if needed :)

About the stack, well it's FILO, but you can access everything with SP+value(assuming resulting address is valid), and one need to managed SP(and in general different architecture have a different understanding of it). Btw, biggest reason that Macs where platform of choice for every musician - it was simply faster and better, most notably PPC has a lot more registers :)

There's also something called compiler intrinsics which let programmer tell to "everything" knowing compiler that in some places...well, compilers just sucks and better left the job done by human(after all only person who write the program knows that algorithm need cache flush at specific time in order to be useful).

P.S. I'm amazed how thread about assembly start to not have anything to do with assembly, but more with other languages... come on! If you don't know something about the topic stop flooding and make another thread about abstractions and is it useful and when!

---

### Post by falconindy on 2009-10-05
> **Can+~ said:**
> And it isn't supposed to. That wasn't my point, at all. The boring things about instructions are managed by the compiler, **choosing the correct algorithm and/or data structure is what makes your code better, independent of the programming language.**That's all I'm trying to do.

> **Can+~ said:**
> This kinda remind me of the [gentoo crowd]("http://funroll-loops.info/").
I may have seen that before, but I still laughed out loud this time.

> **Can+~ said:**
> Your idea of moving algorithms to lower level languages is not wrong, but the whole point of Programming languages is that they build a layer on top of an older one, being the most basic one, the hardware. So pushing algorithms closest to hardware, implies a gain in speed, but a decrement in genericness, and losing touch with higher-level interfaces that would probably make a better use of said functions on the long run.
Well put.

[quote=grayrainbow]P.S. I'm amazed how thread about assembly start to not have anything to do with assembly, but more with other languages... come on! If you don't know something about the topic stop flooding and make another thread about abstractions and is it useful and when![/quote]
Assembly is intrinsic to a better understanding of other languages. It's only natural that almost any thread about assembly gets derailed. My initial question was answered already anyways.

---

### Post by rCXer on 2009-10-05
> **falconindy said:**
> (much to my dismay using MASM) [JWasm](http://www.japheth.de/JWasm.html) is is a MASM clone that runs in linux.  Haven't tried it though...

---

### Post by falconindy on 2009-10-06
> **rCXer said:**
> [JWasm](http://www.japheth.de/JWasm.html) is is a MASM clone that runs in linux.  Haven't tried it though...
Sure, and I have that. Now show me a way to link on Linux and I'll still need a Windows environment to test.

I'd rather learn NASM on the basis that I'm tired of dealing with anything and everything Microsoft after 15+ years. Fortunately, porting from one to the other hasn't proven to be **too** tedious.

---

