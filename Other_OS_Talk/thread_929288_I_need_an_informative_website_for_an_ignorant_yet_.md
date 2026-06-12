---
title: "I need an informative website for an ignorant yet potentially helpful budding coder."
date: 2008-09-24
forum: Other OS Talk
---

### Post by MaxIBoy on 2008-09-24
This kid is a grade younger than me. He's just getting started on programming, and I think the world needs more programmers. He's suffering from a few delusions, though.

He's working on a graphical shell/desktop environment, which he's making in Game Maker. So far so good. I started out with Game Maker. It's a good beginning step. His shell focuses on eye candy above all else and isn't practical for real use; animated bubble-shaped menu entries spiral out from a central point, you click on one, they spiral back in, and another set spirals out. That is the extent of the interface. I think that's excusable, because we all make mistakes like that early on.

This shell is very limited. It is a single-tasking environment. The only "application" I've seen it run is a plaintext editor which is built into the shell itself.


Here's the problem: the kid insists up and down that he's created an operating system. He wouldn't know self-hosting if it walked up to him and bit his nose off, sad to say.



Is there any good literature out there on the Internet I could show him? This kid wants his own operating system-- he could be the next Ian Murdock, and I want to encourage him.

---

### Post by Sorivenul on 2008-09-25
If the kid wants an operating system, show/teach him what an operating system is, first.  I work in a college bookstore on my campus part-time and study computer science myself.  The class on operating systems here starts with this book:
[Operating System Design and Implementation]("Operating System Design and Implementation")
It revolves around MINIX, which, IMO, is a great place to start.
This site contains some good information and links:
[ComputerHope]("http://www.computerhope.com/os.htm")
And don't forget the invaluable [HowStuffWorks]("http://www.howstuffworks.com/operating-system.htm").
[The History of Linux]("https://netfiles.uiuc.edu/rhasan/linux/") offers some nice insight on how Linux came to be.
If the kid isn't totally put off after that, start with simple programs: text editors as mentioned, and more.  A user interacts with the OS, which interacts with the hardware.  Understanding this will help in future design efforts, though a full course on heuristics of GUIs probably wouldn't be in order yet.
From there, let the kid decide.  An operating system in C and Assembly (or any other language that is decided upon) is a huger undertaking.  Have him dissect some alternative operating systems listed at SourceForge to see the various kernel codes and what all people are working on.  
I hope this is a good starting point, and good luck!

---

### Post by cmay on 2008-09-25
above post is the best advise being giving but there is one more site you could look at.
[http://wiki.osdev.org/Main_Page](http://wiki.osdev.org/Main_Page)

hope it helps.

---

### Post by MaxIBoy on 2008-09-25
Awesome stuff! I'll show that to him. 

I want to get him started out making a distro to start with, I think I'll suggest him making a PuppyLinux remaster or something.

---

### Post by jrothwell97 on 2008-09-26
If he struggles with a Puppy remaster, toss him a Debian netinstall CD and show him how to build a functional system on top of the CLI base. After that, he may want to try Linux from Scratch, etc.

The important thing to do is to teach him what the kernel does and why it's important that the OS is 'self-sufficient'. I find the 'house' model useful when explaining this: the kernel is the utilities (gas, water, electricity, etc) and everything else is furniture.

---

### Post by MaxIBoy on 2008-09-26
More like the kernel is the foundation, the plumbing, the wiring, and the furnace, the servers and daemons are the electricity, gas, and water, and everything else is furniture.

---

