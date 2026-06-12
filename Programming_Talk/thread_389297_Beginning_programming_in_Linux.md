---
title: "Beginning programming in Linux"
date: 2007-03-20
forum: Programming Talk
---

### Post by Polbit on 2007-03-20
I have decided that I want to start playing with programming in Linux. I am not new to programming in general, having used C, C++, Java, and assembler in the past on Amiga and Windows.

What I want to find is a good, solid, and in-depth introduction to Linux from a programming perspective. Is there one or two books that are recommended over others, or some good on-line texts? It is so hard to start when there is just so much information out there...

Thanks!

---

### Post by pmasiar on 2007-03-20
> **Polbit said:**
> I have decided that I want to start playing with programming in Linux.(...)a good, solid, and in-depth introduction to Linux from a programming perspective. 

Programming what? Kernel? Drivers? Communication software? websites? GUI apps? Games? Ubuntu Packages? Crossplatform?

If you want to contribute to Ubuntu, most original work is done in Python. OLPC uses also Python for it's cool laptop project.

---

### Post by Polbit on 2007-03-20
Programming in general. I just want to learn overall Linux programming, the system architecture, etc., for now. Not looking into anything specific.

---

### Post by Tomosaur on 2007-03-20
> **Polbit said:**
> Programming in general. I just want to learn overall Linux programming, the system architecture, etc., for now. Not looking into anything specific.

It's all pretty much the same regardless of platform. To get started, open up a terminal and type:

```

sudo aptitude install build-essential

```

This will download and install the necessary stuff to 'get started'.

The python interpretor is already installed. For an introduction to Python, check [here](http://www.python.org/). Python programs are platform independent, so there's no difference between code for Windows and code for Linux. That site should explain everything you need to know anyway.

For C/C++ - you won't see any API similar to Win32. You will need to know what your program needs. If you want to check out which libraries and such are immediately available to you, just open Synaptic Package Manager and check in the 'Development' sections. The standard compilers are gcc for C, and g++ for C++.

If you want to read documentation about something, open up a terminal and type:
```

man <command>

```

So if you want to read about gcc, for example, type:
```

man gcc

```

Or you can just search on the web.

Try [This page](http://www.techbooksforfree.com/linux.shtml) for some ebooks on Linux programming.

Or alternatively you could take it slow, and learn all about shell scripting first. The Linux shell is very powerful, so it's a good skill to have. [Check this site for more info](http://tldp.org/LDP/abs/html/).

---

### Post by slavik on 2007-03-21
write your own 'ls -l'

write an ls that takes arguments (via getopt)

write multi-process code

write multi-threaded code

that is what I have been doing so far ...

---

### Post by rplantz on 2007-03-21
I suggest you take a look at "Beginning Linux Programming, 3rd edition" by Stones, Matthew, and Cox. I used the 2nd edition in a class I taught several years ago. I think it's pretty good for self-teaching. The fact that there is a 3rd edition is a good sign. It's only $26.39 on Amazon.

---

### Post by wkulecz on 2007-03-21
+1 to the "Beginning Linux Programming" book recommendation.  

It pretty much assumes you know programming but not the specifics of Unix/Linux.

"Advanced Linux Programming" by Mark Mitchell, Jeffery Oldham, and Alex Samuel is a useful addition if you need to use mmapped files or pthreads.

--wally.

---

### Post by Polbit on 2007-03-22
Thanks guys, I will definitely give the book a try, looks like it has good reviews.

---

