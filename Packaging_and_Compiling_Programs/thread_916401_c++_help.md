---
title: "c++ help"
date: 2008-09-10
forum: Packaging and Compiling Programs
---

### Post by Roeyfreak10 on 2008-09-10
so i just started learning c++

and i was on another computer before it was running xp
so i was using dev-c++ to write up all the code and then compile it
and then create an execeutable out of it but now im on my computer at home
running ubuntu 8.04 so i need a program that can do the same. any suggestions?

---

### Post by cszikszoy on 2008-09-11
You should post this in the Programming Talk forum.  This section is mainly meant for the packaging and compiling of ubuntu software.

```
sudo apt-get install build-essential
```

This will install the c/c++ compiler.  To write programs just open gEdit and compile with g++

ie, if your source file is a.cpp

```
g++ ./a.cpp -o a
```

This will compile a.cpp and create an executable called "a" in the same directory.  If you are looking for something more like a visual editor, search the forums for "c++ IDE".  There are many, many threads in the Programming Talk forum about C++ IDEs

---

### Post by ilrudie on 2008-09-11
> **cszikszoy said:**
> You should post this in the Programming Talk forum.  This section is mainly meant for the packaging and compiling of ubuntu software.

```
sudo apt-get install build-essential
```This will install the c/c++ compiler.  To write programs just open gEdit and compile with g++

ie, if your source file is a.cpp

```
g++ ./a.cpp -o a
```This will compile a.cpp and create an executable called "a" in the same directory.  If you are looking for something more like a visual editor, search the forums for "c++ IDE".  There are many, many threads in the Programming Talk forum about C++ IDEs

+1
I use vi to edit code.  Its complicated (takes a while to get even basic editing down) but powerful.  Any text editor should work and if you look around the programming talk area I believe there is a sticky about IDEs and text editors.

---

