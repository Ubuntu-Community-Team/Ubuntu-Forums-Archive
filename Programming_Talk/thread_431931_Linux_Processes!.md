---
title: "Linux Processes!"
date: 2007-05-03
forum: Programming Talk
---

### Post by scottious on 2007-05-03
Hey folks, I'm kinda new so bear with me if this post is not in the right forum.

So I'm looking into learning about how Linux processes work and how memory is managed in the Linux kernel and I was wondering what resources there were available online or books that I can read about this.  I understand this is a loaded question so I totally don't expect all of the answers to my questions on this forum, but I figure if anybody knows where to find resources about this kind of stuff, the ubuntu forums would.  The kind of stuff I'm looking to learn include:

1.  how a new process is created and run
2.  how the kernel manages running multiple processes
3.  how context switches work
4.  threads vs. processes and the advantages/disadvantages of each
5.  where in memory the kernel is and how the kernel protects parts of the memory
6.  how does virtual memory fit into all of this?
7.  how does a process's memory space grow/shrink
8.  how is a process's memory space divided up (code, stack, heap, etc)

Again, if anybody has links to web pages or books to recommend, that would be much appreciated!

---

### Post by leg on 2007-05-03
Start with [this]("http://www.tldp.org/LDP/lki/index.html") and then try looking around the rest of the documentation there.

---

### Post by Blacktalon on 2007-05-03
I would also suggest that you go to the Absolute Beginners from the forums home page.  And read some of those posts..they can help you understand a bit better.

:)  Good luck,
~BT

---

### Post by psusi on 2007-05-03
You might want to read this:

[http://www.amazon.com/Art-UNIX-Programming-Eric-Raymond/dp/0131429019/ref=pd_bbs_sr_1/103-6683617-5259045?ie=UTF8&s=books&qid=1178221747&sr=8-1](http://www.amazon.com/Art-UNIX-Programming-Eric-Raymond/dp/0131429019/ref=pd_bbs_sr_1/103-6683617-5259045?ie=UTF8&s=books&qid=1178221747&sr=8-1)

---

### Post by slavik on 2007-05-04
in Linux, there are no processes ... there are no threads either. There are 'tasks'.

Reason this is so, is because if a process is split into 2 threads, those threads would normally be sharing the same CPU (the one that runs the process), in Linux, the two threads can actually migrate between CPUs :)

easiest way of creating processes:
fork() then exec() (look around for a thread I made about it, explains it in much more detail).

also, look up stack smashing protection (neat stuff)

for the code, stack, heap stuff, find an assebly book :)

---

### Post by psusi on 2007-05-04
> **slavik said:**
> in Linux, there are no processes ... there are no threads either. There are 'tasks'.

Reason this is so, is because if a process is split into 2 threads, those threads would normally be sharing the same CPU (the one that runs the process), in Linux, the two threads can actually migrate between CPUs :)


Task is a good generic term for a thread or a process, but to say there is no longer such a thing as a process is false.  It is still true that you get a new process after a fork().  

Also no threaded OS that I know of can't run each thread on its own cpu.  Threads are simply processes which share the same memory space and other resources.

---

### Post by winch on 2007-05-04
Try this book, [Understanding the Linux Kernel]("http://www.oreilly.com/catalog/understandlk/").

---

### Post by public_void on 2007-05-04
[Advanced Linux Programming]("http://www.advancedlinuxprogramming.com/alp-folder") is a programming book, however it does have a good explanation of threads and processes.

---

