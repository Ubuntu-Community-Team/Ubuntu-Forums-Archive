---
title: "x86 register question"
date: 2012-01-13
forum: Programming Talk
---

### Post by nolag on 2012-01-13
In x86 I know you can access eax, ex (and on 64-bit rax), for int/long, short (and long long) types.  What I don't get is why gcc uses eax when I use a short?  I know that the result would be the same once the mov puts it to it's final location, but won't the overflow flag be off?

---

### Post by trent.josephsen on 2012-01-13
ax is the low (?) half of eax.  It's probably an adjustment gcc makes for simplicity and efficiency of code.

I think the overflow bit should only be set when a mathematical operation causes an overflow -- couldn't swear to it though.

---

### Post by Bachstelze on 2012-01-13
Yes, the overflow bit (and other control bits) are set by the ALU.

---

### Post by ofnuts on 2012-01-13
> **nolag said:**
> In x86 I know you can access eax, ex (and on 64-bit rax), for int/long, short (and long long) types.  What I don't get is why gcc uses eax when I use a short?  I know that the result would be the same once the mov puts it to it's final location, but won't the overflow flag be off?Yes... but IIRC there is nothing in the C standard that mandates an overflow detection.

---

### Post by Npl on 2012-01-13
32bit ops are plain alot faster on current CPUs than fractional (8/16bit ones).
The reason is that a 32bit ops sets all bits, while a fractional leaves some untouched and the ISA requires them to remain intact - that makes tracking depencies hard.
eg. :

1: mov eax, 1
2: mov eax, 2; can be executed immediatly, op1 could be even canceled and not taking any time on the CPU 
3: mov ax, 3; now eax still depends on bits from op2, op3 cant start before op 2 is done.

32bit ops on 64bit x86 CPUs are no prob because the remaining bits dont have to be kept intact (effectively they always write 64bit).

makes you really love RISC architectures which dont have useless shenanigans like 8/16 bit ops.

---

### Post by nolag on 2012-01-13
Thank you all for your replies, but there is still somethings I don't get or would like to ask about.

> **ofnuts said:**
> Yes... but IIRC there is nothing in the C standard that mandates an overflow detection.

I know C does not, but I am making a compiler, and may want my language to (have not decided yet)


> **Npl said:**
> 32bit ops are plain alot faster on current CPUs than fractional (8/16bit ones).
The reason is that a 32bit ops sets all bits, while a fractional leaves some untouched and the ISA requires them to remain intact - that makes tracking depencies hard.
eg. :

1: mov eax, 1
2: mov eax, 2; can be executed immediatly, op1 could be even canceled and not taking any time on the CPU 
3: mov ax, 3; now eax still depends on bits from op2, op3 cant start before op 2 is done.

32bit ops on 64bit x86 CPUs are no prob because the remaining bits dont have to be kept intact (effectively they always write 64bit).

makes you really love RISC architectures which dont have useless shenanigans like 8/16 bit ops.

I guess this would more apply to reordering than useless instructions?  So like below

```
movl eax, [eps-8]
movl [eps-4], eax
movw ea, [eps-12]
movw [eps-14], ea

```

if eps-12, and -14 are in cache, and eax is used with movw it can reorder it so that the cache is taken advantage of.  Thanks.


> **Bachstelze said:**
> Yes, the overflow bit (and other control bits) are set by the ALU.

I know the ALU takes care of that.  From what I understand if there is an overflow on a word (but not a long aka dword), add ax,bx  set he overflow while add eax,ebx would not.  Can someone verify this?  If so I may stick with that.

Thanks again everyone!  I am very interested in how it all works and what makes it faster :D.

---

### Post by Npl on 2012-01-14
> **nolag said:**
> I know C does not, but I am making a compiler, and may want my language to (have not decided yet)Well, have you considered not starting from scratch but using gcc or llvm. That way you only have to do the "language part" (overly simplified) and get all supported architectures from their backends.
> **nolag said:**
> I guess this would more apply to reordering than useless instructions?  So like below

```
movl eax, [eps-8]
movl [eps-4], eax
movw ea, [eps-12]
movw [eps-14], ea

```

if eps-12, and -14 are in cache, and eax is used with movw it can reorder it so that the cache is taken advantage of.  Thanks.cache is a different thing, but yes - the primary issues are the dependency on reading the output-register, superscalar and out-of-order execution. Just dint want to create elaborate examples.
Whats really important though is that modern x86 CPUs abandoned alot of instructions, including partial width ones. they are still supported for compatibility but they are using some kinda fallback-paths - means they are potentially alot slower. you can google [Directpath Vectorpath]("http://www.google.com/search?q=directpath+vectorpath") to get a better picture what I mean. But in short, CPUs have well supported fast ops and legacy ones - and the legacy ones arent just slow because of technical issues but also increasingly slow **by design** (resources are spent on making the fast path as fast as possible by keeping the legacy stuff from interfering)
> **nolag said:**
> I know the ALU takes care of that.  From what I understand if there is an overflow on a word (but not a long aka dword), add ax,bx  set he overflow while add eax,ebx would not.  Can someone verify this?  If so I may stick with that.yep if assume unsigned ints, for signed ones its the same (if you just sign-extended your 16bit values to 32bit). for unsigned ones you could just test for eax > 0xFFFF, or shift eax right by 16bits to get either 0 or 1 if overflow.

but get your compiler working first, then you can start scratching your head about such optimizations :D

---

### Post by nolag on 2012-01-15
Sorry, I should have been more clear, I am building a compiler that compiles to assembly, I am then using NASM as the assembler.  I am considering encapsulating nasm if my project becomes more complete (since it's license permits it).  

I looked up that term on google, but did not find much.  The only things I have ever seen on speed of instructions stop at i486 cycles.

I noticed another reason to use eax vs ax for math, if I want people to be able to say x = b +a and a and b are not the same type it is odd to use ax for one and ecx for the other.  I did decide that when assigning x a value I will use eax, ax or al (gcc does the same).

I know I can check if something is overflow by seeing the next bit, but I was hoping to avoid that.  I have not decided if I want to support that anyways.

Thanks again for your help.  It's funny how there are so many little gotchas on x86, like c passes all arguments (and return types) as int (or void* can't remember its the same on 32 bit but not 64 bit).  I don't know if I want my language to do that, it's a waste of stack space (granted a max of 3 bytes/argument max is not much but still, it is an odd choice) and counter intuitive.  I'm going to mark this as solved, but feel free to comment if you have more that I can learn from :D.

---

### Post by ofnuts on 2012-01-16
> **nolag said:**
> Thanks again for your help.  It's funny how there are so many little gotchas on x86, like c passes all arguments (and return types) as int (or void* can't remember its the same on 32 bit but not 64 bit).  I don't know if I want my language to do that, it's a waste of stack space (granted a max of 3 bytes/argument max is not much but still, it is an odd choice) and counter intuitive.  I'm going to mark this as solved, but feel free to comment if you have more that I can learn from :D.
Word-aligned parameters are loaded faster.

---

