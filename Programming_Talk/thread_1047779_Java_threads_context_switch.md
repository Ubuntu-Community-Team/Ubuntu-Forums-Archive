---
title: "Java threads context switch"
date: 2009-01-22
forum: Programming Talk
---

### Post by tashe on 2009-01-22
Hi
I have two threads,each from different class. In each of the thread's run method there is a while cycle. I've noticed that when a threads time finishes and the processor switches to the other thread, he does it almost always when the thread is in the middle of the while cycle.
Is it possible to make the context switch at the end of a iteration in the while loop? 
thank you

---

### Post by slavik on 2009-01-22
yes. sometimes compilers put in code in loops that once a while make a system call for house keeping.

---

### Post by myrtle1908 on 2009-01-22
I think you want the Thread.yield() method.  Basically it says end my time-slice prematurely, look around for other threads to run. If there is nothing better than me, continue.

Edit: By "better", I mean with a higher priority.

---

### Post by CptPicard on 2009-01-22
I haven't heard of any way to have absolute explicit control over this, but there is the "yield" method you could try calling at the end of your while block to signal that now would be a great time to give processor to the other thread.

---

### Post by myrtle1908 on 2009-01-22
Further to what has been said previously, the following is an interesting (short) read: [http://www.javamex.com/tutorials/threads/yield.shtml](http://www.javamex.com/tutorials/threads/yield.shtml), specifically the section regarding how linux deals with calls to yield().

---

### Post by tashe on 2009-01-22
First, thanks for the answers in such a short time
From what I can read, the CPU will give control to the other thread when called yield, but my bigger concern is how to be sure that when the time slice of the thread is finished, this same thread won't give up the CPU until the last line in the while loop, that is, the yield method.

---

### Post by slavik on 2009-01-22
you can't be certain. :) there are ways to sort of force this, but I am sure you don't need it at this point in your adventures ;)

but if you really want to know, we can always tell you :)

---

### Post by CptPicard on 2009-01-22
> **tashe said:**
> when the time slice of the thread is finished, this same thread won't give up the CPU until the last line in the while loop, that is, the yield method.

Welcome to the world of pre-emptive multitasking... you're not really allowed to do that. Priorities might help some, but if these are equal-priority threads, I am afraid you're probably SOL...

---

### Post by tashe on 2009-01-22
If you have the time, feel free :D
And if its not too complex,I'll probably try it on my project. ;)

---

### Post by slavik on 2009-01-22
basically, if you want to force a thread to run instead of other threads, create a global mutex and give it to the thread, then once it is done, it can release it and then you have to somehow decide who gets it next (free for all, round robin, etc.) :)

---

### Post by jespdj on 2009-01-23
You should not write multi-threaded programs in a way that depends on how the scheduler schedules your threads. There is no guarantee that your threads are scheduled in a particular order or with a particular timing. On a different operating system with a different implementation of Java it might work differently, or in a next version of Java on Ubuntu it might work differently. It might even work differently on another computer with a dual- or quad-core processor, running the same version of Ubuntu and Java as you.

If you need to coordinate how threads work together, you should use some thread synchronization method. Java has the **synchronized** keyword, and for more sophisticated thread synchronization mechanisms use classes from the package **java.util.concurrent**.

---

