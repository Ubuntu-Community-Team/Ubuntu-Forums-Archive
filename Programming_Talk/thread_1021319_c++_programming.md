---
title: "c++ programming"
date: 2008-12-25
forum: Programming Talk
---

### Post by hezy00 on 2008-12-25
hello,
I've just installed a new ver. of ubuntu. I'ld like to have your advice about which compeiler to use at the beggining? Is there a system-build-in tool for that? thx,
hezy.

---

### Post by namdung on 2008-12-25
There are several IDEs available for C++. Search & install in *Add/Remove Applications*. Remember to select *All available applications*.

Take ur pick:[LIST]
[*]KDevelop
[*]Anjuta IDE
[*]Netbeans
[/LIST]

---

### Post by Sorivenul on 2008-12-25
Reading the Programming Talk stickies should help:
[How to Learn to Program FAQ, Linux Programming]("http://ubuntuforums.org/showthread.php?t=1006666")
[Programming Tolls and References]("http://ubuntuforums.org/showthread.php?t=1006662")
The short answer about the compiler is "g++", which should be installed with the "build-essential" metapackage. As far as IDEs go, the stickies also offer great suggestions.

Also, unless you are using C++ for university coursework or something similar, I wouldn't suggest beginning with C++. The stickies offer many suggestions of how to get yourself started, and the community here is very good.

Good luck!

---

### Post by tseliot on 2008-12-26
Moved to the Programming Talk.

---

### Post by jimi_hendrix on 2008-12-26
use gedit or vim to write the code then compile with

```

g++ -o executableName test.cpp tester.cpp
#this is a bash comment (comment in the shell)
#use this to run your new program
./executableName

```

---

### Post by monkeyking on 2008-12-26
sudo apt-get install build-essentials ...

---

### Post by meanburrito920 on 2008-12-26
The compiler and IDE are two separate things.

If you are asking which compiler to use, g++ is the standard. It is already installed with the base system. However, as has been mentioined, it does not include the build-essentials package, which includes basic headers and the such that are needed for compiling your files. monkeyking's post shows how to install build-essentials.

As for IDEs, I would suggest that you begin with gedit. It works wonders if you are just beginning, and if not it still has features for the more advanced user. However, if you are a more advance user and you would like to put down some time to learn tools you will always use, look into learning vim or emacs (imho you should go with emacs :-) ). 

For compiling your programs, bring up a terminal in the directory your source directory you are in and use g++. If you are unfamiliar with g++, run

$ man g++
or 
$ info g++

There are a plethora of options, but it should be relatively easy to figure out what parameters you need.

Hope that helps.

---

