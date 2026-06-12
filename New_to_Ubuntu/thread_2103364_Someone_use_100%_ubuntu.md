---
title: "Someone use 100% ubuntu?"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by rilesac on 2013-01-10
Hi, I am studying software development and I want to use 100% Ubuntu. I have read a lot about Linux in general and I would like to change.

I already tested Ubuntu, Fedora, Linux Mint, BackTrack and others but just for a few days.

Here are my questions...

1. If I use C# and C++ (in windows), its possible to use them in Ubuntu? Or the solution would be use a virtual box?

2. Like a programmer its good to use Linux?

Greetings!

---

### Post by zombifier25 on 2013-01-10
Of course you can program in Ubuntu. You must first to install the build-essential package, either by command line
```
sudo apt-get install build-essential
```
or graphically, with Software Center or Synaptic. After that, the simplest way is to write a program using your preferred text editor, and then compile it using gcc for C (or g++ for C++):
```
gcc filename.c -o file
```

You can also install an IDE to do all the work graphically like Geany. Or if you code in C#, then install MonoDevelop.

---

### Post by Abhinav Kumar on 2013-01-10
Hi 
> **rilesac said:**
> 
1. If I use C# and C++ (in windows), its possible to use them in Ubuntu? Or the solution would be use a virtual box?


Yup there are several people who completely have switched over to linux. For compiling C++ codes you can use g++. I have no experience in C#. Hence, I can't say anything about C#.

> **rilesac said:**
> 
2. Like a programmer its good to use Linux?

Linux is superb for programmers. You have several great tools ranging from compilers, debuggers to IDE for many different languages. Infact its so good that I would recommend using linux for software development.:D

Regards,
Abhinav

---

### Post by squakie on 2013-01-10
I whole heartedly support Ubuntu, but just in case:  developing an application for Microsoft Windows in Ubuntu is a different animal.  If you don't mind the customer having to install a couple of packages to Windows, you could try using QT or GTK for the graphical interface.  If you want it to be a standard Windows gui'd program, you'll need a slightly different approach.

---

### Post by d4rk0wl on 2013-01-10
I have found it much easier to build/compile/debug programs on Ubuntu or *nix in general then I have in Windows. I am happy I switched over.

I would recommend checking out the program Geany (available in app store) it is what I use for all my coding work and it is great. :)

Regards,
- D4rk0wl

---

### Post by slickymaster on 2013-01-10
Regardless of whether you desire to use a 100% Linux platform - which I support completely - you should take into consideration  that C# is a language more native to windows.

Having said that, Mono Develop, the IDE associated with Mono Project should be enough for C# development on Linux, it contains pretty much everything you need to get started right away (Compiler, Runtime Environment, IDE) and if you have used visual studio you should find it simple enough to get started.

To C++ there's a lot of solutions, just google for **_developing c++ on linux_**.

---

### Post by squakie on 2013-01-11
My whole point may be moot, but what I was suggesting is that if you are trying to develop programs that are intended for Microsoft Windows by using Ubuntu as the development platform, then it may not be successful.  There may be, but I haven't read anything about a package for Ubuntu that lets the code be intended as a native GUI'd app to Microsoft Windows.  All the dll's, etc., aren't there and aren't the way things are done in Linux (similar items, just not the same).

---

### Post by mastablasta on 2013-01-11
you mean like for example GIMP? or inkscape? or numerous other opensource linux progammes with windows ports?

---

### Post by zombifier25 on 2013-01-11
> **squakie said:**
> My whole point may be moot, but what I was suggesting is that if you are trying to develop programs that are intended for Microsoft Windows by using Ubuntu as the development platform, then it may not be successful.  There may be, but I haven't read anything about a package for Ubuntu that lets the code be intended as a native GUI'd app to Microsoft Windows.  All the dll's, etc., aren't there and aren't the way things are done in Linux (similar items, just not the same).

> **mastablasta said:**
> you mean like for example GIMP? or inkscape? or numerous other opensource linux progammes with windows ports?

How do you know that the developers of GIMP, Inkscape, ... does not compile the Windows version on Windows? (in GIMP's case, the Windows version was not even provided by the developers, but was provided by a third-party.)


Cross compiling (the act of compiling a program for an OS different than the OS you're compiling on) is possible, but if you want to develop your software for Windows, and want to know if it will work well or not, it's always good to keep a Windows box around, or on a virtual machine.

With that being said, for programming, Ubuntu/Linux is one of the best platforms yet, with many helpful tools only an apt-get away.

---

### Post by slickymaster on 2013-01-11
> **zombifier25 said:**
> Cross compiling (the act of compiling a program for an OS different than the OS you're compiling on) is possible, but if you want to develop your software for Windows, and want to know if it will work well or not, it's always good to keep a Windows box around, or on a virtual machine.

+1 on keeping a Windows box around or on a virtual machine.

Regarding cross compiling, although possible , IMHO one must always keep in mind the difficulties and the problems that can occur, namely problems with the programs themselves and problems with the build system.
This in addition to issues associated to speed, flexibility, capability, convenience, and so one, make an approach to cross compiling really tricky.

---

### Post by iMac71 on 2013-01-11
First of all, I wish to precise that I'm not a programmer; I like to program as hobby.
This said, I think that it be a good choice to write pure code as much as possible, i.e. to use system specific libraries only when it's strictly necessary: doing so, the code is more portable between different platforms.

---

### Post by squakie on 2013-01-11
Yeah, any program that runs in Windows either needs a cross-compiler or a running Windows installation to compile it.  There's also, as I said, the mention of DLLs, etc.  Programs like GIMP, etc., that run on multiple platforms are not just take the same source over to another platform and compile it either.  These type of apps have been changed to support the internal Windows calls for creating the GUI, etc..  The only exceptions that I know of are programs that use a cross-platform tool, such as GTK.  The GTK package is modified from the Linux version so it can use native Windows calls.  This makes it transparent to the program as the same GTK functions still work.  However, it still requires installation of the GTK package in Windows.  We know that GTK stands for Gimp Tool Kit, so perhaps Gimp is done slightly different, but it still must be compiled for the other environment.

I've used GTK in the past for cross-platform development.  All I had to do was change the code slightly so it knew if it was Linux or Ubuntu so it could build paths up.  The same source compiled and ran on both Linux and Windows, but this was due to using GTK for the GUI.

At any rate, I was just trying to say the OP needs to keep such things in mind.  If they plan to develop Windows programs but want to use Linux as the development platform, it's not as simple as some think.  At a minimum extra tools are needed.  Personally, if I was going to develop for Windows I'd do it on a Windows platform - a virtual machine as mentioned by someone else here in the thread would suffice.  Likewise, if I was going to develop for Linux then I would use a Linux box.  Yes, Mingw, etc., are available to be installed in Windows, and give you a minimal Linux environment to compile in, but things are just much easier on their native box.

---

