---
title: "[SOLVED] C++ compiler"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by MarlonDean on 2008-09-15
Hi everyone,

I am currently studying programming. I also recently switched to ubuntu. Now in windows I used Dev C++ as my IDE and Mingw as the compiler. I tried running Dev c++ through wine, but no success...

Does anyone know how to get it working, or can you suggest a great IDE?

I really dont want to dual boot just because of this....

Thanks

---

### Post by Christmas on 2008-09-15
There are several ways to compile C++ sources. First install the package *build-essential* which contains the compilers, like gcc (GNU Compiler Collection). Create a source using a text editor (for example Kate, Gedit, Nano, Vim, Emacs etc) and compile it using:

```
gcc hello_world.cpp
```

Or:

```
gcc hello_world.c
```

See *man gcc* or *gcc --help* for parameters.

There is also a port of Code::Blocks for Linux, but you'll have to install the dependencies and compile it yourself. I wrote a tutorial for Debian [here]("http://vivapinkfloyd.blogspot.com/2008/07/how-to-compile-and-install-codeblocks.html"), it should work for Ubuntu too.

As for other IDEs, you can try:

**CLI (Command Line Interface)**
Nano
Vim
Emacs

**GUI (Graphical User Interface)**
Kate
Gedit
Geany
KDevelop (although for studying I don't recommend such a complex application)
Anjuta

Many others are available, just search the forum in the Programming section.

---

### Post by bumanie on 2008-09-15
I am not a programmer so know very little. However, what I do know is that for "C" and "C++" the compiler can be installed via command line > sudo apt-get install build-essentialThis gives all the necessay libraries etc. needed. The gcc compiler is the program needed if one needs to install source code onto linux, most users need to install it at some stage. [Look here]("http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html") for a bit more information

---

### Post by rraj.be on 2008-09-15
> **MarlonDean said:**
> Hi everyone,

I am currently studying programming. I also recently switched to ubuntu. Now in windows I used Dev C++ as my IDE and Mingw as the compiler. I tried running Dev c++ through wine, but no success...

Does anyone know how to get it working, or can you suggest a great IDE?


I think you should have known about code :: blocks IDE.

You can have it in both windows and ubuntu.

Try this link to install code blocks IDE 

[http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu]("http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu")

---

### Post by Joeb454 on 2008-09-15
Code::Blocks is a good IDE.

Personally I use vim with syntax highlighting :) Also to compile, usually I use g++ instead of gcc. The syntax is the same however :)

---

### Post by MarlonDean on 2008-09-15
Thanks, Code::Blocks works great! I suggest it to anyone looking for a nice, easy IDE

---

### Post by pwicken on 2008-09-15
[http://sourceforge.net/projects/dev-cpp]("http://sourceforge.net/projects/dev-cpp")

---

