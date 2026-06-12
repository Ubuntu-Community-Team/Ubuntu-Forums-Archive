---
title: "Cost of fork() function???"
date: 2009-10-31
forum: Programming Talk
---

### Post by RichardUK on 2009-10-31
It seems it is standard practice when one wants to run an external tool is to fork a process then call exec. But I'm a little worried about it's cost on resources. What if I have a complicated 3D studio application that has a lot of ram allocated, say over 2gigs of it. At the end of a render that app wants to execute the resulting file that is a self playing video file. When you fork is the system really going to duplicate my uber resource hungry app???

The reason I ask is that I have a tool that reads a file and from that manages a large number of other tools. The tool has many threads to then process the output of the external tools. This takes quite a few resources up and so having the system constantly duplicating the application just to run another one seems very wasteful.

Can you put my mind at rest?

P.s. been looking at the kernel code and does seem to do a lot. But some of it I get lost so I may have miss understood.

---

### Post by ENOTTY on 2009-10-31
Short answer: It won't duplicate the 2 GB of memory.

Long answer: It depends on how the operating system has implemented fork(). There is some overhead for process creation, but the most expensive part, as you identified correctly, would be duplicating the program's referenced memory.

Most (if not all) modern operating systems use copy on write (COW), which does not duplicate most of the 2 GB of memory when fork() is run, but the OS might duplicate memory later during execution of either the parent or child process.

Think about what the process wants when it is doing a read or a write. Lets say after the fork, the memory is only read. So the memory stays the same for the rest of the life of the processes. So what's the point of duplicating the memory? However, if there is a write, then the memory has diverged. The parent process expects the memory to look like one thing, and the child process expects the memory to look like another thing. So we need to duplicate the memory.

Copy on write is an algorithm that encapsulates the above usage. On fork(), both the parent and child process reference the same physical memory, so reads are reading from the same physical place. But when either process attempts to write to the memory, the OS will duplicate* the memory, update the references in each process, and then run the writing instruction again.

*On x86 and x86_64 (not sure how other architectures work), duplication really only happens in sizes of physical frames, so it won't duplicate all 2GB, but instead it will duplicate the 4KB section** that contained the memory address that you tried to write to. If you want more info on this, the term virtual memory paging is the thing you want to look up.

**4 KB if you're using small pages, which most people are. I forget how big the big pages mode is, and I forget the real terminology for it.

Check out:
[http://en.wikipedia.org/wiki/Copy-on-write](http://en.wikipedia.org/wiki/Copy-on-write)
[https://secure.wikimedia.org/wikipedia/en/wiki/Paging](https://secure.wikimedia.org/wikipedia/en/wiki/Paging)

---

### Post by slavik on 2009-10-31
to extend this:

Before, it used to be that fork() would copy all the memory. Then vfork() was created which would not copy memory and was used mostly by shells (since they fork any command you ask them to do).

Nowadays though, Linux kernel combines the two and only gives fork() which as ENOTTY has mentioned does COW (copy on write).

for any kernel, always install the syscall manpages and man -s 2 fork for accurate info.

---

### Post by Can+~ on 2009-10-31
> **RichardUK said:**
> The reason I ask is that I have a tool that reads a file and from that manages a large number of other tools. **The tool has many threads** to then process the output of the external tools. This takes quite a few resources up and so having the system constantly duplicating the application just to run another one seems very wasteful.

Can you put my mind at rest?

P.s. been looking at the kernel code and does seem to do a lot. But some of it I get lost so I may have miss understood.

Then why not just add another thread instead of forking?

---

### Post by wmcbrine on 2009-10-31
fork() has been highly optimized in Linux, as in *nix generally, and is safer and easier to use than threads. It's much less overhead than process creation in Windows. Don't fear it.

---

### Post by slavik on 2009-10-31
> **wmcbrine said:**
> fork() has been highly optimized in Linux, as in *nix generally, and is safer and easier to use than threads. It's much less overhead than process creation in Windows. Don't fear it.
have you ever written multithreaded/multiprocess programs?

---

### Post by wmcbrine on 2009-11-01
Yes...

---

### Post by terry_a_g on 2009-11-01
> **wmcbrine said:**
> fork() has been highly optimized in Linux, as in *nix generally, and is safer and easier to use than threads. It's much less overhead than process creation in Windows. Don't fear it.
Unless you're on Solaris.  fork() there is as slow as molasses.

---

### Post by RichardUK on 2009-11-02
Thanks for the very indepth info, I did wonder if it did something like that. 

I would have thought it would have been simpler to create a function in the ilk of exec functions but creates a new process instead of replacing the current one.

---

### Post by grayrainbow on 2009-11-02
Generaly speaking maybe the biggest coast of fork/exec nowadays is communication. Thread communication is much less expensive than inter process chat. On the other hand, bug in child process is unlikly to crash its parent.

---

### Post by Arndt on 2009-11-02
> **grayrainbow said:**
> Generaly speaking maybe the biggest coast of fork/exec nowadays is communication. Thread communication is much less expensive than inter process chat. On the other hand, bug in child process is unlikly to crash its parent.

If you want a programming language with very fast thread spawning and communication, try Erlang.

---

