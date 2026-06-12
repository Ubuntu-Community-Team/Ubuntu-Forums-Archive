---
title: "changing which automake is default"
date: 2006-01-20
forum: Programming Talk
---

### Post by oldmanstan on 2006-01-20
how do i go about changing which automake the computer uses by default (i need it to use 1.8 but it's set to 1.4), i know there's a variable to set or something just like with gcc, etc. but for the life of me i can't remember what it is

thanks

---

### Post by ganix on 2006-02-01
Hi, i have the same problem. no idea how to solve this the right way, i guess i can install a more recent version of automake with apt-get, right? but how?

---

### Post by slavik on 2006-02-01
this is what I did ...
use synaptic to install automake 1.9, and then use it to remove automake 1.4

the thing is that the 2 versions are separate packages (I don't see a reason for this) ... if you attempt to remove 1.4 it will give you an error about package dependancies.

---

### Post by oldmanstan on 2006-02-04
hmm, and that didn't break anything? i was worried about something needing a certain version, kinda like the kernel modules and what not

---

### Post by asimon on 2006-02-04
Doesn't
```
$ sudo update-alternatives --config automake
```
work?

---

