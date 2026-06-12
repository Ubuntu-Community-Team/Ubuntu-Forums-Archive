---
title: "Applications for functional programming in the real world"
date: 2010-09-18
forum: Programming Talk
---

### Post by absolutezero1287 on 2010-09-18
What are they? I'm a computer science major and I love functional programming. I'm currently trying to learn haskell and common lisp. From my understanding, functional programming does away with state. How would you use a functional programming language for systems programming? I have so many questions.

---

### Post by worseisworser on 2010-09-18
An application for functional programming in the real world is that it allows one to deal with concurrency in a particular way that makes some things there a lot easier. This is real and increasingly so because we're now seeing 2, 4, 6, 8 and 12+++ core CPUs already here or here very soon (1-2 years from now).

I'm not sure what you mean by systems programming, but if/when you eventually need to communicate (state and I/O) with the outside world you can use things like transactions or STM: [http://en.wikipedia.org/wiki/Software_transactional_memory](http://en.wikipedia.org/wiki/Software_transactional_memory)

Some people think transactions and functional programming are in direct opposition with each other; this is wrong; they can complement each other.

edit:
I think Haskell has STM support built in, and Common Lisp has several STM libraries available; my very own SW-STM ( [http://github.com/lnostdal/SW-STM](http://github.com/lnostdal/SW-STM) ) for instance.

---

### Post by matthew.ball on 2010-09-18
At my university they recently verified an ad-hoc kernel which was written in C using Haskell. I don't know the exact details, but that's one strength of (pure) functional programming - proofs. Which is an incredibly important (if not underestimated) strength of programming.

You *can* use Hoare logic with weakest-precondition calculus to verify imperative programs, but it's incredibly tedious for anything but simple programs. On the other hand, it's essentially tied into the functional paradigm. Massive bonus really.

As worseisworser has said, concurrency is inherently tied into a (pure) functional language, and we're moving into a realm where concurrency is paramount really. One of my [lecturers]("http://www.cse.unsw.edu.au/~benl/") from a few years ago (who was a PhD student then, but he is now a research associate with UNSW) did a lot of work with Sun's (I guess they're Oracle's now) SPARCs, in particular porting GHC, but he had a lot of multi-core benchmarks which were incredibly impressive. If you're interested, check out his site, some very cool stuff there.

---

### Post by phrostbyte on 2010-09-18
The executive summary is that functional programs have the potential for better performance and reduced defects over imperative programs. I will justify this further.

There is two properties of functional programs that are important here:

* Functions with referential transparency
* Reentrent functions

As others have said but I will elaborate on, functional languages tend to encourage the development of reentrent code. A reentrent function can be run multiple times in parallel, allowing for automatic concurrency optimizations by the compiler.

Functions with referential transparency can further be automatically memorized (ie, the value of a function can be precomputed ahead of time).

The above two properties can improve an application performance, even when the realities of the underlying hardware change in a way not possible with totally imperative programs.

In general these properties also lend themselves to improved static analysis and the possibility of proving the correctness of a function by techniques like induction. These possibilities has the ability of reducing the defect count.

---

### Post by absolutezero1287 on 2010-09-19
> **worseisworser said:**
> An application for functional programming in the real world is that it allows one to deal with concurrency in a particular way that makes some things there a lot easier. This is real and increasingly so because we're now seeing 2, 4, 6, 8 and 12+++ core CPUs already here or here very soon (1-2 years from now).

I'm not sure what you mean by systems programming, but if/when you eventually need to communicate (state and I/O) with the outside world you can use things like transactions or STM: [http://en.wikipedia.org/wiki/Software_transactional_memory](http://en.wikipedia.org/wiki/Software_transactional_memory)

Some people think transactions and functional programming are in direct opposition with each other; this is wrong; they can complement each other.

edit:
I think Haskell has STM support built in, and Common Lisp has several STM libraries available; my very own SW-STM ( [http://github.com/lnostdal/SW-STM](http://github.com/lnostdal/SW-STM) ) for instance.

By systems programming I was referring to low-level programs like kernels and other aspects of operating system design.

This all seems very interesting. Thank you all for replying. I'm still somewhat green at programming but its my passion. In particular, I like the theoretical aspects of computer science.

---

