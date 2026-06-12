---
title: "compiling c programs"
date: 2006-06-24
forum: Programming Talk
---

### Post by zexoc on 2006-06-24
ive been looking through the help files on 5.10 on how to compile c programs but havent found any.

could someone please give advice on how to compile c and c++ programs in ubuntu?

do i need a separate IDE or can i use a text editor and a compiler < if so how?

also once compiled how do i run it?

thanks in advance

---

### Post by voitrix on 2006-06-24
Hi, first of all you need to install g++, just open a terminal window and write
      sudo apt-get install g++
once the g++ is installed you can compile a .cpp file by typing
      g++ -o filename1 filename.cpp
where filename1 will be name of the executable file, to run the filename1 you have to type
       ./filename1

---

### Post by Revert on 2006-06-24
Even better would be to just sudo apt-get install build-essential.  It'll get you most everything you need for C/C++ compiling and the like.

---

### Post by zexoc on 2006-06-24
thanks for the replies.

ive installed build essential, is there any documentation or tutorial on it for a newbie in compiling ?

---

### Post by ynef on 2006-06-24
The 6 second newbie tutorial:

If you have a C source file called program.c you want to compile, write "make program".

The same goes for C++ files (if they are named something.cpp). "make" will figure out the command that should be used. 

Is there anything in particular you need help with?

---

### Post by zexoc on 2006-06-25
thanks for the tutorial, it was helpful

I downloaded and installed Anjuta too

---

