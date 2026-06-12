---
title: "Explaining instruction sets and memory registers"
date: 2010-02-22
forum: Programming Talk
---

### Post by blueshiftoverwatch on 2010-02-22
What's a simple explanation of what an instruction set is, the differences between various instruction sets, and what a memory register is?

Are memory registers even smaller and quicker than the L# caches?

---

### Post by NovaAesa on 2010-02-22
> **blueshiftoverwatch said:**
> 
Are memory registers even smaller and quicker than the L# caches?Affirmative.

---

### Post by NoaHall on 2010-02-22
I think it's cute how you're trying to understand these things.

A memory register is indeed smaller and quicker than L# caches, as the L# **caches** are just that. The registers are being accessed quickly, and in small numbers at a time - that is, per cycle.

---

### Post by 3rdalbum on 2010-02-22
Register sizes are measured in bytes, aren't they? For a 32-bit CPU, it's 4 bytes per register.

Level x cache size is measured in kilobytes or megabytes.

---

### Post by koenn on 2010-02-22
> **blueshiftoverwatch said:**
> What's a simple explanation of what an instruction set is, the differences between various instruction sets, and what a memory register is?

Are memory registers even smaller and quicker than the L# caches?

This has to do with the design of (micro-)processors, like the processor in a computer.
I'm not an expert on this, but I think it goes something like this : 

registers are the parts of the processor that hold the actual data that's being processed - usually 8, 16, 32, ... bits at the time. There are also registers that keep track of program execution - eg a register that holds the memory address of the next program instruction to be executed. 

The instruction set is a set of instructions that are implemented on the chip, they are the actions that will be executed on the data in the register, eg move the content from one register to another, add the content of two registers together and write the result to a 3rd register, etc. 

L1/L2 cache operate a bit on the side of this : they store contents from main memory so it can reach the cpu faster.


Chips/processors differ in the number of registers they have, the width of a register (eg 8 bit vs 32 bit), and which instructions they have (their instruction set)


