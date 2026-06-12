---
title: "Parallel build with make"
date: 2010-03-10
forum: Packaging and Compiling Programs
---

### Post by DuXati on 2010-03-10
Hi all,

I'm trying a parallel build with the "make" command on a quadcore by using "make ... -j4". In top I can see that multiple processes are created but the CPU never reaches more than 25%, while the point of a parallel build is using 100%.

How is this possible? Should I install multi-core support or something like that?

I'm using Ubuntu 9.10 on a x86 64bit Intel quadcore with 4GB RAM.

Thanks in advance,

DuXati

---

### Post by Choragos on 2010-03-10
What are you using to program in parallel?  I'm not familiar with the -j4 flag.  If you're using MPI, you need a different compiler, but openmp will work with the standard compiler.

---

### Post by MadCow108 on 2010-03-10
what are you trying to compile?
probably the makefile is written correctly for parallel build or one of your components (like harddisk) is slowing things down

---

### Post by DuXati on 2010-03-10
Hi guys,

I'm trying to compile Firefox for my master's thesis. 

I've installed g++ to compile, I suppose make uses this to compile the C++ code? I'm not actually trying to program in parallel, only to compile in parrallel to speed up the process. I've got four cores, it would be nice being able to use them too ;)

DuXati

---

### Post by MadCow108 on 2010-03-10
have you read the section on parallel build here:
[https://developer.mozilla.org/en/Mozilla_Build_FAQ](https://developer.mozilla.org/en/Mozilla_Build_FAQ)

especially
> 
Note that you have to add the -j option to your .mozconfig file like this:
mk_add_options MOZ_MAKE_FLAGS=-jN


---

### Post by Choragos on 2010-03-10
Oh, I see--I misunderstood.  You're trying to compile in parallel, not compile Firefox to run in parallel.

---

### Post by DuXati on 2010-03-11
MadCow108: doh... Read it up to "Parallel building with -j4 and -j8 seems to work well." A RTFM problem all along :)

Thank you very much, both of you!

---

