---
title: "Optimizing my Makefile"
date: 2011-04-09
forum: Programming Talk
---

### Post by DBQ on 2011-04-09
Hi everybody.

I got a question.  Basically, I am using the "make" program to build my C++ program.

I basically first create many object files e.g. file1.o file2.o etc.

I then link the files together using g++ file1.o file1.o ... -o prog.  This operation takes a long time and is not sped up by using multiple threads e.g. make -j4.  

Is there a way I can restructure my makefile in order to make the compilation faster?  Thank You!

---

### Post by MadCow108 on 2011-04-09
linking is often a bottleneck during compilation as available linux linkers to not support incremental linking.
Thus there is nothing you can do about it besides changing linker.

ld is a terribly slow linker
consider using gold, it is up to 5 times faster.

```

ld.gold --version
GNU gold (GNU Binutils for Ubuntu 2.21.0.20110327) 1.11

#replace ld on whole system
apt-get install binutils-gold
ld --version
GNU gold (GNU Binutils for Ubuntu 2.21.0.20110327) 1.11
```

---

### Post by DBQ on 2011-04-09
Thank you so much!  Are there any compatibility considerations to be aware of?

---

### Post by DBQ on 2011-04-09
I installed gold, but do not see much difference.  Is there some setting I need to tweak?

---

### Post by DBQ on 2011-04-09
I am still hoping there is a way to restructure the Makefile -- the linking is so slow each time...

---

### Post by Arndt on 2011-04-09
> **DBQ said:**
> I am still hoping there is a way to restructure the Makefile -- the linking is so slow each time...

How long does it take?

I'm not doubting you, but I can't recall finding the linking step to be so much of a bottleneck to disturb me.

---

### Post by DBQ on 2011-04-09
It takes around 10-15 seconds...while compilation is generally fast i.e. like 3 seconds when done with multiple threads.

---

### Post by JupiterV2 on 2011-04-11
Is it the linking that's the issue or the speed at which your makefile is processed? If you do the linking manually, rather than via a makefile, does it take the same, less or more time? If it's the processing of the makefile then you'd need to show us the code in order to suggest improvements. For example, if your project is using GNU autotools then you can drastically increase building and linking your program by using non-recursive make. Heck, even if you're NOT using autotools but you are using recursive make, you can gain a major speed increase by using a non-recursive method.

If, however, its just the linking itself, I'm not sure what else you can do other than using a faster linker as already suggested.

Maybe you need to explain, or show example code, as to why you think the Makefile is the problem.

I have a fairly low-end machine by today's standards and it can compile and link my project, of about 30 files, in a very reasonable amount of time. I haven't timed it but I can't see the whole process taking more than about 10-15 seconds in total, and that includes linking glib/GTK+ libraries.

---