You don't really need to know any of this unless you're planning to design chips, or build an operating system or some other program that needs to talk to a chip directly. But if you're interested, wikipedia has some good starters:
[http://en.wikipedia.org/wiki/Microprocessor](http://en.wikipedia.org/wiki/Microprocessor)
[http://en.wikipedia.org/wiki/Processor_register](http://en.wikipedia.org/wiki/Processor_register)
[http://en.wikipedia.org/wiki/Instruction_set](http://en.wikipedia.org/wiki/Instruction_set)

---

### Post by blueshiftoverwatch on 2010-02-22
> **NoaHall said:**
> I think it's cute how you're trying to understand these things.
Is there really a need for that kind of arrogance?

---

### Post by NoaHall on 2010-02-22
> **blueshiftoverwatch said:**
> No need to be an arrogant ***.

I wasn't, I mean it. I think it's cute. I don't know why, it just is.

---

### Post by doas777 on 2010-02-22
think of an instruction set as a dictionary of machine code operations that a processor platform can perform. every task your computer performs is a combination of "instructions".

I take it you are studying assembly programming?

---

### Post by mcduck on 2010-02-22
> **3rdalbum said:**
> Register sizes are measured in bytes, aren't they? For a 32-bit CPU, it's 4 bytes per register.

Level x cache size is measured in kilobytes or megabytes.

yes, general-purpose registers are usually 32 bits for 32-bit CPU's and 64 bits for 64-bit processors... ;)

This is of course because registers are what the CPU actually uses when processing data, so if your processors calculates with 32-bit values the registers need to hold those 32 bits at a time.

Modern processors also include other than just the general purpose & instruction registers, so there are usually some larger registers for holding some floating-point data, for example, as any multimedia-related instruction sets (like SSE) will need to handle slightly larger amounts of data.

There can be other types of registers as well, for example the EmotionEngine processor used in Playstation2 had a bunch of special instructions for vector calculations, so it also had vector registers that were able to hold 4 x 32 bits of data each, and the processor then applied same instructions to all those 4 values at the same time. (this is why they called it 128-bit processor, it didn't count with 128 bit precision, but it *did* calculate 128 bits of data at a time)

---

### Post by Some Penguin on 2010-02-22
[http://arstechnica.com/cpu/4q99/risc-cisc/rvc-1.html](http://arstechnica.com/cpu/4q99/risc-cisc/rvc-1.html)
is archaic but probably still worth understanding.

Unless there's a newer edition out, [http://www.amazon.com/Computer-Architecture-Quantitative-Approach-4th/dp/0123704901](http://www.amazon.com/Computer-Architecture-Quantitative-Approach-4th/dp/0123704901) is probably the go-to book on computer architecture.

If you want an instruction set that is simple enough that it's been frequently used for teaching, look at the MIPS instruction set.  If you want something that looks like it was designed to give compiler authors lifetime employment, look at IA-64 (or now 'Intel Itanium Architecture', apparently).

---

### Post by blueshiftoverwatch on 2010-02-22
> **koenn said:**
> L1/L2 cache operate a bit on the side of this : they store contents from main memory so it can reach the cpu faster.
So, it's basically a much smaller but faster extension of your system RAM.
> **koenn said:**
> Chips/processors differ in the number of registers they have, the width of a register (eg 8 bit vs 32 bit), and which instructions they have (their instruction set)
Why do all of these architectures that were released long before x64 have just as much if not more registers?
> **doas777 said:**
> I take it you are studying assembly programming?
Actually no, I'm going to school for network management. Which I chose because I wanted to get into a good computer field that involved the least amount of programming knowledge as possible. But it seems like a good idea to be familiar with the how certain essential parts of a computer (like the CPU) work at the most basic and least abstract level. Lets say one day I had children and one of them asked me "How does a CPU work"? Most people could probably describe what a CPU does. But as to the actual technical workings of it, it might as well be magic or witchcraft as far as they're concerned. Sort of like how a car mechanic might be interested in the exact specifics of how an engine works.
> **NoaHall said:**
> I wasn't, I mean it. I think it's cute. I don't know why, it just is.
Ah, well than I severely misinterpreted your statement. It just seemed like you were trying to make fun of me because I couldn't think of any other way to interpret that statement.
> **Some Penguin said:**
> [http://arstechnica.com/cpu/4q99/risc-cisc/rvc-1.html](http://arstechnica.com/cpu/4q99/risc-cisc/rvc-1.html)
is archaic but probably still worth understanding.
I think I'll stick to the shorter article you posted instead of the 700 page book. I've only read the first page but so far it seems fairly interesting and not too technical.

---

### Post by Some Penguin on 2010-02-22
Regarding cache, cache is also physically much closer to the CPU, which will be important in so far as electrons take time to travel.

Regarding 32-bit and 64-bit architectures and their orders of appearance, bear in mind that --

- Intel 32-bit platforms were disproportionately associated with individual PCs, not 'big iron'

- Binary compatibility layers between 32- and 64-bit aren't trivial, and have even caused performance penalties (vs. running on native 32-bit hardware)

- Upgrading applications from 32- to 64- bit can be much more complicated than recompiling, because a LOT of code has been written (especially for Intel platforms, many of whose programmers probably never, ever programmed for any significantly different architecture) which makes implicit assumptions about how large types are (e.g. people that write binary files assuming 32-bit ints)

- Desktop users also tend to have much more variety in devices (accessories) attached, and get ticked off an OS upgrade means that most of that stops working

- Users of individual PCs tended not to run things like earthquake simulations or massively multiuser environments which meant that being able to address more memory or do faster double-precision arithmetic was critical

---

### Post by koenn on 2010-02-23
> **blueshiftoverwatch said:**
> So, it's basically a much smaller but faster extension of your system RAM.
Well, it's a bit like RAM, or it can be, but
1- you don't get "more RAM" from the cache, it just holds data that exists also in RAM (the way a web proxy cache holds pages that exist also on a web server)
2- it could be (technically, electronically) quite similar to RAM; or completely different. 


> **blueshiftoverwatch said:**
> 
Why do all of these architectures that were released long before x64 have just as much if not more registers? 
I don't know, I don't design chips. 
I suppose when you design a chip, you ask yourself 'what would be the best, fastest way to process those bits'  and depending on the answer you come up with, you include instructions and registers in your design to make things work the way you envisioned. So "more" or "less" is irrelevant - except maybe in regards to what it will cost to actually produce that chip. 


But really, this is almost purely electronics. 
To use your car analogy : you don't need to understand the chemistry of fuel, the physics of  detonation, or the math to describe how much energy the fuel/air mixture will produce in order to tell your kids how a combustion engine works.

---

### Post by doas777 on 2010-02-23
keep in mind, x64 is just a extended version of x86. pretty much the same, just a longer addressspace.

---

### Post by lisati on 2010-02-23
An instruction set is like a vocabulary, what a processor "knows" how to do.
A cache (from a French word meaning "hide" or "hidden") sits in between two devices which work at different speeds and is like a "helper" that lets each part of a system work at its own speed without impacting system performance.

---

### Post by blueshiftoverwatch on 2010-02-23
> **doas777 said:**
> keep in mind, x64 is just a extended version of x86. pretty much the same, just a longer addressspace.
Since x86 is 32 years old at this point and they've been extending it ever since it was originally 16 bits. I wonder how long before the technology is so old and inefficient that the industry will demand a new ISA/CPU standard? It sort of seems like they can only do so much for so long with a technology created in the late 70's.

---

### Post by doas777 on 2010-02-23
I've had the same thought, cause it is essentially ancient.

the problem is, that i don't trust what the current computing industry would do with an opportunity to start over. i am afraid that they will put untrustworthy "trusted computing" initiatives and content protection mechanisms and surveillance backdoors at the top of the priority list. once we are drm'ed in hardware, I fear we risk losing many digital freedoms.

---

