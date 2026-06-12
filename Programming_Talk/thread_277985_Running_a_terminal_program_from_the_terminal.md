---
title: "Running a terminal program from the terminal?"
date: 2006-10-15
forum: Programming Talk
---

### Post by el__sid on 2006-10-15
Hey guys,

Straight to the point: I've just compiled a simple c++ program using g++, and when I open a terminal and try to run it, I can't!

I've placed the resulting executable (named the default a.out) in my home folder, however whenever I use the command "sh a.out" I get the reply:

"a.out: a.out: cannot execute binary file"

I've also tried not giving the file an extension with the -o option, only for the terminal to somehow skip the part where the program runs and bring me straight back to the prompt:S

The only way I've gotten it to run so far is to name the file with the .sh extension and "Run from terminal" by double clicking it, however I'd much rather be able to run it directly from the terminal, which surely must not be that hard considering I'm trying to run a CLI program?

Any way to make CLI programs run from a terminal? or am I doing something wrong?

---

### Post by skymt on 2006-10-15
"sh a.out" tries to run it as a shell script, which it isn't. You probably want "./a.out", which runs an executable "a.out" in the current directory.

---

### Post by el__sid on 2006-10-15
lmao thank you, that's exactly what I needed. My linux experience is showing again :P

---

### Post by bieber on 2006-10-15
It's alright, it's something we all go through.  Might I suggest that you add a -o flag to your compile command line, so you're not producing executables called a.out?  For instance, to compile lineup.cpp to an executable called lineup, one would run ```
g++ -o lineup lineup.cpp
``` and then ```
./lineup
``` to run the resulting program.

---

### Post by el__sid on 2006-10-15
As a rule, I normally do, however it's not worth it for the sake of debugging single functions.

I do my work at university normally, and their Linux Boxes have a GCPP flag set up so all I have to do is "gcpp myprogram.cpp" and it automatically names the exe the same as the source file name.

I have learned the lesson of taking things for granted today :P

---

### Post by duff on 2006-10-15
> **el__sid said:**
> 
I do my work at university normally, and their Linux Boxes have a GCPP flag set up so all I have to do is "gcpp myprogram.cpp" and it automatically names the exe the same as the source file name.


You can do this by adding
```
gcpp() { g++ $1 -o $(basename $1 .cpp) }
``` to your **.bashrc** file.

---

