---
title: "Intel vs GCC"
date: 2010-01-22
forum: Programming Talk
---

### Post by blazemore on 2010-01-22
This isn't a troll thread, and I don't want to start a flame war.

What are the advantages and disadvantages of using the Intel compiler over GCC.
What about other compilers? What are the advantages and disadvantages, including free software philosophy.
What are the legal implications of compiling a binary with Intel's compiler?
Are you still allowed to distribute a GPL program if you compile the code with a proprietary compiler?
Does Intel not have software patents on compiling x86, which GCC would surely infringe?

I've been curious about this for a while, and I don't have much technical knowledge about compilers, as I am only due to start my compilers module in 2 days.

---

### Post by Shin_Gouki2501 on 2010-01-22
[http://www.agner.org/optimize/blog/read.php?i=49](http://www.agner.org/optimize/blog/read.php?i=49)

or

[http://www.itwriting.com/blog/2031-how-intels-compiler-underperforms-on-other-cpus-artificial-impairment-versus-failure-to-optimise.html](http://www.itwriting.com/blog/2031-how-intels-compiler-underperforms-on-other-cpus-artificial-impairment-versus-failure-to-optimise.html)

---

### Post by blazemore on 2010-01-22
Yes I heard about that. I subscribe to loads of blogs on my Google Reader (awesome btw). According to Linux Format they are also being sued by the US government (Under some equivalent of EU competition laws, I don't know much about 'merkin laws)

But assuming they've done that, and now from a purely technical and legal (rather than moral) viewpoint, what are the pros and cons?

---

### Post by TheStatsMan on 2010-01-22
Intel will give more performance, particularly when you have a lot of fine grain parallelisation in your code. There are a lot of nice features for optimising the performance of your code. GCC is obviously more portable. Beware when comparing performance though that Intel's default setting is to run fairly heavy optimisations, where as GCC doesn't.

---

### Post by MadCow108 on 2010-01-22
I guess if you use gcc 4.4 (or even 4.5) the difference will be quite negligible.
The big advantage of icc is its auto vectorizer.
But gcc 4 also has one and 4.4 adds quite some functionality.
also gcc 4.5 will finally be able to do whole program optimization.

But the only way to know for sure is just benchmark.
be sure to compile properly with gcc, e.g. set right mcpu/march/msse flags and enable the autovectorizer with -ftree-vectorize

---

### Post by blazemore on 2010-01-22
> **MadCow108 said:**
> I guess if you use gcc 4.4 (or even 4.5) the difference will be quite negligible.
The big advantage of icc is its auto vectorizer.
But gcc 4 also has one and 4.4 adds quite some functionality.
also gcc 4.5 will finally be able to do whole program optimization.

But the only way to know for sure is just benchmark.
be sure to compile properly with gcc, e.g. set right mcpu/march/msse flags and enable the autovectorizer with -ftree-vectorize

Well I just ./configure && make && make install
So how come GCC doesn't run the same optimisations, if people always do it with flags anyway? Surely they should be opt OUT rather than in? Or does it depend on the distro?

What about new Intel processors like Lynnfield? Does GCC have to "catch up" with Intel for a while after a new release?

---

### Post by MadCow108 on 2010-01-22
gcc is designed to produce extremely portable code. So its just logical that its greatest strength will be the default mode. Also gcc was not always as good at optimizing as it is today.

a program compiled with gcc for generic x86 runs on almost every(all?) x86 available, including those without vector instructions.

a configure script can include machine dependent flags making there program potentially faster but less portable, gcc lets that decision to the to the distributer.
It is also often solved by runtime cpu detection, see mplayer/ffmpeg.

I'm sure that gcc has to catch up with icc for brand new architectures. Seems logical as intel has access to all details during chip development whereas gcc will have to wait until their published or even reverse engineered.
But this is only an issue for high performance computing. Normal programs will rarely be able to use the new features effectively anyway.

---

### Post by blazemore on 2010-01-22
> **MadCow108 said:**
> gcc is designed to produce extremely portable code. So its just logical that its greatest strength will be the default mode. Also gcc was not always as good at optimizing as it is today.

a program compiled with gcc for generic x86 runs on almost every(all?) x86 available, including those without vector instructions.

a configure script can include machine dependent flags making there program potentially faster but less portable, gcc lets that decision to the to the distributer.
It is also often solved by runtime cpu detection, see mplayer/ffmpeg.

I'm sure that gcc has to catch up with icc for brand new architectures. Seems logical as intel has access to all details during chip development whereas gcc will have to wait until their published or even reverse engineered.
But this is only an issue for high performance computing. Normal programs will rarely be able to use the new features effectively anyway.

Right, and the physical hardware performance increases would far outweigh the software optimisations anyway. Like, if I upgraded my (aging?) first generation Core 2 duo to a shiny core i5, it wouldn't be compiler optimisations that would make HD video encoding run faster, it would be raw oscillating performance.

---

### Post by ibuclaw on 2010-01-22
> **blazemore said:**
> Right, and the physical hardware performance increases would far outweigh the software optimisations anyway. Like, if I upgraded my (aging?) first generation Core 2 duo to a shiny core i5, it wouldn't be compiler optimisations that would make HD video encoding run faster, it would be raw oscillating performance.

Correct.

Which is also why compiling with the -OMG-FAST gcc flag won't actually make it any noticeably quicker.

---

### Post by lostinxlation on 2010-01-22
Technically, if you run on Intel CPU, using Intel compiler is the best option. 
Microprocessors have a lot of restrictions in microarchitecture. For example, if it has only 2 floating point units, compiler shouldn't schedule more than 2 floating point instructions back to back otherwise it gets performance impact. If it has only 2 address calcuation units, the compiler shouldn't schedule more than 2 load/store instructions in the same cycle otherwise it hits performance. If it can issue only 1 branch instructions in a cycle, the compiler should make the size of basic block more than the instruction issuance width. These examples are simple ones, there are more deep inside the chips that people outside the microprocessor team cannot see.
Intel hardware team is the one which knows those restrictions the best, and Intel compiler team works closest to them.

---

### Post by grayrainbow on 2010-01-23
> **blazemore said:**
> Right, and the physical hardware performance increases would far outweigh the software optimisations anyway. Like, if I upgraded my (aging?) first generation Core 2 duo to a shiny core i5, it wouldn't be compiler optimisations that would make HD video encoding run faster, it would be raw oscillating performance.
That's sometimes could be true, except cases when it's not :)
Imagine that you compile a proper multimedia program without any SIMD support for core i7 CPU and somebody else compile it with SIMD support for core 2 duo. Which one will goes faster?(hint - the program using GPU support will be way faster than both).
It's kinda like transition from 16 bit to 32 bit, and now to 64 bit.

And of course it's not only about CPU freq(nowadays that's the least significant factor), registers size, addressable memory, etc, it's about the whole processor architecture, and how software use it.

