---
title: "Systematic way of finding a segfault?"
date: 2010-07-07
forum: Programming Talk
---

### Post by simeon87 on 2010-07-07
I was wondering if some of the more experienced C programmers could tell me what their approach is in finding a segfault. I'm rather new to C and I've got a C extension for my Python program in which I've introduced a segfault somehow... most of the time, it doesn't occur and I've yet to find what triggers it...

Debugging is no less significant than programming itself so I was wondering if there are general things to look for. How do I find in what part of the code the segfault is occurring, other than staring at each line of code?

---

### Post by StephenF on 2010-07-07
Try running with environment variable MALLOC_CHECK_ set. This mostly eliminates a class of faults to do with memory management.

Unit tests. Write a test routine to force the fault to occur. This is easy to do with a small module.

Lots and lots of printf statements e.g. ### 1, ### 2. These can pinpoint where the program ceased. Then add some more displaying the contents of structures, etc.

When all else fails, refactor your code. This can cause subtle bugs to come into focus.

---

### Post by nvteighen on 2010-07-07
> **simeon87 said:**
> I was wondering if some of the more experienced C programmers could tell me what their approach is in finding a segfault. I'm rather new to C and I've got a C extension for my Python program in which I've introduced a segfault somehow... most of the time, it doesn't occur and I've yet to find what triggers it...

Debugging is no less significant than programming itself so I was wondering if there are general things to look for. How do I find in what part of the code the segfault is occurring, other than staring at each line of code?

Using gdb...

---

### Post by simeon87 on 2010-07-07
> **StephenF said:**
> Try running with environment variable MALLOC_CHECK_ set. This mostly eliminates a class of faults to do with memory management.

Unit tests. Write a test routine to force the fault to occur. This is easy to do with a small module.

Lots and lots of printf statements e.g. ### 1, ### 2. These can pinpoint where the program ceased. Then add some more displaying the contents of structures, etc.

When all else fails, refactor your code. This can cause subtle bugs to come into focus.

Thanks both for the replies.

Let's try that. I tried the printf approach but it apparently happened after control had returned to the Python code... I have unit tests but not for the C code yet - let's work on that too :) I know that it was introduced in some recent modifications but clearly the code is not clear enough yet to make the bug stand out.

> **nvteighen said:**
> Using gdb...

Ah, cheers - I didn't even know that it existed - I'll read some tutorials on that.

---

### Post by MadCow108 on 2010-07-07
gdb of course.
It makes "printf debugging" obsolete and a waste of time.
Many in-development segfaults can be solved (or at least located) by doing:
gdb --args program
r
bt (= backtrace)
in a couple of seconds.

in some cases like memory corruption it can be tricky to find the source of error even with gdb
In that case use valgrind. It will tell you exactly where your corruption occured (+ lots of other useful stuff). Then you can use that information to pinpoint the source in gdb.

I always have my testcases run in valgrind (and _MALLOC_CHECK=2 _MALLOC_PERTURB=172). This notifies you of subtle problems very early on.

for debugging raceconditions you can use dtd or helgrind but unfortunately they give many false positives :/

---

### Post by DanielWaterworth on 2010-07-07
> **MadCow108 said:**
> gdb of course.
It makes "printf debugging" obsolete and a waste of time.

printfs can still be useful to track a programs flow, but gdb rocks.

---

### Post by Some Penguin on 2010-07-07
A significant problem with a printf() approach is that function calls involve writing new stack frames, and this can change the behavior that you're seeing.  gdb and similar debugging tools are somewhat less likely to have this problem (cases where you'll still have observer-changes-behavior problems include things dependent upon scheduling, for instance).

Unit test it, generate a core dump if need be, and yes, do backtraces.  And check your functions to make sure they check the sanity of their inputs and whatever functions they call.

---

### Post by dwhitney67 on 2010-07-07
> **Some Penguin said:**
> A significant problem with a printf() approach...
This is the approach I took 20 years ago when a debugger wasn't available.  It worked then, probably works just as good today.  Still, it is impossible to detect a memory overwrite using printf(), so it does have it's limitations.

Whenever someone is writing code that employs buffers, and perhaps functions similar to memcpy() and memset(), the simplest advice is to double- or triple-check the code to make sure it correct, and to never assume indexes/offsets into a buffer are correct.

---

### Post by Simian Man on 2010-07-07
Finding and fixing segfaults is seriously easy.  There are other problems that are much harder to diagnose and solve.  When you have values (seemingly) randomly changing in memory, you will wish for a simple segfault :).

BTW ddd is an easier to use alternative to gdb.

---

### Post by Zugzwang on 2010-07-07
I often find running "valgrind --tool=memcheck" on a segfaulting application to be the quickest way of finding the problem in about 90% of the cases as the information put out by it is often already sufficient for knowing immediately where the problem lies.

---

