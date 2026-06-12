---
title: "So if I wanted to try and make my own operating system how would I go about it??"
date: 2007-02-01
forum: Other OS Talk
---

### Post by presbp on 2007-02-01
What if I was to try and make my own operating system.  I am not talking about a clone of Windows or Mac OS X or another Linux distribution.  What if I wanted to completely try and make my own operating system without stealing ideas from windows mac os's or linux distributions.  **Could I do it, and where would you say would be the best place for me to start?**

I think it would be really cool to make a Linux distribution but I was thinking wouldn't it be even cooler to try and make my own operating system?

---

### Post by pay on 2007-02-01
If you have to ask then you're not ready to write your own operating system from scratch. You could try either the Gentoo handbook and install Gentoo from scratch or use Linux From Scratch to compile your own linux distro. Either way you'll learn ALOT about Linux.

If you wanted to write your own, I suggest doing a Software Engineering Course at Uni.

---

### Post by mips on 2007-02-01
If you are asking then you are not ready as pay said.

You should know:
1. C & Assembly language
2. Understand hardware operation
3. Understand Kernel & OS designs, the pros & cons of different designs etc.

You can start reading up on the topic:
[http://cdsmith.twu.net/professional/osdesign.html](http://cdsmith.twu.net/professional/osdesign.html)
[http://www.cs.purdue.edu/homes/dec/osbooks.html](http://www.cs.purdue.edu/homes/dec/osbooks.html)
[http://flinflon.brandonu.ca/dueck/KModel/kernelclasses.htm](http://flinflon.brandonu.ca/dueck/KModel/kernelclasses.htm)
[http://freshmeat.net/articles/view/237/](http://freshmeat.net/articles/view/237/)
[http://www.gnu.org/software/hurd/hurd-paper.html](http://www.gnu.org/software/hurd/hurd-paper.html)
[http://www.eros-os.org/design-notes/00DesignNotes.html](http://www.eros-os.org/design-notes/00DesignNotes.html)
[http://i30www.ira.uka.de/index.php?lid=en](http://i30www.ira.uka.de/index.php?lid=en)

Many more available via google & a bookstore

---

### Post by SunnyRabbiera on 2007-02-01
If i were you I would just make a tailored linux before making my own OS, its much easier...
You really got to know programming and how a computer works.
I mean sure you could try to build your own unix/dos like system or whatever floats your boat but its far from easy

---

### Post by unbuntu on 2007-02-01
> **presbp said:**
> What if I was to try and make my own operating system.  I am not talking about a clone of Windows or Mac OS X or another Linux distribution.  What if I wanted to completely try and make my own operating system without stealing ideas from windows mac os's or linux distributions.  **Could I do it, and where would you say would be the best place for me to start?**

I think it would be really cool to make a Linux distribution but I was thinking wouldn't it be even cooler to try and make my own operating system?

on top of everyone else has said, there're couple of other open source OS'es besides Linux/BSD, e.g. ReactOS (suppose to be a clone for Windows), FreeDOS

---

### Post by RAV TUX on 2007-02-02
> **presbp said:**
> What if I was to try and make my own operating system.  I am not talking about a clone of Windows or Mac OS X or another Linux distribution.  What if I wanted to completely try and make my own operating system without stealing ideas from windows mac os's or linux distributions.  **Could I do it, and where would you say would be the best place for me to start?**

I think it would be really cool to make a Linux distribution but I was thinking wouldn't it be even cooler to try and make my own operating system?
It is a big project...I would suggest in helping where help is needed...

I suggest help with [**Haiku.**]("http://haiku-os.org/")

---

### Post by aysiu on 2007-02-02
I believe Linus Torvalds wrote the first version of Linux over the course of a summer, but...

1) Already knew what was involved
2) Based it on an already-existing operating system (Minix?)
3) Almost never left his room--just stayed cooped up in there programming, day and night

Start with Linux from Scratch:
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by riven0 on 2007-02-02
> **presbp said:**
> ...but I was thinking wouldn't it be even cooler to try and make my own operating system?

You're going to do it all on your own, too? Man, you are brave. You better quit your job and get to work if you ever want to finish your os within the next 10 years. :lol:

---

### Post by xabbott on 2007-02-03
> **aysiu said:**
> ...
2) Based it on an already-existing operating system (Minix?)


Hrm, I wouldn't say it was based on Minix. Minix was made for education and I think was used as a build enviroment. The actual design of the kernels are very different. Anyone interested could check out [the infamous debate]("http://en.wikipedia.org/wiki/Tanenbaum-Torvalds_debate").

---

### Post by xabbott on 2007-02-03
> **riven0 said:**
> You're going to do it all on your own, too? Man, you are brave. You better quit your job and get to work if you ever want to finish your os within the next 10 years. :lol:

You never "finish" an os. So making one doesn't really take ten years.

---

### Post by happy-and-lost on 2007-02-05
Time and Coffee are the only 2 real components in an OS, and alot of it too.

---

### Post by Hendrixski on 2007-02-05
> **aysiu said:**
> I believe Linus Torvalds wrote the first version of Linux over the course of a summer, but...

1) Already knew what was involved


I'd like to disagree with that just a little bit.  In his autobiography Linus mentions how if he knew how much work would lay ahead he would have never started it.

To say that Linus made an operating system is stretching it too far.  He made a Kernel.  The open source community made the rest of the operating system.  Much of it was pre-assembled from the GNU project, which is still working on its first release of the HURD kernel.

So really, GNU/Linux so far has been almost 20 years of work by thousands of people.  Don't start a new OS, contribute to an existing one.

---

### Post by steven8 on 2007-02-07
> Don't start a new OS, contribute to an existing one.

I'd stamp my agreement on that statement big time!!

---

### Post by rai4shu2 on 2007-02-07
Contributing is no fun. If you want fun, learn assembly and do all the nitty gritty stuff yourself. Memory handling, fault-handling, timer-handling, hardware-hammering, multi-tasking, multi-processing, memory protection, coprocessing, etc. is glamorous stuff you'll never get to do yourself otherwise.

---

### Post by RAV TUX on 2007-02-07
> **presbp said:**
> What if I was to try and make my own operating system.  I am not talking about a clone of Windows or Mac OS X or another Linux distribution.  What if I wanted to completely try and make my own operating system without stealing ideas from windows mac os's or linux distributions.  **Could I do it, and where would you say would be the best place for me to start?**

I think it would be really cool to make a Linux distribution but I was thinking wouldn't it be even cooler to try and make my own operating system?Start with Morphix.

---

### Post by mips on 2007-02-07
I honestly don't think we are going to hear from the OP again. Kinda like a bait & run post.

---

### Post by WaterCottage on 2007-02-07
> **presbp said:**
> 

I think it would be really cool to make a Linux distribution but I was thinking wouldn't it be even cooler to try and make my own operating system?


[COLOR="Blue"]Recommend that you write it in Machine language in order for fast speed and small size.[/COLOR]:)

---

### Post by mips on 2007-02-07
Somehow i don't think we are going to hear from the OP again...

---

### Post by RAV TUX on 2007-02-07
> **mips said:**
> Somehow i don't think we are going to hear from the OP again...
perhaps you should PM him

---

### Post by erlyrisa on 2007-02-09
I would love to do this:

Dream OS....

1st Abstraction Layer (Hard Shell) full control of OS/Hardware via an Assembler (like debug in dos)
Shell. Like a Posix shell with code in assembly or Higher.
VM.Shell - Ruby or even higher level language is what you would boot to.
GUI - 100% XAML - and even the code behind could slowly be XMLised - though Msoft is already leap years ahead.

The VMachine would be an 'open entity' - all information can be passed to it from shell devices . eg IPv6 transactions, Mount Pionts etc
Information would be stored in a container called the VMshell container. The libraries for the VM shell would also reside in the container - making them wholly upgradable from shell sources.

-Really linux though is already what I have described above - with the exception of Higher language shells still keeping data/libraries in the shell.

-A sun Java machine is pretty much what I described above - an the new >.Net machine will be what I have described above (if it technically already isn't)



--I wouldn't mind doing a distro that booted to a DotGNU.3 + .OPenGL/XNA shell and nothing else. - you could make your own gui via XAML. right there at the prompt.

---

### Post by aysiu on 2007-02-09
> **Hendrixski said:**
> I'd like to disagree with that just a little bit.  In his autobiography Linus mentions how if he knew how much work would lay ahead he would have never started it. Point taken.

But there's a big difference between a seasoned columnist not realizing how much work would be involved in writing a trilogy of novels and someone barely able to construct a sentence not knowing what's involved in writing a novel.

If you have to post a thread on how to make an operating system, you probably have other things you have to learn first.

---

### Post by slimdog360 on 2007-02-09
you would be better off using the linux or bsd kernel (which talks to the hardware) and building off of that. Otherwise you would have to learn all about the i386 etc processor technology.

---

### Post by justin whitaker on 2007-02-09
There are lots of good OS ideas and nascent kernels out there....just check OSNews, and Freshmean for links. One of my faves was this [Unununium]("http://en.wikipedia.org/wiki/Unununium_(operating_system)") OS (or whatever) idea that loads everything on the fly via components. That's a slick idea, but the website no worky. :(

---

### Post by mmcclure79 on 2007-10-30
You don't get it from their website instead you need to go to Source Forge to  get it.

[http://sourceforge.net/projects/uuu]("http://sourceforge.net/projects/uuu")

---

