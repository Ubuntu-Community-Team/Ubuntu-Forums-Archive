---
title: "Noob looking for C++ Editor/Compiler"
date: 2011-04-08
forum: Packaging and Compiling Programs
---

### Post by Murdoc419 on 2011-04-08
So I have just started my first programming class in college and would like to write all of my programs here on Ubuntu. I have been looking for a couple weeks but haven't had much luck (I don't really know what I'm doing). My professor has us using Textpad to edit our code and Cygwin to compile it. They work together nicely so we never have to open the Cygwin shell to compile. We simply click tools>compile C++ and tools>run C++ in text pad to compile and execute our code. I am looking for something with the same functionality in Ubuntu. I have found Kate and Eclipse but have had no luck figuring out how to configure them to compile and execute C++. For me Eclipse seems like the better program but I wouldn't really know as I have just started doing these things. If anyone could help me in setting up either of these programs I would greatly appreciate it. I'm open to suggestions to other software that may be better suited to me as well.

---

### Post by Murdoc419 on 2011-04-08
sorry to bump my own post but thought I would let everyone know that I have figured out (sort of) why I was having troubles. I needed to install the g++ packages. Right now I'm just using gedit to write/edit the code, and terminal to compile/execute the programs. I think Fall quarter I will definitely be looking out for a class teaching about Linux operating systems.

---

### Post by SevenMachines on 2011-04-09
You'll here people mention the 'build-essential' package a lot, installing that covers the basic development environment, including the c++ compiler

---

### Post by marin123 on 2011-04-09
see if gcc can compile c++...

i like monodevelop. you can compile c, c++ and c#... try it out and see if you will like it :)

EDIT: i have checked gcc..

```
gcc -x c++ yourfilename.cpp
```

it will compile and make an executable..

---

### Post by GregBrannon on 2011-04-09
There is a sub-forum here called Programming Talk where the subject of which Integrated Development Environment (IDE) is best to use for which application, programming task, language, when learning, etc. is often discussed, near to death, in fact.  You'll find information in the stickies at the head of that forum and many, many threads on this topic.

Edit: I should add that whether a student should use an IDE at all is also hotly debated, so the discussions are not limited to which IDE to use but which editors are best for all stages of programming and for which programming languages.

Good luck with setting up your programming environment and with learning C++.  Come back for more help.

---

### Post by lucasart on 2011-04-09
> **Murdoc419 said:**
> So I have just started my first programming class in college and would like to write all of my programs here on Ubuntu. I have been looking for a couple weeks but haven't had much luck (I don't really know what I'm doing). My professor has us using Textpad to edit our code and Cygwin to compile it. They work together nicely so we never have to open the Cygwin shell to compile. We simply click tools>compile C++ and tools>run C++ in text pad to compile and execute our code. I am looking for something with the same functionality in Ubuntu. I have found Kate and Eclipse but have had no luck figuring out how to configure them to compile and execute C++. For me Eclipse seems like the better program but I wouldn't really know as I have just started doing these things. If anyone could help me in setting up either of these programs I would greatly appreciate it. I'm open to suggestions to other software that may be better suited to me as well.

I use codeLite, you can install it directly from Synaptic Package Manager. It's quite straightforward to use. The interface is very similar to Microsoft Visual C+ for example: Workspace/Project, F7 to build, F5 to run, F9 for breakpoints, F10/F11 for step debugging. A debug windows where you can watch your variables etc. It uses GCC for C and G++ for C++. Have a try, I think it's a good choice for beginners.

Of course you can use whatever text editor you like and compile in command line, but it's not very practical if you're a beginner. I'm sure the super hard core developpers use VI, but for my part I prefer a simple IDE :)

---

### Post by leg on 2011-04-09
Install build essentials and Geany and then you will have similar environmeb
nt to the one your professor has provided.

---

### Post by cgroza on 2011-04-09
CodeBlocks for C++, and g++ as a compiler. I find geany a little bit weird for C++, other wise I use it for Java, Python and sometimes Ruby.

---

### Post by rsajdok on 2011-04-16
You can use the best plugin to Eclipse:
[http://www.eclipse.org/cdt/]("http://www.eclipse.org/cdt/")

---

