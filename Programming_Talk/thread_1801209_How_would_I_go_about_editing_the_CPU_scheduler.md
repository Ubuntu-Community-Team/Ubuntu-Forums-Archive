---
title: "How would I go about editing the CPU scheduler?"
date: 2011-07-10
forum: Programming Talk
---

### Post by gingerkid101 on 2011-07-10
How would I go about editing the CPU scheduler in Linux/Ubuntu? Would I have to edit/recompile the kernel, or is there another file which contains the CPU scheduling algorithm? In any case, I'm taking a class on Operating Systems, and I'm curious to get my hands on the code and see for myself what kind of changes I can make.  Thanks in advance for your help!

(I am specifically interested in the mid-term scheduler, but if somebody could lead me in the right direction, I'd appreciate it.)

-Chris

---

### Post by Elfy on 2011-07-10
Thread moved to Programming Talk.

---

### Post by TwoEars on 2011-07-10
I recommend reading O'Reilly's "Understanding the Linux Kernel", it's a good read. "Linux Kernel Development" by Robert Love is also fairly decent on the topic. They'll teach you much better than anyone on here could. Kernel development is a big undertaking, and you can't leap into it without first knowing everything you need to know (otherwise, you get PP code and that's never good).

---

### Post by gingerkid101 on 2011-07-10
Thanks for the suggestions. I have a basic understanding of how operating systems work with processes and schedule them. I was just really interested in seeing the actual code for myself.

---

### Post by slavik on 2011-07-11
> **gingerkid101 said:**
> Thanks for the suggestions. I have a basic understanding of how operating systems work with processes and schedule them. I was just really interested in seeing the actual code for myself.
get the linux source code (kernel.org is a start, there are also source packages for the one ubuntu uses).

---

### Post by TwoEars on 2011-07-11
> **gingerkid101 said:**
> Thanks for the suggestions. I have a basic understanding of how operating systems work with processes and schedule them. I was just really interested in seeing the actual code for myself.

Again, reading those books will give you a much better overview and a better idea on what you need to edit to get what you want. Jumping into the source code will probably leave you lost and confused (don't take this as a dig at you - the same would apply to anyone asking this question)

---

### Post by gingerkid101 on 2011-07-11
> **TwoEars said:**
> Again, reading those books will give you a much better overview and a better idea on what you need to edit to get what you want. Jumping into the source code will probably leave you lost and confused (don't take this as a dig at you - the same would apply to anyone asking this question)

Yeah, after seeing it, I see what you mean. I will look into those books when I have some spare time. I'm doing a research paper on cpu scheduling. This thing may be the end of me haha. Thanks for your help again.

---

