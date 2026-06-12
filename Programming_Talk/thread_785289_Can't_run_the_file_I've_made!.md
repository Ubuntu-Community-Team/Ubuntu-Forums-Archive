---
title: "Can't run the file I've made?!"
date: 2008-05-07
forum: Programming Talk
---

### Post by Stonehambey on 2008-05-07
Hi, I've made a couple of test programs using C++ and I've got my executable.

The only thing is...I can't run it. O_o

I try double clicking on it, and nothing happens. I try running it from the command line, and nothing happens. I should add that I've only just started using Ubuntu and so I might be missing out on something.

Also, save starting another thread I might as well ask it here. How does one go about building a project with multiple files using the command line? Say I wanted to build a program consisting of class.h, class.cpp and main.cpp, how would I do that? At the moment I'm building single files like this

```
g++ ./filename.cpp -o filename
``` 

Any help on these two questions/problems would be much appreciated, thanks :)

Stonehambey

---

### Post by Kadrus on 2008-05-07
mm..lets say that you created a file called ex.cpp..
compile it using g++ ex.cpp
then run it using ./a.out ..it should work..

---

### Post by Stonehambey on 2008-05-07
Ah yes, that seems to run the program in the terminal, thanks

If I may be so bold, could you possibly explain to me what the command "./a.out" actually does.

And also, how would I run the program in a separate window? For I will be making GUI applications using the SDL libraries, would these run in the terminal as well?

Thanks :)

---

### Post by Kadrus on 2008-05-07
mm..yeah..you compile all your programs from terminal and they run..let's say if you're making a GUI program using GTK you compile it and then u see your program and all its graphical features..and  for the ./a.out read
[A.out]("http://en.wikipedia.org/wiki/A.out")

---

### Post by WW on 2008-05-07
If you compiled your program like this
```
g++ ./filename.cpp -o filename
``` 
then to run it, you can do this in the terminal:
```
$ ./filename
```
The **-o filename** option tells the compiler/linker to call the executable program **filename**. If you don't give this option, the default name is **a.out**.

By the way, putting ./ in front of the source code file name is superfluous.  This should work:
```
g++ filename.cpp -o filename
```
When you run the program with **./filename**, you need **./** in front of the name because, by default, the terminal shell will not look for executable files in the current directory.  In Linux, the dot (**.**) refers to the current directory.

---

### Post by Stonehambey on 2008-05-08
Thanks to both of you, I can run them now :)

---

