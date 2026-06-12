---
title: "Compiling PolyPaint, GPL WhiteBoard"
date: 2008-06-27
forum: Packaging and Compiling Programs
---

### Post by transkinetic on 2008-06-27
PolyPaint is a program that allows people to work on one painting in real time over the internets. I'm trying to compile it but with no luck.
[http://smart-idiot.no-ip.com/polypaint/](http://smart-idiot.no-ip.com/polypaint/)
I installed Allegro-Dev and Bzip-Dev. I passed the compiler a flag to not make warning into errors. All to no avail. This looks like a really cool program. If anyone can get it working or has any suggestions, please let me know. I've been missing OpenCanvas on windows for its cooperative functionality. Painting with others is so much fun!

---

### Post by WW on 2008-06-27
> **transkinetic said:**
> ... All to no avail.
Well, what went wrong?  Show the commands that you used, and the errors that were printed.

---

### Post by transkinetic on 2008-06-27
Running make gives me the following error.
```
koopdi@koopdi-laptop:~/PolyPaint$ make
make: Nothing to be done for `all'.
```
I tried to reproduce my previous errors errors by deleting the Polypaint directory and extracting it again from the original archive but I'm still only getting the 'Nothing to be done for "all"' error.

---

