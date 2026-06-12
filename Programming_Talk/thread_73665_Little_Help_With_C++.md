---
title: "Little Help With C++"
date: 2005-10-09
forum: Programming Talk
---

### Post by YenningComity on 2005-10-09
Well I am on my second year of java and have dabbled in C++ however recently I have been using a beginner game programmers guide. It works well enough but as of yet I can't seem to get any of the programs to work in linux. I have been using Scite and Anjuta? (at my desktop which is windows so I cant check). Anyways neither will compile and throws up various errors so I was wondering if anyone could send me a nice link to a guide for linux. Nothing to teach me the language just enough so I can take what I have and move it over to linux and continue on. (this is basic stuff at the moment just output to the console really)

---

### Post by thumper on 2005-10-09
If you are just after simple stuff to and from the console, then I'd say compile from the command line.

```
g++ -o sample sample.cpp
```will create an executable called **sample**.

You need to make sure that you have the build-essential package installed first (or else it won't find g++).

Give that a go and get back with what happened.

---

### Post by YenningComity on 2005-10-09
g++: sample.cpp: No such file or directory
g++: no input files

that help?

---

### Post by Quartus on 2005-10-09
[QUOTE=thumper]You need to make sure that you have the build-essential package installed first (or else it won't find g++).
[/QUOTE]

```
sudo apt-get install build-essential
```

---

### Post by YenningComity on 2005-10-09
i glazed over that part I guess regardless it works now thanks all

---

### Post by thumper on 2005-10-10
[QUOTE=YenningComity]g++: sample.cpp: No such file or directory
g++: no input files

that help?[/QUOTE]
My guess is that you didn't actually have a C++ file called sample.cpp to compile first...

---

