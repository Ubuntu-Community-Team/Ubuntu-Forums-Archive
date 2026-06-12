---
title: "What does &quot;Cannot locate flex binary&quot; mean?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by gsschenk on 2008-10-20
I'm a college student in an electrical engineering course that requires us to install a simulator of a very basic computer called the LC-3. I recently switched over to Ubuntu 8.04 and when I tried installing the simulator through the instructions given on the course website the terminal gave me "Cannot locate flex binary". What does that mean? How can I fix it?

The instructions for installing the program are here: [http://courses.ncsu.edu/ece109/common/lc3linux.html](http://courses.ncsu.edu/ece109/common/lc3linux.html)

---

### Post by Titan8990 on 2008-10-20
I would assume that "flex" is a program/file that you do not have installed. Those instructions are poor at best.

Evan the readme lacks information telling you that you need this binary. The only way I was able to verify that it needs it was by looking at the code in the configure file:

```
# Some binaries that we'll need, and the places that we might find them.

binlist="uname flex gcc wish rm cp mkdir chmod sed"
pathlist="/bin /usr/bin /usr/local/bin /sw/bin /usr/x116/bin /usr/X11R6/bin"
libpathlist="/lib /usr/lib /usr/local/lib"
incpathlist="/include /usr/include /usr/local/include"

```

Try:

sudo apt-get install flex

---

### Post by gsschenk on 2008-10-20
alright i did that and now it gave me "Cannot locate wish binary".

---

### Post by Titan8990 on 2008-10-21
Not in front of a machine but try:


sudo apt-get install wish

---

### Post by gsschenk on 2008-10-22
Ok. That gives me this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wish is a virtual package provided by:
  tk8.5 8.5.0-3
  tk8.3 8.3.5-12ubuntu1
  tk8.4 8.4.16-2ubuntu1
You should explicitly select one to install.
E: Package wish has no installation candidate

I tried adding those onto it but I'm not sure I know the right way to do that. Any suggestions?

---

### Post by adamcollac on 2009-01-27
sudo apt-get install tk8.5
then make
get error about -lcurses 
so if you need to then-->
                            sudo apt-get install libncurses5-dev

---

