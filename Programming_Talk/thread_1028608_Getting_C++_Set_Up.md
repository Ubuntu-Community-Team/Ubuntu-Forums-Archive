---
title: "Getting C++ Set Up"
date: 2009-01-02
forum: Programming Talk
---

### Post by insilicium on 2009-01-02
I'm trying to get set up with C++ for a class that starts this upcoming semester.  I am running Hardy and followed the directions at [https://help.ubuntu.com/8.04/programming/C/build-essential.html](https://help.ubuntu.com/8.04/programming/C/build-essential.html) and installed build-essential and anjuta.  However, I can't seem to get hello world to work!  If I compile using Anjuta, I'll get a .o file, but it won't run - it says ~/hello is not a local file.  If I try to compile using the command g++ hello.cpp, it creates a new file called a.out and that's it.  What am I missing or doing wrong?

Also, my apologies if this has already been asked - I searched the forum but didn't find anything quite the same.

---

### Post by aJayRoo on 2009-01-02
The a.out file created by g++ is your compiled program. You can run it by typing ```
./a.out
``` in to the terminal after running the compile command. You can choose to name the program something else by using the -o switch at compile time:
```
g++ -o myprogram hello.cpp
```
Hope that helps.

---

### Post by stevescripts on 2009-01-02
As a bit of an addition to what aJayRoo posted - a suggestion especially for beginning ....

Start your c++ programming by using a simple editor (such as GEDIT), and learning to compile/build from the command line.  Once you have a good feel for using c++ in that manner, *then* move on to the IDE of your choice.

Steve

---

### Post by slavik on 2009-01-02
Please read the stickies, they contain how tos on getting C and C++ compilers set up.

---

### Post by kavon89 on 2009-01-02
Other than setting up a nice folder backup script for where all your code is, there isn't much to set up for C++ since you'd be using g++ to compile and something like gedit is fine for an editor.

---

### Post by slavik on 2009-01-03
> **kavon89 said:**
> Other than setting up a nice folder backup script for where all your code is, there isn't much to set up for C++ since you'd be using g++ to compile and something like gedit is fine for an editor.
or a versioning system ;)

---

