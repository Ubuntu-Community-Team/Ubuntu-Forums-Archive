---
title: "Testing page swapping algorithms"
date: 2008-01-02
forum: Programming Talk
---

### Post by EricDallal on 2008-01-02
Hello,

I'm a graduate student currently looking at a number of possibilities for my project. One of the possibilities that my supervisor suggested was trying to test various algorithms for reducing page faults, or trying to apply a reinforcement learning approach to the problem. In order to do this, I assume I would need access to the operating system (I won' be doing this on my computer). I have taken a course in operating systems but I have never done anything like this. Does anybody know what would be involved in trying out different algorithms for reducing page faults?

A few more specific questions:

Is there a way to simulate an algorithm without actually entering an operating system? If so, is there some standard test suite that could be run as a test? I know that such things exist for branch predictors, since I've already done a project on those. Ignore the following questions if there is a way to simulate the effect of page swapping algorithms without going into the operating system.

Is there some file or set of files (I am looking for both source code and the location of the object code) containing the algorithm for page swapping? If so, does anyone know where it/they is/are?

Would it be possible to change this part of the operating system without having to recompile the whole system?

Thanks in advance for any answers to any of these questions.

Eric

---

### Post by CptPicard on 2008-01-02
My immediate concern about using reinforcement learning with page faults is the fact that the OS tries to layer stuff so that there is as little information about other layers as possible in each any given layer. As you know, swapping algorithms mostly just rely on the assumption that what hasn't been touched for a while is not going to be touched next.

What do you intend to be learning from? Just the facts available to normal swapping algorithms and the current usage pattern? I'm afraid you will have a hard time being competitive with machine learning in that environment, and in order for you to be able to touch some interesting stuff, you'll have to hack your way through the OS layers, which is potentially painful.

If you have no experience with for example the Linux kernel, getting familiar with it might be more work than you want to do... depending on you, of course. My course of action might be to code some logging statements into strategic points in the kernel, produce datasets for training and then simulate using those. Of course if this is supposed to be online reinforcement learning that discovers as it goes, your algorithm's behaviour would be influencing the future contents of this log... 

Switching the algorithms and dumping data out of them should be doable as well... but, in a live system, it will be an interesting exercise to produce situations that are similar enough for you to actually see the difference in performance :)

---

### Post by slavik on 2008-01-03
just write some kind of a simulator and something that issues signals to it on which page to swap into memory (could be random or some kind of other pattern).

no need to hack the kernel for this.

---

### Post by CptPicard on 2008-01-03
The whole problem is the learning part. If you have a simulator, it will just learn whichever way you coded your simulator to work. If it produces some pattern, it might learn it, but there is no saying that a real-world OS actually produces a similar pattern... and if you already know enough of the way the page requests come in, you'd probably already have a hard-coded algorithm for it and no need to learn :)

---

### Post by amo-ej1 on 2008-01-03
What is wrong  with entering and operating system ? The most 'real' life test you could do is simple look at the way page faults are handled in  you favorite open source kernel. 


In the linux code when you look at include/linux/mm.h you'll find all prototypes you need and the mm directory in the source route is also the place that deservers a look (which contains the memory manager). 


Google for example was kind enough the share the following links:

[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=260](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=260)
[http://www.linux-security.cn/ebooks/ulk3-html/0596005652/understandlk-CHP-9.html](http://www.linux-security.cn/ebooks/ulk3-html/0596005652/understandlk-CHP-9.html)
(especially section 9.4)  
[http://www.linux-security.cn/ebooks/ulk3-html/0596005652/understandlk-CHP-9-SECT-4.html](http://www.linux-security.cn/ebooks/ulk3-html/0596005652/understandlk-CHP-9-SECT-4.html)

---

