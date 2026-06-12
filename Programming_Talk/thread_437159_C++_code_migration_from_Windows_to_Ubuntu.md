---
title: "C++ code migration from Windows to Ubuntu"
date: 2007-05-08
forum: Programming Talk
---

### Post by feravolo on 2007-05-08
Hello,

We need help transporting a large C++ project from Visual Studio 2005 to Ubuntu, and need to know what tools are available us.

Thanks 

Mike Feravolo

---

### Post by Auria on 2007-05-08
"Tools" is perhaps too vague, perhaps elaborate a little. Libraries, IDEs, GUI editors, documentation, etc... ?

---

### Post by samjh on 2007-05-09
> **feravolo said:**
> Hello,

We need help transporting a large C++ project from Visual Studio 2005 to Ubuntu, and need to know what tools are available us.

Thanks 

Mike Feravolo

Mike, what dependencies does your C++ project have?  Do they rely on libraries that are available for Linux, or are they Windows only?

The standard C++ tool chain for Linux are the GNU build tools, which include:
g++ (GNU C++ compiler)
make (build management)
autotools (a collection of tools for automatic build management)
binutils (a collection of tools for working with binary files)
gdb (the GNU debugger)

If your project doesn't have Windows only dependencies, you can try using Code::Blocks IDE ([www.codeblocks.org](www.codeblocks.org)) to work on your Visual Studio project.

---

### Post by feravolo on 2007-05-09
I can't go over the details of the project, however it is an embedded system and does have quite a few windows dependencies as far as the user interface goes.

I am not looking for the solution to the entire problem, just for the different options that are out there. From what I used stand the cost per unit of using windows xp embedded as an operating system is making significant impact on the profitability of the finished product when it goes to market, Therefore the people that are developing this code are looking for a different operating system, in the middle of the development phase after a ton of code has already been written.

---

### Post by samjh on 2007-05-09
Judging by your reply, it seems this question is not something that can be properly answered in this forum, or in any public discussion board.

I guess from your description that the project is run on Windows XP Embedded.  I have no experience with the platform and cannot really give useful advice.  The only sure thing I know is that the UI will need to be completely rewritten in order to run on a Linux system.  But if the project uses .NET Framework and WinForms, then the Mono Project may be worth investigating, since it partially supports WinForms on Linux (however that feature could have patent complications in the future).

---

### Post by feravolo on 2007-05-09
> **samjh said:**
> Judging by your reply, it seems this question is not something that can be properly answered in this forum, or in any public discussion board..

We  don't agree that the details of the project are required to talk about this in a forum.  Since people are always "cagey" when talking to consultants, it was hard for us to get any information about this project in fear that we would use it to compete against them.  So all we are  trying to do is to find out if we what to take a meeting with these people or not.

We don't do a lot of C++ programing these days and the information that has been provided to us though this posting has been very helpful and we would like to thank everyone for taking the time to post it for us.

So any thing that anyone can think of will be helpful to us, we don't plan to do the actual work just help find the right path for a potential client that seems to be in some trouble. 

Thanks Again

Mike Feravolo
Cocoa Beach, Florida

---

### Post by DavidBell on 2007-05-10
What I have done that worked with a VS2002 project is 

* Google, download and install wxPack in Windows, it should detect VStudio and add a few wizards if you are lucky.

* Ditch MFC and redo the GUI in wxWidgets in VStudio, you have to rewrite the GUI bit but wx is fairly similar to MFC/WTL and most of your functions can be easily converted. Unless the GUI is very complex it's quite doable, and GUIs are easier second time round anyway ;-). wxFormbuilder helps but it's not perfect. Kill off other MS specific stuff like CString and change to wx or stl equivalent. When it all compiles without warnings and runs VStudio, copy source as is to linux.

* You need to set up the same version of wxWidgets on your linux box - you probably need to compile and set it up from source. Then reopen your source in Code::Blocks and I seem to remember it made a makefile automagically.

* Recompile in linux/code::blocks with GCC, you will probably get more warnings for slight differences between compilers.  Fix the warnings and you should be good to go. (Note: you can also set up GCC as an alternative compiler in VS if you want to catch these warnings in Windows)

That's my limited experience anyway, I did it on a couple fairly simple things to see how it worked, but no reason it couldn't be done on bigger projects. If you use .NET you need to look into Mono project but I don't know how successful it really is.

DB

---

