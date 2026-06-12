---
title: "How do you learn makefiles?"
date: 2008-12-14
forum: Packaging and Compiling Programs
---

### Post by ColinGuy on 2008-12-14
Hi I getting into programing and I am writing a game in SDL and C but I want to package it and for that I need to write a makefile so how am I meant to write one.:confused: 
I have looked at the documentation, but it all looks very complex and hard to write for a simple project!    

Please Help!

---

### Post by linuxguymarshall on 2008-12-14
[http://tinyurl.com/5ozvv2](http://tinyurl.com/5ozvv2)

---

### Post by lensman3 on 2008-12-17
The easiest is to find a Makefile and copy it.  Makefiles always have the first letter M capitalized, otherwise, to run make and have it find the make file you have to do "make -f other_makefile_name".  Originally, the Makefile was capitalized so that it appeared near the top of a directory listing.

The other part that is hard to learn is that the lines that have a command on them, like gcc or c++ are always TABBED.  Never use spaces. You will get an error.

Once you get these two things, Makefiles are a cinch.   

Also learn the "make -i" command.  The dash-eye always does the make even if there are errors in the compile.

The other trick is the "make -n".  This way the make shows you what it is going to compile but not really do the compile.  It will show you the commands that will be executed.  Great for debugging.

Also learn the "touch" command.  It is almost as important as make.  The touch command changes the date/time of a file so that it can be made by make. But don't touch a dot-h file that has lots of dependencies or you will make the world.  Touch a file that doesn't exist and touch will create a zero length file with that name.

---

### Post by ColinGuy on 2009-01-03
Thx

---

### Post by monkeyking on 2009-01-04
there are also some built in vars in make files they are called

stuff like CC,CXX, CFLAGS CXXFLAGS

then you can substitute these at compile time using make like

```
make CC=icc CXXFLAGS="-ansi -pedantic"
```

---

