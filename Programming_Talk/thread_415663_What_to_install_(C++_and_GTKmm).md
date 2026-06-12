---
title: "What to install? (C++ and GTKmm)"
date: 2007-04-20
forum: Programming Talk
---

### Post by shador on 2007-04-20
I'm using C++ and GTKmm in school for programming. We got it to work fine in WinXP but I would now like to switch to using ubuntu. 

What do I need to install to be able to use GTKmm and C++ in ubuntu? Anything special I need to do? 

It was quite tricky for us to get it to work on WinXP, I reccon it would be alot easier on Linux but I want to ask just in case =)

---

### Post by lloyd_b on 2007-04-20
First off, install the "build-essential" package (if it's not already installed).  This will provide you with the C & C++ compilers, as well as a bunch of other required build components (assembler, linker, etc).

Second, install the GTKmm library (and the associated "dev" package): "libgtk2.0-1c2a" and "libgtkmm2.0-dev".

Note that installing the "-dev" package may require you to install a bunch of other GTK related "-dev" packages - this is normal.

Lloyd B.

---

### Post by shador on 2007-04-21
Ok thanks, but what do I need to compile? Where do I write the code? On WinXP I used DevCpp to write and comiple n stuff.

EDIT: I've found out how to compile and write the code now the problem is running it =) As of now I'm dragging the created file after compiling the code into the terminal and the program runs. There's gotta be a better way right? Sorry for the stupid questions but I just want to get the flow of it yknow.

---

### Post by jlulian38 on 2007-04-24
cd to the directory and do

./[filename]

---

