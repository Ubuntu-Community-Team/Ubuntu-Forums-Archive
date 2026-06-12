---
title: "c/c++ compiler"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by mitar on 2008-09-01
I would like to learn programing in C/C++ languages, so I was wandering if someone knows for a good (free) compiler for Linux. Before I switched to Linux, I had Windows and there were Borland Builder,... If there is something like that for Linux, at all?

---

### Post by kjohansen on 2008-09-01
i think you are actually asking for an IDE not just a compiler.

i like code::blocks, lots of other people like eclipse.

you can use these IDEs with lots of compilers but GNU is the default.

---

### Post by WRDN on 2008-09-01
The compiler many/ most here use is GCC, and this can be installed by opening the Terminal and typing:

```
sudo apt-get install build-essential
```

Then, compile the code. If it is a C program, type:

```
gcc -o program program.c
```

This creates an executable called "program", using the source file, "program.c".

For a C++ program, replace "gcc" with "g++".

If you are looking for an IDE (Integrated Development Environment), then I would recommend [Code::Blocks]("http://www.codeblocks.org/").

---

### Post by cszikszoy on 2008-09-01
Monodevelop can be used as a C/C++ compiler and IDE.

It has an interface very similar to Visual Studio for Windows.  As the name implies, it is mainly used for developing Mono applications, but it will also work as a C/C++ compiler as this page explains:

[http://www.monodevelop.com/Creating_C_and_CPP_Projects](http://www.monodevelop.com/Creating_C_and_CPP_Projects)

---

### Post by lovinglinux on 2008-09-01
I used Code::Blocks on Windows for learning C/C++ 

It is easy to configure and use.

---

