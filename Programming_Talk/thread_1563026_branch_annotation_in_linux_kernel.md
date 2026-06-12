---
title: "branch annotation in linux kernel"
date: 2010-08-28
forum: Programming Talk
---

### Post by jamesbon on 2010-08-28
Hi,before asking this question I had googled
[http://www.google.co.in/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=branch+annotation](http://www.google.co.in/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=branch+annotation)
 but no useful thing came in my search results.
I want to know the concept of Branch Annotation with respect to Linux Kernel use of likely() and unlikely().
I am not clear with what should I search for this.

---

### Post by MadCow108 on 2010-08-28
the kernels un/likely annotations are just macros for gcc's __builtin_expect
[http://gcc.gnu.org/onlinedocs/gcc-4.1.2/gcc/Other-Builtins.html](http://gcc.gnu.org/onlinedocs/gcc-4.1.2/gcc/Other-Builtins.html)

here's a simple example of its affect on the assembler code:
[http://kerneltrap.org/node/4705](http://kerneltrap.org/node/4705)

but its effect is negible on modern x86 cpus due to their builtin branch prediction and very low branching costs.
But on machines with high branch costs or some very tight loop with unavoidable branch it can be useful

---

### Post by tapas_mishra on 2010-08-28
You need to understand following terms
pipelined instructions
branch prediction
5 stage pipeline
speculative instruction execution (conside it wont write any thing in memory)
pipeline flush (if prediction is wrong) 
Also check these links
[http://en.wikipedia.org/wiki/Speculative_execution](http://en.wikipedia.org/wiki/Speculative_execution)
[http://en.wikipedia.org/wiki/Instruction_pipeline](http://en.wikipedia.org/wiki/Instruction_pipeline)

---

