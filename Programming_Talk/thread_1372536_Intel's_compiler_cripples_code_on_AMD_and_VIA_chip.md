---
title: "Intel's compiler cripples code on AMD and VIA chips"
date: 2010-01-04
forum: Programming Talk
---

### Post by mmix on 2010-01-04
This is the reason why intel cpu looks better than AMD/VIA

[http://www.theinquirer.net/inquirer/news/1567108/intel-compiler-cripples-code-amd-via-chips](http://www.theinquirer.net/inquirer/news/1567108/intel-compiler-cripples-code-amd-via-chips)

[http://www.osnews.com/story/22683/Intel_Forced_to_Remove_Cripple_AMD_Function_from_Compiler_](http://www.osnews.com/story/22683/Intel_Forced_to_Remove_Cripple_AMD_Function_from_Compiler_)

---

### Post by SunSpyda on 2010-01-04
Doesn't surprise me. But then again, how many *actually use* Intel's own compiler? I thought the world was mostly using MS's compilers for Windows, or GCC for *nix.

---

### Post by mmix on 2010-01-04
see the link of osnews.
intel is king of cpu world, their will is not fair in every way.

> **SunSpyda said:**
> Doesn't surprise me. But then again, how many *actually use* Intel's own compiler? I thought the world was mostly using MS's compilers for Windows, or GCC for *nix.

[quote="osnews"]
In fact, Fog points out that even benchmarking programs are affected by this, up to a point where **benchmark results** can differ greatly depending on how a processor identifies itself. Ars found out that by changing the CPUID of a VIA Nano processor to AuthenticAMD you could increase performance in PCMark 2005's memory subsystem test by 10% - changing it to GenuineIntel yields a 47.4% performance improvement! There's more on that here [print version - the regular one won't load for me]. [/quote]

[quote="osnews"]
"If the vendor string says 'GenuineIntel' then it uses the optimal code path. If the CPU is not from Intel then, in most cases, it will run the slowest possible version of the code, even if the CPU is fully compatible with a better version." [/quote]

---

### Post by Queue29 on 2010-01-05
If AMD and VIA want optimized code on their hardware they can write their own compilers.

---

### Post by Habbit on 2010-01-05
> **Queue29 said:**
> If AMD and VIA want optimized code on their hardware they can write their own compilers.

The problem is not the Intel compiler not delivering the best possible optimizations for non-Intel processors, but the fact that it also failed to perform pretty generic optimizations (and sometimes even chose the _worst_ possible option) if the CPU did not identify itself as Intel.

---

### Post by CptPicard on 2010-01-05
It is an interesting question on whether this is a matter of Intel putting their work into Intel-specific optimizations and not really working on the "generic optimizations" part of the compiler (which would be understandable), or actively, intentionally making it suck  on non-Intel. In the latter case it's a bit like the Windows "problems" on DR DOS back in the day... :)

---

### Post by MadCow108 on 2010-01-05
how is worst possible option meant?
in my opinion that would be an infinite loop or something that takes very very long o_O
the formulation "worst" seems quite exaggerated

---

### Post by John Bean on 2010-01-05
> **MadCow108 said:**
> how is worst possible option meant?
in my opinion that would be an infinite loop or something that takes very very long o_O
the formulation "worst" seems quite exaggerated

An infinite loop will indeed take a *very* long time, no matter what the optimisation...

"Worst" can't be exaggerated. It is - by definition - the least optimal choice from a finite set of options. There's nothing worse than "worst" ;-)

---

### Post by cascade9 on 2010-01-05
Very lame Intel, but its not that hard to see why they did this....or why they thought they could get away with it. 

It makes me wonder how much the intel compiler is used.

---

