---
title: "etags in emacs"
date: 2010-08-19
forum: Programming Talk
---

### Post by gaurish108 on 2010-08-19
Hi I am new to learning C and C++. I use the editor Emacs. Someone told me etags is very useful in Emacs while understanding a long code.

Could someone tell me how to use etags, and the concept of a tags table. Does tags mean the functions/ routines I define in C/C++ or something more?

Thank you

---

### Post by lordhaworth on 2010-08-19
The link below gives a reasonable description of both what it does and how you do it. I use emacs but had never used etags (despite my working on some large code) - I think I will give it a try! 

[http://www.linuxjournal.com/article/153](http://www.linuxjournal.com/article/153)

---

### Post by cthulhu_54 on 2010-08-19
All you need to know is:
```
etags file.cpp
```
Then when you're in flie.cpp pressing M-.  (dot) will let you search all your function/class declarations, and M-* takes you back to where you were. If the marker is on a function/class/whatever it will default to search for that function. I love it.

---

