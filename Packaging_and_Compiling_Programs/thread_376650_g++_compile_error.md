---
title: "g++ compile error"
date: 2007-03-05
forum: Packaging and Compiling Programs
---

### Post by coldmeadow on 2007-03-05
Hi

Im trying to install from source a program which needs a GNU c++ compiler. I have build-essentials g++.  Unfortunately Im getting this error when make

g++ -O2 -I./libsrc/ -I./pedstats/ -I./pdf/ -o pedstats/Pedstats.o -c pedstats/Pedstats.cpp -DPEDVERSION=\"0.6.3\"
pedstats/PedstatsQuality.h:34: error: extra qualification ‘PedstatsQuality::’ on member ‘PedstatsQuality’
make[1]: *** [pedstats/Pedstats.o] Error 1


Would anybody be able to alert me to my problem? Please let me know if you require further info.

Very kindly appreciated

---

### Post by WW on 2007-03-07
That error is probably caused by a problem in the code you are compiling; apparently the code uses a class name qualifier within the class definition when it defines a member function.  This is now considered an error in g++.  It wasn't an error in older versions of g++. (Perhaps it would be better to say that the old versions of g++ had a bug, because they didn't flag the error?)

Try googling for "error: extra qualification" and browse through the first few links.  The very first one that I got was this mini-rant: [http://www.fourmilab.ch/fourmilog/archives/2006-05/000699.html](http://www.fourmilab.ch/fourmilog/archives/2006-05/000699.html)
It explains the problem pretty well.

---