About icc vs gcc, well icc was kinda fastest compiler for intell CPU, and as I know they promise that compiler will no longer check for type of processor when do optimizations, but it's nowhere near gcc as supported platforms and performance on PPC and RISK as general(and most of processors in the world are not x86 or x86_64).

P.S. Btw, you probably will do more with parsers(formal grammatic, etc) when learning compiler design, but that probably depends on university.

---

### Post by blazemore on 2010-01-23
Well here's an example question

(d) Use the extended set of typing rules to formally prove that the expression
       ```
let xys : NatList = (cons x (cons y xys)) in (head (tail xys))
```
    is well-typed and what its overall type is in the typing context
```
&#915;2 = x : Nat, y : Nat
```

---

### Post by CptPicard on 2010-01-23
> **blazemore said:**
> Right, and the physical hardware performance increases would far outweigh the software optimisations anyway.

Although consistently applying "common" optimizations (which is what compilers are very good at) produces noticeable performance increases... that is, it is often a very significant percentage of unoptimized running time. It's not the last bit of extreme tuning that tends to matter, but all the rest.

(EDIT: of course there is the exceptional case where your code actually is very amenable to some special optimization provided by some compiler... the speedup can be quite dramatic in those cases)

---

### Post by sinbadbuddha on 2010-01-23
First of all, GCC is obviously much more portable, and in fact no other compiler can better it on that one. Intel produces code for Intel chips. Pentium chips.

Intel were being sued by AMD, and one of the issues was that their compiler was shown to compile bad AMD code. AMD also develop a compiler which optimizes heavily for ia64/amd64 chips, a version of Open64 under the GPL as an extension to GCC. I do not know much about this, but generally Intel compilers produce faster code than GCC, and in fact faster code than any other major compiler (I don't know about Open64), including MS Visual C++ and Borland. It does this  by making heavy use of the 128-bit media registers.

You cannot publish Intel-compiled binaries under an open source license, because the libraries it supplies are limited in this regard. You are completely free regarding license choice when using GCC.

One more thing: If you're running it on linux, it strives to be compatible with GCC, so you shouldn't have trouble switching, if you want to. Intel may have patents on specific optimizations (I don't know much about Intel patents, but I think they do), but if they were so invasive that you couldn't actually legally compile for Intel with anything except Intel, it would make them bloody unpopular. Software patents are always a problem though.

---

