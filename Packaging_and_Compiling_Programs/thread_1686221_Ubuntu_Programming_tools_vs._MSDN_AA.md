---
title: "Ubuntu Programming tools vs. MSDN AA"
date: 2011-02-12
forum: Packaging and Compiling Programs
---

### Post by GTMoraes on 2011-02-12
Hey, I'm running Ubuntu Maverick.

I've started my university. On the 'Introduction to Programming' class, the teacher talked about the MSDNAA tools, Visual Studio, among other Microsoft tools. 
As I use and love Ubuntu, I asked her about any linux counterpart. Her words were "You've got GCC, CodeBlocks and Dev C, but they're all buggy and not reliable. You should get windows" 

- Even though the Technology Center on the university runs Ubuntu 10.04.. - 

Oh well, I don't know if she's right. But she's the teacher anyway and obviously knows better (at least than me). So here am I, kindly asking for the community for a programming tool. I need one that really kicks ***, or at least is on pair to the Microsoft MSDN tools.
And about the buggy tools... do you guys know anything about it? Is that much unreliable?
Should...... I install windows?

Thanks for the attention!

P.S.: Nobody, apart from me ('till some point) and the system administrator, knows how to use the Ubuntu. I've been 'promoted' to be the class' monitor. tee-hee :)
P.P.S.: The Technology Center got some nice i7's. I don't know outside Brazil, but -only- a compatible motherboard + i7 processor = +US$1000. Can I use all of its firepower somehow?

---

### Post by GregBrannon on 2011-02-12
There is a sub-forum here called Programming Talk.  The stickies in that forum cover everything you need to know to get started in programming in a Linux environment.

Is the teacher right, and should you install Windows to learn to program? I don't think so and absolutely not.  GCC and the tools she mentioned are not buggy, at least no more than any other software as all software has bugs.

Good luck!

---

### Post by Vaphell on 2011-02-12
i'd seriously lmao if i heard that line.
gcc buggy? given that earth shattering news one can only wonder how it's possible that linux environment is in an usable state at all and thank divine powers for that... ;-) In fact the only time i have ever heard about compiler doing something oddball from c++ pros at my work was in fact microsoft's one messing things up in some haxxorish template inheritance magic. Either way, i don't think your programming projects will do anything that would expose any obscure flaws in a compiler.

You can go text editor+makefile combo but there is like dozen of open source IDEs (for linux/crossplatform) if you want - Codeblocks, codelite, kdevelop, anjuta, eclipse with C++ plugins, QtCreator - you name it. Granted, open source IDEs are not as slick as VS and don't provide tight integration with the OS because frankly it's impossible. Only MS can provide it in Windows and in linux greater modularity prevents the case of 'one tool to rule them all'. Integration is nifty, sure, but skipping it can be a good thing if you want to go cross-platform. In such scenario, where you want to have a common path as big as possible to streamline the process, dependency on microsoft environment with its own dependencies, quirks and caveats is a liability not an asset.

another thing - 'Introduction to Programming' has no business in teaching vendor specific solutions. Text files with optional makefile are all that is needed to show the basics to students if you go c/c++ route.

---

### Post by GTMoraes on 2011-02-12
Thanks for such professional answer and for the programs' name!
So, you tellin' me that I'll be able to go through this particular class using a text editor + makefile for basic programming? No need to worry about (now) with fancy programs? What do you recommend me? I want it to be as easy as possible.

Thanks again!

P.S.: I don't know anything about programming

---

