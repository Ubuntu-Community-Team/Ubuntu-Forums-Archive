---
title: "Compiling something to work on windows from linux"
date: 2008-11-05
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-05
I wrote an application with C, which uses SDL and OpenGL, so it should be cross-platform.

But can I use linux compilers (gcc) to compile it to windows .exe? I'd like to share this application with my friends who use windows.

---

### Post by Delever on 2008-11-05
Check out MinGW compiler.

---

### Post by LaRoza on 2008-11-05
> **crazyfuturamanoob said:**
> I wrote an application with C, which uses SDL and OpenGL, so it should be cross-platform.

But can I use linux compilers (gcc) to compile it to windows .exe? I'd like to share this application with my friends who use windows.

The target should have those libraries as well.

For C, source distributions are what are best, unless you want to package for each platform.

---

### Post by crazyfuturamanoob on 2008-11-05
> **Delever said:**
> Check out MinGW compiler.

Installed MinGW with synaptic, but it doesn't work.

> 
arho@ohra-laptop:~/Työpöytä/C/gltest$ man mingw
Manuaalisivua mingw ei ole
arho@ohra-laptop:~/Työpöytä/C/gltest$ mingw
bash: mingw: command not found
arho@ohra-laptop:~/Työpöytä/C/gltest$ 


---

### Post by crazyfuturamanoob on 2008-11-05
Should I compile my code to exe on a windows box?

---

### Post by JupiterV2 on 2008-11-05
There are multiple ways to achieve what you're trying to do, ranging from easy to hard:

1) [easy] Compile the code on a windows machine. Make sure the appropriate libraries are installed.

2) [moderate] Install Wine and a windows compiler. Depending on what you're doing, bugs in Wine can potentially complicate things. For example, the library you want to install may not cooperate when attempting to install it with Wine.

3) [hard] Create a cross-compiler environment. You will need to cross compile all libraries you will be using, meaning you must build gcc, SDL and any other libraries you intend to use with the --target= configure option **before** compiling your code and linking against these libraries.

---

### Post by WW on 2008-11-05
You don't have to build gcc to cross-compile--that's what the mingw package provides for Ubuntu.  See this thread (and its links) for an example of cross-compiling a simple program: [http://ubuntuforums.org/showthread.php?t=724495](http://ubuntuforums.org/showthread.php?t=724495)

JupiterV2 is right, though, about having to cross-compile all the other libraries that you use in your program.  Some libraries can be cross-compiled with no problems, but others can be a challenge.

---

### Post by unoodles on 2008-11-05
I compile windows programs all the time. What I would recommend is to just download CodeBlocks and run it under WINE (it works fine).
Then just download the windows builds of the libraries you need.
Put the .a files in lib/ and the .h files in include/<libraryname>
Then just use CodeBlocks to add linking library and select the .a file.

---

### Post by crazyfuturamanoob on 2008-11-05
Does the same makefile for linux work when compiling windows stuff?

---

