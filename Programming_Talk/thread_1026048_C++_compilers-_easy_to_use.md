---
title: "C++ compilers- easy to use"
date: 2008-12-30
forum: Programming Talk
---

### Post by Maximo7274 on 2008-12-30
Is there a c++ compiler for Ubuntu that is like dev-c++ for windows?  I tried Geany, but I couldn't get it working right.  It can be a really simple compiler, but one that is easy to use as I just want to use it for small projects.  I have my desktop with vista and visual c++ for the big projects.

Any help would be appreciated.

---

### Post by cb34 on 2008-12-30
i like code::blocks IDE. i tried all the editors and compilers from the repos, and i only like to use this one.

it's in ADD/REMOVE under Programming if you're gui'in it. [noparse]:)[/noparse]

---

### Post by CLomax on 2008-12-30
I use gcc for C, might work for c++ too.

First make sure you:
> sudo apt-get install build-essential
To write the program:
> nano *name*.c
Or you can use gedit.
To compile:
> gcc *name*.c -o *name*
To run:
> ./*name*

[B]Edit:
There's NetBeans too from the repos.[/B]

---

### Post by monkeyking on 2008-12-30
theres a bunch of stickies about this.

But are you talking about a compiler or ide?

---

### Post by samjh on 2008-12-30
> **Maximo7274 said:**
> Is there a c++ compiler for Ubuntu that is like dev-c++ for windows?  I tried Geany, but I couldn't get it working right.  It can be a really simple compiler, but one that is easy to use as I just want to use it for small projects.  I have my desktop with vista and visual c++ for the big projects.

Any help would be appreciated.

Dev-C++ isn't a compiler.  It's an Integrated Development Environment (IDE), which is fancy editor with project functionality.  The compiler it uses is MinGW, which is the Windows port of the GCC compiler used on Linux/Unix systems.

Try [Code::Blocks](http://www.codeblocks.org/).  You can find it in the repositories.  Install using:
```
sudo apt-get install codeblocks
```

---

### Post by nvteighen on 2008-12-31
At the very end, people here usually end up using vi/emacs/gedit/<place a decent text editor> + gcc/g++ as the simpliest solution for C and C++...

---

### Post by ByteJuggler on 2008-12-31
How about [KDevelop]("http://www.kdevelop.org/")?

---

### Post by ggaaron on 2008-12-31
> **nvteighen said:**
> At the very end, people here usually end up using vi/emacs/gedit/<place a decent text editor> + gcc/g++ as the simpliest solution for C and C++...

Simple and really powerful. It is usually all you need, but for ones that can't live without almighty IDE there is netbeans, eclipse, kdevelop... From these I'd recommend eclipse for c++.

---

### Post by pokerbirch on 2008-12-31
+1 for code::blocks as it's similar to using Visual Studio.

---

### Post by Maximo7274 on 2008-12-31
Thanks to everyone for the help.  Wow that was fast responding... I was mainly looking for something that was an IDE, but could also compile, just like dev-c++.  I guess i will try out code::blocks as it is like visual c++.

Sorry for the lack of knowledge in c++ compilers and IDE:confused:, i am somewhat new to c++ and I didn't really know there was a difference between and IDE and a compiler.  

Thanks for all the help!:D
P.S.- I think that was a record for the fastest responding time!:lolflag:

---

### Post by jimi_hendrix on 2008-12-31
vim + g++ == "good coding"

---

