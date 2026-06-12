---
title: "Geany build error"
date: 2007-05-11
forum: Programming Talk
---

### Post by lognok on 2007-05-11
Hi there,
  I'm just learning to program in c++ and I'm using Geany to build a simple three-file program that I found at: [http://ubuntuforums.org/showthread.php?t=421056&highlight=header](http://ubuntuforums.org/showthread.php?t=421056&highlight=header) it's the last post posted by baltimark.
  Copy and paste (test.h + test.cpp + main.cpp) into Geany gives me the following error:

g++ -Wall "main.cpp" -o main (in directory: /home/qaim/Programming/GDA)
/tmp/ccg8VGfQ.o: In function `main':
main.cpp:(.text+0x84): undefined reference to `testReturn()'
collect2: ld returned 1 exit status
Compilation failed.

What's going on here?
This exact code runs fine in Code::Blocks

Do I need to make some kind of 'project' in Geany or custom Makefile?

Thanks for any reply

---

### Post by lognok on 2007-05-13
Solved:
  Had to make a 'Makefile' including this command:

all: g++ file1,cpp file2.cpp file3.cpp -o file1

Now I just press Shift+F9 (make all) and it makes/builds the files. :) 

Note: it still displays errors when pressing F9 (build). Also no build/make without my custom Makefile.

---

