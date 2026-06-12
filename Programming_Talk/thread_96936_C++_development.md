---
title: "C++ development"
date: 2005-11-29
forum: Programming Talk
---

### Post by slrafal on 2005-11-29
I'm looking for some advice regarding programming with C++ in Ubuntu. I'm a Comp. Sci. student learning the C++ language and essentially looking for an IDE. On campus we program in emacs which is okay but I would like something better.

Any opinions on Anjuta?

Second thing I need help with is, how do I make a C++ executable. At school, when I create the file.cc, all I have to type at the command line is *make file* and either I get errors or it simply makes an executable in my directory. But on my Ubuntu system, I get the following:

bash: make: command not found

I'm still a newbie to the Linux world, so could someone please help me out. Thank You.

---

### Post by darth_vector on 2005-11-29
it looks like make is not installed. do a:

sudo apt-get install build-essential

that will install make, the c/c++ compiler, the headers files and some other stuff. if you want to compile the thing manually you can type:

g++ -o name_of_executable source1.cc source2.cc ... sourcen.cc

EDIT: as for IDE's, vi is the bomb :)

---

### Post by slrafal on 2005-11-29
Once I manually compile these files - yeah they turn into executables but I assume the computer proecesses them so fast I truly do not see an output window.

---

### Post by darth_vector on 2005-11-29
if you compile from the terminal there wont be an output window. the output from the compiler, including compiler warning and so forth, will be printed in the terminal. if the code compiles without error you will get no output at all.

---

