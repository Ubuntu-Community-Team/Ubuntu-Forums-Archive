---
title: "automatic compiling in eclipse"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by kobras on 2008-07-24
Hello!!!
I have installed eclipse and cdt. When i have tried to run it, appeared some window for configuration. I chose "Search Project", but it was empty, so i searched for g++, but now when i am trying to compile it, i am getting a message:
g++: no input files
I have read that its possible to make using the terminal, but its very hard.
is it possible to make it inside in eclipse(like in Turbo C++, for example)

---

### Post by LinuxRocks713 on 2008-07-31
Change compiling command to:

g++ *filename.cpp* -o *filename* -Wall

---

