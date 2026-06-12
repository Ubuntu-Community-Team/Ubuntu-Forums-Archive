---
title: "Multi-threading in C"
date: 2007-06-28
forum: Programming Talk
---

### Post by christoforever on 2007-06-28
hey guys i didnt know where to post this, but this seemed as good a place as any. Are there any libraries for multi-threading in C? I've been doing java programming for quite some time, seeing as this is all they teach at my university. I've just recently got back into programming in C, and couldent find any good sources for multi-threading. Any help would be greatly appreciated, or a point in the right direction.

sincerely,
Chris Dancy

---

### Post by slavik on 2007-06-28
man pthreads :)

---

### Post by WebDrake on 2007-06-28
The basic mechanism is pthread.h: 
[http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html)
[http://www.opengroup.org/pubs/online/7908799/xsh/pthread.h.html](http://www.opengroup.org/pubs/online/7908799/xsh/pthread.h.html)

There's also GNU Pth:
[http://www.gnu.org/software/pth/](http://www.gnu.org/software/pth/)

---

### Post by karthikbalaji on 2007-06-29
Thanks a lot for the links man..Nice tutorial..Will be of a great help to me

---

### Post by KaeseEs on 2007-06-29
A nice feature you get by using Pthreads is ease portability, as a very good (and GPL, too!) Pthreads implementation exists for w32, in addition to every unix supporting it natively.

---

### Post by g3k0 on 2007-06-29
Don't forget those mutex locks... otherwise you will get some crazy numbers and have no idea where they are coming from.

---

### Post by christoforever on 2007-07-06
Just wanted to say thanks for all the help. Its a great step in the right direction.:popcorn:

---

