---
title: "why is FORTRAN still taught"
date: 2009-01-22
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-01-22
if i am not mistaken, FORTRAN is still used by engineers...why?

---

### Post by bruce89 on 2009-01-22
Why not?

---

### Post by monkeyking on 2009-01-22
I think it't because of the fast matrix operation library called, blas, linpack and lapack.

These are still the fastest way of handling numerical linear algebra on computers. (from what I've heard)

Futhermore fortran to c/c++ translaters exists, so there really hasn't been a need to reimplement og reinvent these routines.

I never bothers to learn fortran,
it's to ugly for me.

---

### Post by jimi_hendrix on 2009-01-22
what else is being deved in FORTRAN these days?

---

### Post by twisted_steel on 2009-01-22
> **jimi_hendrix said:**
> what else is being deved in FORTRAN these days?

I'm not sure about these days, but my FORTRAN professor worked on autopilot systems for Sikorsky (helicopters) in the 70s. I'm curious what other people have to say about modern FORTRAN development as well.

---

### Post by HyperHacker on 2009-01-22
Legacy code maintenance would probably be one reason. It might also be one of those languages they teach to students just so they can get an idea of how things work.> **monkeyking said:**
> I think it't because of the fast matrix operation library called, blas, linpack and lapack.

These are still the fastest way of handling numerical linear algebra on computers. (from what I've heard)Why haven't they been ported to C?

---

### Post by Juffo-Wup on 2009-01-23
> **HyperHacker said:**
> Why haven't they been ported to C?

It seems like some libraries (if not all) have already been translated to C, even if machine-translated using f2c. Anyhow, from what I've heard the routines contained in those packages are very optimized and mature, and the people who aren't willing to learn or use Fortran in order to access them  already have other (higher-level) languages that wrap around those libraries, like MATLAB and R/S/S-PLUS.

---

### Post by Old Jimma on 2012-06-29
Fortran is still used by scientists with computationally demanding applications... like Bayesian statisticians. The previous post suggests using R/S etc. These are very, very slow for computationally demanding work, and have very high memory requirements, even for some pretty mondaine applications like analysis of complex survey data.

However, advances in computing machinery makes the arguments for FORTRAN hard to make. For example, in 1995 I wrote a program for latent class models in both S and FORTRAN and ran both on a Sun workstation. At that time the S was very, very slow, and the FORTRAN program took 20 minutes to complete. Today, the R program to do the same computations on an average computer takes just a few seconds.

However, as time progresses, scientists ideas on what they'll try computationally increases, also. And in these cases R is still eclipsed by FORTRAN. It will always be that way, until FORTRAN is fades into history.

---

### Post by ofnuts on 2012-06-29
> **Juffo-Wup said:**
> It seems like some libraries (if not all) have already been translated to C, even if machine-translated using f2c. Anyhow, from what I've heard the routines contained in those packages are very optimized and mature, and the people who aren't willing to learn or use Fortran in order to access them  already have other (higher-level) languages that wrap around those libraries, like MATLAB and R/S/S-PLUS.
Are these libs written in plain Fortran? On x86, they are likely using SSE instructions (there may be CUDA or OpenCL versions).

---

### Post by MadCow108 on 2012-06-29
fortran has some significant performance advantages over C, namely the much stricter aliasing rules and, kind of related, no pointers (newer fortran has pointers but much less dominant than in c)

this gives the compiler much more options for optimization making you code easier to write and more readable than the C equivalent where you need a whole host of weird stuff to get what the compiler should but cannot do [0].

this makes fortran much more suitable for numerical number crunching.
many number crunching tools are historically written in fortran (for above reasons and of course fortrans age) and they need maintaining.
So its very common for university to teach fortran to be able to keep that code running and improve it.
Pretty much every scientist dealing with programming sooner or later encounters fortran in some (legacy) application.
E.g. scipy, it consists of 20% fortran.

[0] Granted this has improved lately by addition of a bunch of annotations to C (like restrict), or compiler intrinsics (like builtin_assume_aligned)

---

### Post by slavik on 2012-06-30
as someone mentioned mathematics libraries, I will add that there are clusters that run those ... really well.

---

### Post by liviogasp on 2012-07-19
> **jimi_hendrix said:**
> if i am not mistaken, FORTRAN is still used by engineers...why?
Everybody here talk about legacy code, but my point of view is a bit different: fortran (I'm talking about the recent revisions: 90,95,2003 etc.) is actually the easiest **compiled** language to learn if you have to deal with matrices and number crunching. You can add, multiply etc. matrices with one simple command, no for cycles implied. In the end you obtain clear and short sources, while if you used C you would have to deal with pointer, hard to mange indexes etc. What other language can do this and compile in fast binaries?

Then there is legacy code, that still matters today, and is more maintainable than automatically translated code.

---

### Post by bouncingwilf on 2012-07-19
As someone who cut his teeth using Fortran I can assure those that think it obsolete are wrong. For pure number crunching nothing beats it, for ease of programming, its up there with Python  (IBM also has - or used to have 30 years ago - a code and go compiler - a bit like python/basic interpreter). I only moved to C  20 years ago for a) bypassing the OS to get at the hardware direct and b) screen i/o handling (before GUI's) Modern Fortran has a lot going for it - as fast as C without the tricksy bits.

As for the legacy code - Mostly everything scientific was written in it ( and to a certain extent still is)  Much of my old Code was written in Fortran but linked to and using the C libraries where there was not a direct Fortran function/call


In fact, now that you mention it, I might go back to it for a little project I'm doing.

Bouncingwilf

---

