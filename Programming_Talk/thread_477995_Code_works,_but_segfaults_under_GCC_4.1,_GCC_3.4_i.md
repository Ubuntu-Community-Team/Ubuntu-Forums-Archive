---
title: "Code works, but segfaults under GCC 4.1, GCC 3.4 is just fine"
date: 2007-06-18
forum: Programming Talk
---

### Post by montgoej on 2007-06-18
Okay, my problem is with this file [http://kyol.net/~hatc101/binstring.c](http://kyol.net/~hatc101/binstring.c) 
It compiles and works as expected under GCC 4.1 and GCC 3.4, but for some reason segfaults at the end if compiled with GCC 4.1. Anyone know why this happens and what can be done to fix this?
~Jordan Montgomery

---

### Post by joe_bruin on 2007-06-18
You're reading an int into a short (usually 32 bits into 16).  scanf()'s %d format reads an int.  Try changing the type of 'value' to unsigned int and changing the format to %u (unsigned int).

---

### Post by Smygis on 2007-06-18
jupp, Nothing to see heare, Move on peapole

---

### Post by montgoej on 2007-06-18
Thanks. My code is meant to work on 16 bit values, but doing those changes and changing binstring() to work on 32 bit values does work. BTW, the code is from C For Dummies: All-In-One Desk Reference by Dan Gookin. 
~Jordan Montgomery

---

### Post by vexorian on 2007-06-18
```
sudo apt-get install valgrind
```

Then run your 4.1 compiled program with valgrind from console like:


~@# valgrind ./myprogram

It should at least tell you suspicious lines of codes that got issues.


I once had issues with 4.1 and tinyxml, it was all about some changes in STL support


EdiT: DOH, I was unable to read the previous posts correctly, sorry for the unnecessary post.

---

### Post by Lux Perpetua on 2007-06-18
To scanf a 16-bit integer, use "%hd" instead of "%d".

---

