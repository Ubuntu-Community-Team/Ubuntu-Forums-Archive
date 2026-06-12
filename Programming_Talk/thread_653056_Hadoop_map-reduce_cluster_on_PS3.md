---
title: "Hadoop map-reduce cluster on PS3?"
date: 2007-12-29
forum: Programming Talk
---

### Post by evymetal on 2007-12-29
Hi, I was wondering if anyone had tried running hadoop ([http://lucene.apache.org/hadoop/](http://lucene.apache.org/hadoop/)) on the playstation3 version of Ubuntu?

Unfortunately I t haven't got a PS3 to test this out on yet, but I thought it might be an ideal platform for clusters (60Gb to go towards the distributed file system, and 25.6 GFlops for float vector processing - plus they're fairly quiet).

Anyone got any suggestions or comments?

* Would Python & Java run fine under the hood?

* If I use Numpy with LAPack, will Java / Python / BLAS / LAPack together be able to make the most out of the processors - do we just write code as if it were a normal CPU and let GCC optimise it for us, or do we have to get our hands dirty?

* Multi-thread or Multi Process?

* How well would GCC compiled code run on the PS3 in general?

* Is Ubuntu the best choice? Notice Fedora-based systems seem to be used a lot (YDL seems to be used a lot), and we normally stick with BSD on our servers, but I'm not such a fan.

---

### Post by havchr on 2007-12-29
I can't shed too much light on the PS3, as I havn't gotten my hands proper dirty yet, but I have read through some of the documentation on the cell broadband engine and some articles regarding PS3 development.

My impression is that you will have to code very differently to utilize the PS3. You will even have to do multithreading differently (or should I say more specialized) for the SPU's than what you would do on say a core 2 CPU.
this is not just because there are more cores, but also because the cell works very differently than a core 2.

I have a feeling, allthough not entirely qualified, that python or java would have to be specially optimized to be able to exploit the SPU-cores to the extent they can be exploited.

if I recall correctly, the IBM cell SDK also has a special compiler for SPU programs.

---

### Post by evymetal on 2007-12-30
Thanks, the SDK suggestion helped me find loads more info. For the sake of future readers:

Looks like IBM only support Red Hat/Fedora, but they do have a custom kernel for Fedora, along with an optimized BLAS and A GCC toolchain for C / ADA / FORTRAN. (The Kernel patches have propagated to the Vanilla Kernel though)

So, (hopefully) BLAS should take care of controling the SPUs for dense vector operations in Numpy (python numeric lib) methods.

I've also found CorePy ([http://www.corepy.org/](http://www.corepy.org/)), which gives you C like access to pointers, and allows you to pass code on to run on specific processors (including the SPU)

For example
```
(Load the SPU instructions and environment)
>>> import corepy.arch.spu.isa as spu
>>> import corepy.arch.spu.platform as synspu
(Create a simple empty synthetic program)
>>> code = synspu.InstructionStream()
>>> code.add(spu.stop(0x200C))
(Execute the synthetic program on an SPU)
>>> proc = synspu.Processor()
>>> result = proc.execute(code)
>>> print result
12

```

However, I was thinking of running this code via Hadoopstreaming, on a variety of machines, so all my code needs to be portable. 

While this may slow it down a little, I think that with a couple of well crafted libraries I should be able to make use of about half of the possible power (unfortunately as python uses Doubles this is going to have to be half of 11 GFlops, rather than the total 150 GFlops available for singles.)


Should be enough for me to give it a go if I can get my boss to agree to run Linux boxes (BSD normally). If I manage, I'm sure we will propagate some code back to open-source, we release a fair bit of code :)



But does anyone know the state of Ubuntu on PS3? How much SPU based stuff is in the system level, and is the Ubuntu PS3 kernel built with debugging on (As I believe Fedora is)?

---

### Post by doktorZee on 2010-07-01
> **evymetal said:**
> Thanks, the SDK suggestion helped me find loads more info. For the sake of future readers:

Looks like IBM only support Red Hat/Fedora, but they do have a custom kernel for Fedora, along with an optimized BLAS and A GCC toolchain for C / ADA / FORTRAN. (The Kernel patches have propagated to the Vanilla Kernel though)

So, (hopefully) BLAS should take care of controling the SPUs for dense vector operations in Numpy (python numeric lib) methods.

I've also found CorePy ([http://www.corepy.org/](http://www.corepy.org/)), which gives you C like access to pointers, and allows you to pass code on to run on specific processors (including the SPU)

For example
```
(Load the SPU instructions and environment)
>>> import corepy.arch.spu.isa as spu
>>> import corepy.arch.spu.platform as synspu
(Create a simple empty synthetic program)
>>> code = synspu.InstructionStream()
>>> code.add(spu.stop(0x200C))
(Execute the synthetic program on an SPU)
>>> proc = synspu.Processor()
>>> result = proc.execute(code)
>>> print result
12

```

However, I was thinking of running this code via Hadoopstreaming, on a variety of machines, so all my code needs to be portable. 

While this may slow it down a little, I think that with a couple of well crafted libraries I should be able to make use of about half of the possible power (unfortunately as python uses Doubles this is going to have to be half of 11 GFlops, rather than the total 150 GFlops available for singles.)


Should be enough for me to give it a go if I can get my boss to agree to run Linux boxes (BSD normally). If I manage, I'm sure we will propagate some code back to open-source, we release a fair bit of code :)



But does anyone know the state of Ubuntu on PS3? How much SPU based stuff is in the system level, and is the Ubuntu PS3 kernel built with debugging on (As I believe Fedora is)?

2.5+ years later... any update on this?

---

### Post by alphageek89 on 2010-07-25
Is it possible anymore to use Linux kernels on the PS3 after the Sony Firmware update disabled the guest os feature.

---

