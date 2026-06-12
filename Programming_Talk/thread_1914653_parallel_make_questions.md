---
title: "parallel make questions"
date: 2012-01-24
forum: Programming Talk
---

### Post by PGScooter on 2012-01-24
In order to perform a parallel make, I've learned that after doing
./configure
I can do
make -j2
instead of
make
Can I always do a parallel make? Specifically, does it depend on the source code or is make always able to do a parallel big?

Also, is it safer to do a non-parallel make?

I have two CPUs. Is there ever any reason to do, say,
make -j3
?

Thank you!

---

### Post by 3Miro on 2012-01-24
Usually a project consists of a large number of small files that can be compiled completely independently, this make -jX is pretty useful. I am using -j6 and -j8 on my Desktop and Laptop respectively (Phenom X6 and i7 4+4 cores), although the "rule of thumb" estimate was that you should use one more than the number of your cores. On a dual core CPU -j2 and -j3 should be fine.

Doing a parallel make is no more "dangerous" than a regular make, in the sense that the executable generated is EXACTLY the same. However, depending on the make file, some parallel make commands may fail to compile. Actually, I have seen this only once and then the problem was that make did not only compile, but it also ran some tests to make sure the compiled libraries were stable. Then parallel make was failing, since the test stage wasn't synced with the build stage and make was trying to do the tests before it had the libraries.

Basically, do make -jX where X is the number of cores or one more. If make -jX fails, then you can try a regular make. Bottom line is that if it compiles, then it shouldn't matter whether you used -j or not.

---

### Post by hwttdz on 2012-01-24
> Can I always do a parallel make? 
Make is its own program, and always accepts the -j option.  So yes, but with qualification.

> Specifically, does it depend on the source code or is make always able to do a parallel big(build?)?
I can't think of a case where it depends on the source.  It does however depend hugely on the makefile.  If there is only one make job running having all the dependencies covered is a hidden bug as know the order things are going to be hit in.

> Also, is it safer to do a non-parallel make?
Related to the previous question, if the makefile is correct then no file will start to compile until its necessary dependencies are made. If the makefile is incorrect you'll get some "undefined symbol" errors or something.  Running make repeatedly might get to the end, but if there is a mistake in the makefile I'd just do "make -j 1" (or without any -j flag).

> I have two CPUs. Is there ever any reason to do, say,
make -j3?
Timings for a program I happen to have sitting around (I'm on a core2quad, 4 cores):
command, real time, user time
-j 1: 5:27, 4:38
-j 2: 2:53, 4:40
-j 3: 2:04, 4:47
-j 4: 1:42, 4:53
-j 5: 1:39, 4:52
-j 6: 1:40, 4:54
-j 12: 1:52, 4:56 - system starts thrashing
-j 24: 1:44, 4:57 - no thrashing
-j 36: 1:41, 4:57 - no thrashing
The absolute speedups and whatnot will depend on the actual layout of dependencies in the program.  For instance in this one there are a few files that are needed before much else can be done, so at some point it's not unlikely to be waiting for those, this also limits the maximum number of jobs running at any point (which is probably the only thing saving me from thrashing successively worse every time I increase the number of jobs).  I'd go for the number of cores you have, as you're not going to do appreciably better than that and you risk running out of memory as you increase above that.

> Thank you!
No problem.

>Addressing: "Doing a parallel make is no more "dangerous" than a regular make, in the sense that the executable generated is EXACTLY the same. However, depending on the make file, some parallel make commands may fail to compile. Actually, I have seen this only once and then the problem was that make did not only compile, but it also ran some tests to make sure the compiled libraries were stable. Then parallel make was failing, since the test stage wasn't synced with the build stage and make was trying to do the tests before it had the libraries."

It should have actually been possible to make the test rule depend on the compiled libraries, in which case make would have waited for them.  So this is an example of a hidden bug in a makefile which only becomes apparent if make -j is used (or if one deletes the library and then does "make tests" or whatnot.

---

### Post by 3Miro on 2012-01-24
> **hwttdz said:**
> 
>Addressing: "Doing a parallel make is no more "dangerous" than a regular make, in the sense that the executable generated is EXACTLY the same. However, depending on the make file, some parallel make commands may fail to compile. Actually, I have seen this only once and then the problem was that make did not only compile, but it also ran some tests to make sure the compiled libraries were stable. Then parallel make was failing, since the test stage wasn't synced with the build stage and make was trying to do the tests before it had the libraries."

It should have actually been possible to make the test rule depend on the compiled libraries, in which case make would have waited for them.  So this is an example of a hidden bug in a makefile which only becomes apparent if make -j is used (or if one deletes the library and then does "make tests" or whatnot.

True, but I got the Makefile (and the whole code) from somewhere else and I didn't want to mess with it. Theoretically, if the person creating the Makefile is thinking about parallel build, then all make -jX commands should run flawlessly. In practice, it is sometimes hit and miss, but the bottom line is that the final library or executable will be identical regardless of whether -jX option was used or not.

---

### Post by PGScooter on 2012-01-25
Great, thanks a lot guys for not only answers but explanations! I got more than I bargained for. I will do some of my own tests, specifically of -j2 versus -j3 to see which is faster most of the time. I don't expect much of a difference, but it's fun to pretend like it matters :). I'll post back if I find anything interesting.

---

