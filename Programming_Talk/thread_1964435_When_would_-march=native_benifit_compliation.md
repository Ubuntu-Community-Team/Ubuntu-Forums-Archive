---
title: "When would -march=native benifit compliation"
date: 2012-04-24
forum: Programming Talk
---

### Post by nolag on 2012-04-24
I did a test using the n-body test from [http://shootout.alioth.debian.org/u64q/benchmark.php?test=nbody&lang=gpp](http://shootout.alioth.debian.org/u64q/benchmark.php?test=nbody&lang=gpp) using -O2, -O3, -O3 -march=native and -O2 -march=native.  

There was not much of a difference between with and without -march=native.  I know it was only one test, but I'm wondering what test(s) would show it most.  I tried with both g++ and ipcp with these options.  Not sure why native was so close in most cases.  I felt like it would be a lot faster.

I used 500000000 as the argument so it took round 112-114 with everything, but always less then .5s difference between with and without native march, sometimes it did worse (I'm assuming it is just within the margin of error).

I have a core i7 laptop.

Also anyone know what maxresident is?  Intel's compiler was much higher, but faster.

---

### Post by ssam on 2012-04-24
it depends a bit on what CPU you have. back on 32bit x86 the default settings in gcc would produce a binary that would still run on a intel 386, which meant they missed a lot of opertunity to use new features in chips.

on 64bit x86, the compiler can assume that there are instructions like SSE, so can enable far more optimisation without know precily which chip you have.

It will also depend on the code. for example if it can take advantage of extra instructions on specific chips. that code example you posted looks like it uses very little RAM. if you found an example with some large arrays, then possible cpu specific cache optimisation may have an effect.

---

### Post by nolag on 2012-04-24
> **ssam said:**
> it depends a bit on what CPU you have. back on 32bit x86 the default settings in gcc would produce a binary that would still run on a intel 386, which meant they missed a lot of opertunity to use new features in chips.

on 64bit x86, the compiler can assume that there are instructions like SSE, so can enable far more optimisation without know precily which chip you have.

It will also depend on the code. for example if it can take advantage of extra instructions on specific chips. that code example you posted looks like it uses very little RAM. if you found an example with some large arrays, then possible cpu specific cache optimisation may have an effect.

Thanks, do you think that it is likely just the margin of error that caused the native compiled code to be slower or can that actually happen?

---

