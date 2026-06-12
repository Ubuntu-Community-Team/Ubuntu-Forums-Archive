---
title: "Geany Build Problems"
date: 2008-02-23
forum: Programming Talk
---

### Post by pmaconi on 2008-02-23
I am trying to compile, build, and execute a file that has a space in its name. For example, my file is Assignment 5. It works fine if I rename it to Assignment5, but I'm hoping that there is a way to configure Geany to work fine with a file that includes spaces.

Trying to build such a file gives me this error:
g++ -Wall "Assignment 5.cpp" -o Assignment 5 (in directory: /home/pmaconi/SE 102)
g++: 5: No such file or directory

---

### Post by themusicwave on 2008-02-23
You have to escape the spaces 

I think place \<space> in for each space.

It should work then.

try:
g++ -Wall\ Assignment\ 5.cpp -o

also try using the tab key for auto complete

type g++ Wall then hit tab

Good luck,

Jon

---

### Post by pmaconi on 2008-02-23
My problem isn't with g++ - I'm not actually typing the commands in. Geany auto inserts the entire line (and doesn't have a configuration tool for the -o part). I'm specifically looking for a place to edit how Geany inserts the -o.

---

### Post by amingv on 2008-02-23
This thread has made me fiddle once again with Geany; I've found out two more things:

1. I dislike Geany more than I believed I did...
2. This has been taken care of. Download the latest stable version (v0.13) or the development version, if you feel adventurous, from [http://geany.uvena.de/Main/HomePage](http://geany.uvena.de/Main/HomePage). (The version in the repos is v0.11-2)

I really suggest compiling from the command line from time to time, but do what's best for you.

---

### Post by pmaconi on 2008-02-23
Thanks.

---

