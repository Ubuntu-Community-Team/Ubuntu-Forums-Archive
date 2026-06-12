---
title: "Is Compiling Deterministic?"
date: 2008-06-25
forum: Programming Talk
---

### Post by kripkenstein on 2008-06-25
What I mean is, if I do 'make' on the exact same source files, should I end up with exactly the same output file?

The reason I ask is I have computer that's behaving a little 'odd'. I can't put my finger on it though (memtest is ok, no bad sectors). So I just compiled a large software project (Ogre 3D) twice, and compared the resulting shared library. In fact the two outputs are **not** identical, they are a few bytes different in size.

Is it possible that some part of the 'make' process (compilation, linking) can make non-deterministic decisions? For example, change the name of some internal symbol (but keep it consistent everywhere, of course, so things still run)?

---

### Post by CptPicard on 2008-06-25
Yes, it is. In particular when it comes to the behaviour of the code :) (To suggest otherwise borders on ludicrous IMO)...

---

### Post by sonofusion82 on 2008-06-25
yes, it should be deterministic.
but for many large projects, there may be some build scripts that may auto generate/modify some identifier strings such as build version/number or build time.

---

### Post by kripkenstein on 2008-06-25
> **sonofusion82 said:**
> yes, it should be deterministic.
but for many large projects, there may be some build scripts that may auto generate/modify some identifier strings such as build version/number or build time.

Yeah, that's what I suspected, perhaps a timestamp gets inserted somehow into the symbols, or something like that... a complex build script might do that I guess.

So I can't conclude that my machine is faulty, according to this fact (that I get different outputs from building Ogre), I guess.

---

### Post by _sphinx_ on 2008-06-25
It can also happen if there are many threads in a project that are not synchronized, and also if they depend on each other. I this case also building can give different results.

---

### Post by kripkenstein on 2008-06-25
> **_sphinx_ said:**
> It can also happen if there are many threads in a project that are not synchronized, and also if they depend on each other. I this case also building can give different results.

Interesting, thanks. That makes sense.

---

### Post by henchman on 2008-06-25
So just compile a program of your own where you know that there are no strange threads and / or makefiles :)

---

### Post by kripkenstein on 2008-06-25
> **henchman said:**
> So just compile a program of your own where you know that there are no strange threads and / or makefiles :)

I thought about that, but what was good about Ogre was it was a **huge** project, so I got a 50 MB file at the end, and more chance for a hardware error to show itself.

Hmm, but I guess I can compile 'hello world' lots of times...

---

### Post by henchman on 2008-06-25
after a little googling, if found the following:

[http://www.pcworld.com/downloads/file/fid,7146-order,1-page,1-c,systemresourcestuneup/description.html](http://www.pcworld.com/downloads/file/fid,7146-order,1-page,1-c,systemresourcestuneup/description.html)

it stress-checks (not only) your cpu for errors... sorry its only for windows, but maybe you have windows installed or try it with wine or find an alike program for linux :)

---

### Post by kripkenstein on 2008-06-25
> **henchman said:**
> after a little googling, if found the following:

[http://www.pcworld.com/downloads/file/fid,7146-order,1-page,1-c,systemresourcestuneup/description.html](http://www.pcworld.com/downloads/file/fid,7146-order,1-page,1-c,systemresourcestuneup/description.html)

it stress-checks (not only) your cpu for errors... sorry its only for windows, but maybe you have windows installed or try it with wine or find an alike program for linux :)

Thanks. Actually there is a similar program for Linux (and also Windows) called 'cpuburn', it's in the repos.

I ran it overnight, it didn't give any errors, so that's encouraging at least.

---

### Post by henchman on 2008-06-25
if you have a dual core, perhaps you should run 2 instances of it parralel if it's not programmed ( and what i've quickly seen on their homepage it isn't ). perhaps iam wrong and you don't need to do so, but imho if you run only one instance then perhaps only one core is tested

---

### Post by kripkenstein on 2008-06-25
> **henchman said:**
> if you have a dual core, perhaps you should run 2 instances of it parralel if it's not programmed ( and what i've quickly seen on their homepage it isn't ). perhaps iam wrong and you don't need to do so, but imho if you run only one instance then perhaps only one core is tested

Yeah, to test both cores with something like cpuburn you need to run 2 instances of it, I tried that.

---

### Post by Zugzwang on 2008-06-25
> **_sphinx_ said:**
> It can also happen if there are many threads in a project that are not synchronized, and also if they depend on each other. I this case also building can give different results.

Why should that be the case? We are talking about the build process, not the execution of the program.

@OP: As a simple example, the following program always compiles to something different:
[PHP]
#include <iostream>

int main() {
	std::cout << "Compilation date/time: " << __DATE__ << ", " << __TIME__ << std::endl;
}
[/PHP]
You can compile it using "g++ test.cpp -o test" (if you stored it as test.cpp).

---

### Post by _sphinx_ on 2008-06-25
> **Zugzwang said:**
> Why should that be the case? We are talking about the build process, not the execution of the program.

Ah, I didn't payed attention to that think. Yes the executables would be same, but the result after execution would be different. Thanks for correcting me.

---

### Post by kripkenstein on 2008-06-25
Well in theory the build process itself might be multi-threaded, so that might mix things up, perhaps?

---

### Post by Zugzwang on 2008-06-25
> **kripkenstein said:**
> Well in theory the build process itself might be multi-threaded, so that might mix things up, perhaps?

Well, only in theory. Parallel building processes normally compile the individual source files separately in parallel and then the linker runs without any parallelism. There are no race conditions here.

If we are speaking of theory: Some optimizations by the compiler might be done in a randomized manner, too (for example, the optimization of register allocation might be done in a randomized way since this is a [NP-hard problem]("http://en.wikipedia.org/wiki/Register_allocation")). In practice, I don't think that any common compiler behaves in such a way.

---

### Post by _sphinx_ on 2008-06-25
@ Zugzwang
+1

---

