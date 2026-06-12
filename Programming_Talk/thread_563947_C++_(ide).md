---
title: "C++ (ide)"
date: 2007-09-30
forum: Programming Talk
---

### Post by yyz on 2007-09-30
Hello everyone.
I'm learning C++ programming, I started to learn today. Can I run the programs I make with C++ code by using Xubuntu's Mousepad application? Or do I need an IDE. I installed KDevelop from the add/remove programs sub-menu. I don't know if this will do it.

Note: I've heard such tips that its better to use a simple text program when writing code, instead of using an IDE application.

Thanks to all :)

---

### Post by Lord Illidan on 2007-09-30
If you're just starting, then it's better just to use a text editor, in my opinion. If you want to use an IDE, I recommend geany..very useful!

Kdevelop needs some other utilities to compile programs too.

Did you install build-essential?

---

### Post by yyz on 2007-09-30
> **Lord Illidan said:**
> If you're just starting, then it's better just to use a text editor, in my opinion. If you want to use an IDE, I recommend geany..very useful!

Kdevelop needs some other utilities to compile programs too.

Did you install build-essential?

Thank you for your reply

Well, the package contains these lot:

KDevelop Asistant, 
KDevelop C/C++, 
KDevelop Designer,  
KDevelop: KDE/C++, 
KDevelop: Multilanguage, 
KDevelop: Ruby, 
KDevelop Scripting.

---

### Post by Lord Illidan on 2007-09-30
Yes. It also needs autogen and automake, I think.

But first, install build-essential before you even think about compiling a program, as it contains the compilers you need.

The terminal command is :

```
sudo apt-get install build-essential
```

You can use mousepad, as well.

---

### Post by yyz on 2007-09-30
Hello, thank you for the program. I am concerned about one else thing. When I'm using the Mousepad application to write my code, after saving the source code with the file extension 'cpp', how will I run my program?

---

### Post by Lord Illidan on 2007-09-30
Let's say you saved it as helloworld.cpp

Go to the terminal, cd to the location of the program, and then type :

```
g++ helloworld.cpp -o helloworld
```

This will compile the program, and create an executable.

Then run ```
./helloworld
```

---

