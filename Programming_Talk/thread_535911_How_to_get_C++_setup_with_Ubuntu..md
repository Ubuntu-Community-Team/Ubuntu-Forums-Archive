---
title: "How to get C++ setup with Ubuntu."
date: 2007-08-27
forum: Programming Talk
---

### Post by Will B-R on 2007-08-27
I'm looking for a tutorial on how to download and get started with C++ in Ubuntu.

I'd had just started learning C++ on windows with DevC++ which set itself up, but I've recently gone 100% Ubuntu and would like to continue.

I've tried searching the forums for g++ and hello world; but I can't seem to find what it is I'm looking for.

I would be very grateful for any help anyone could offer.

Thanks in advance.

---

### Post by Dark Star on 2007-08-27
AS far as C++ in Linux I use G++ , and Anjuta ... 

See G++ needs to be used from commands from Terminal.. if u want to compile while Anjuta has inbuilt like Turbo C..
Here are steps u need to do:--

**For G++ Installation and usage :---**

To install G++ 1'st open Terminall.. and type this
```
sudo apt-get install g++
```

but you should probably do (to install everything you might need in ways of developement): Type this after the above commands installation finished. :cool2: 
```
sudo apt-get install build-essential
```

That will also include gcc and g++;) 

Now usage of G++/GCC....

simple, use editor to type in your C/C++ code. save it with the .c or .cpp extension.

**Then exit form the editor, in terminal type :**

cc filename.c

This will create the **a.out file.**

now type **./a.out**

**to get the output**

to specify a custom name, u need :
```
cc -o outputfilename sourcefile.c
```

**About Anjuta : **

To install type thiis in Terminal 
```
sudo apt-get install anjuta
```

It will have a button to press to compile your code.

Hope it helps 
Peas Ds:)

---

### Post by fct on 2007-08-27
Install the package build-essential ("sudo apt-get install build-essential" on the terminal).

Next thing you want is probably an IDE. KDEvelop is a nice one. You can also install eclipse with the CDT plugin for C/C++ development. If you want to mess with an IDE in development, codeblocks is promising and functional, but you want to install the nightly builds.

---

### Post by moma on 2007-08-27
People has already told you about the "build-essential" package. It contains compilers for both C (the compiler name is gcc) and C++ (compiler name is g++).

Learn the basics of C++ by using a simple (gedit or kate) editor and compile the code from the command line.
Check [these C++ guides...]("http://home.online.no/%7Eosmoma/opportunities.html")

Later on, test this [install  guide]("http://ubuntuforums.org/showthread.php?p=2816470#post2816470") for the Code::Blocks IDE.

---

### Post by Will B-R on 2007-08-27
Brilliant that looks like exactly what I needed.

Thanks a lot.

---

### Post by Wybiral on 2007-08-27
I used to use DevC++ in Windows and found Code::Blocks to be really similar to it (but available for Linux).

Since then I realized that I didn't need an IDE at all and I do most of my code+compiling from GEdit now.

But Code::Blocks is very similar to DevC++.

---

### Post by astrojith on 2007-08-30
I somehow installed Code Blocks by reading this guide : [http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu)

But, the funny thing is, I don't know how to open the program. I mean, I don't see an icon anywhere. Neither does anything open when I type "codeblocks". Can anybody help me ?

---

### Post by LaRoza on 2007-08-30
> **astrojith said:**
> I somehow installed Code Blocks by reading this guide : [http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu)

But, the funny thing is, I don't know how to open the program. I mean, I don't see an icon anywhere. Neither does anything open when I type "codeblocks". Can anybody help me ?

I never used it, but it should be under Development or Programming in your menu.

I don't have Ubuntu in front of me, so I can't say for sure.

---

