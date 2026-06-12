---
title: "programming question"
date: 2011-10-11
forum: Programming Talk
---

### Post by coreyscx on 2011-10-11
can i use libre office to program in c++ then save as a .cpp file or is there something close to notepad++ on linux (i dont want to use an ide) and whats the command to compile on ubuntu using gcc (mingw) is it still g++ filename.cpp -o filename.exe?? obviously change the .exe to something else being its not windows but what?..

---

### Post by 11jmb on 2011-10-11
Any text editor will do the trick. gedit and emacs do syntax hilighting for C and many other languages

and yes, the simplest way to compile c++ in Ubuntu is g++

for other compiler options consult the man page


a general thread-use note: please try to use a more descriptive title for the thread such as "c++ text editor".

---

### Post by karlson on 2011-10-11
> **coreyscx said:**
> can i use libre office to program in c++ then save as a .cpp file or is there something close to notepad++ on linux (i dont want to use an ide) and whats the command to compile on ubuntu using gcc (mingw) is it still g++ filename.cpp -o filename.exe?? obviously change the .exe to something else being its not windows but what?..

You could do this but why use a tank to put a nail in?

There are quite a few alternatives for text editors, emacs, vi, gvim, gedit, kate.

If you want to you can take a look at Eclipse, code::bloks, Anjuta for IDEs

---

### Post by Vaphell on 2011-10-12
> **coreyscx said:**
> is it still g++ filename.cpp -o filename.exe?? obviously change the .exe to something else being its not windows but what?..

whatever you wish, in linux any file can be marked as executable. File names don't carry any weight here, executable bits do. More often than not programs don't have any extension - just like in /usr/bin where tons of programs reside.

---

### Post by DarkAmbient on 2011-10-12
+1 on gedit. Comes with Ubuntu, got syntax highlighting, you can enable line rownumbers and automatic indentation. It also has lots of plugins you can enable.

Compile in terminal, I use gcc. 

First cd (change dir) to your .cpp file
```
cd path/to/folder/containing/the/file
``` 

build with
```
gcc file.cpp -lstdc++ -o appname
```

then run your app in terminal using
```
./appname
```

---

