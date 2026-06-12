---
title: "searching for a complier"
date: 2008-03-12
forum: Programming Talk
---

### Post by hasanyaman on 2008-03-12
hi friends
i started C a week ago but didnt give a decision what to use
if it is possible to use Dev C++ Complier  in ubuntu ,,i want to use this
please help

---

### Post by wblancqu on 2008-03-12
"Bloodshed Dev-C++ is a full-featured Integrated Development Environment (IDE) for the C/C++ programming language. It uses Mingw port of GCC (GNU Compiler Collection) as it's compiler. Dev-C++ can also be used in combination with Cygwin or any other GCC based compiler."

So just use gcc:

```
sudo apt-get install build-essential gdb
```

will install all the stuff you need.

Grtz

---

### Post by pmasiar on 2008-03-12
See sticky FAQ about how to pick first language to learn - by opinion of many Python is easier to learn than C. Either way, see other discussions in forum about websites with training problems to solve. Good luck!

---

### Post by hasanyaman on 2008-03-12
thanks for information

---

### Post by akudewan on 2008-03-12
I made my first real program using C++/Qt and using the kdevelop IDE. Found it very easy to use, especially for debugging. Maybe you could give it a shot...

---

### Post by LaRoza on 2008-03-12
> **pmasiar said:**
> See sticky FAQ about how to pick first language to learn 

Also for getting and using the compiler, which is in the sticky.

---

### Post by Achetar on 2008-03-12
The best Development Environment that I have found for GNOME/XFCE4 is Anjuta. it can be obtained by typing the following in a terminal:
```
 sudo apt-get install anjuta
```
There are several plugins you should turn on to get the full functinality:
*Terminal
*Debugger(duh!)
*DevHelp (useful if you have devhelp and API docs installed)
There are more if you ever need them.

---

