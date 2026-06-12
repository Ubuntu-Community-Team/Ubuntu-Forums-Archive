---
title: "Newbie question about Mingw32"
date: 2008-05-12
forum: Programming Talk
---

### Post by razlken on 2008-05-12
a noobish question...how am i supposed to open it? i installed the 3 packages using the synaptic manager, but don't know what to do to open it. any help would be appreciated.

---

### Post by WW on 2008-05-12
You don't open it. The mingw32 package provide commands that you give in a terminal to cross-compile your code.  I gave an example of cross-compiling a simple "Hello, world" C program in [this thread](http://ubuntuforums.org/showthread.php?t=724495).

---

### Post by razlken on 2008-05-12
checked the link but excuse this somewhat stupid question, but still don't get it where am i supposed to write the code?? i'm used working on Visual studio 6, but it isn't compiling/building on wine so i thought to switch to mingw32, but can't really get to use it well...

---

### Post by SledgeHammer_999 on 2008-05-12
if you want to write code using an IDE check Code::Blocks, Kdevelop, CodeLite and other similar programs

If you want to *just* write code, just do with a text editor like gedit.

Then use this code to compile it with mingw32

mingw32 is a compiler

---

### Post by WW on 2008-05-12
It's not a stupid question; in fact, it is pretty common for anyone moving from Visual Studio to programming in Linux. 

You can use any text editor that you prefer.  You may want to use an "IDE" (integrated development environment), to create a working environment something like Visual Studio.  There are several options in Linux. See this thread: [http://ubuntuforums.org/showthread.php?t=752224](http://ubuntuforums.org/showthread.php?t=752224).
I haven't tried it, but it may be possible to set them up to use mingw32 as the compiler instead of gcc.

But why you are using mingw32 instead of gcc?  mingw32 is great for cross-compiling (meaning compiling a program in Linux that can be executed in Windows), but normally you would write a program in Linux and then run it in Linux. For this, use gcc (or g++ for C++).

---

### Post by samjh on 2008-05-12
> **razlken said:**
> checked the link but excuse this somewhat stupid question, but still don't get it where am i supposed to write the code?? i'm used working on Visual studio 6, but it isn't compiling/building on wine so i thought to switch to mingw32, but can't really get to use it well...

The mingw32 packages are used the same way as the gcc compilers: via the command line.

If you've ever used gcc on the command line, you'd do this to compile helloworld.c:
```
gcc -o helloworld helloworld.c
```

The same thing can be done using Mingw32 by doing:
```
i586-mingw32msvc-gcc -o helloworld helloworld.c
```

You can use the Code::Blocks IDE and set it up to use Mingw32 if you think that will be easier for you.  Code::Blocks can be found here: [www.codeblocks.org](www.codeblocks.org)
I haven't used it with Mingw32 on Linux, so you might need to search around for instructions on how to configure it to use Mingw32. :)

---

### Post by stevescripts on 2008-05-13
A quick late-night thought.  You may want to look at monodevelop - it might feel more familiar.

Steve

---

### Post by JupiterV2 on 2008-05-13
If you're familiar with GNU autotools and pkg-config I believe you can setup your autoconf.ac to automate the build process for you.

I haven't tried it yet but I have a program I'm almost finished I plan on porting to Win32.

---

