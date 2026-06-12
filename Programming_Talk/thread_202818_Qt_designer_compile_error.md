---
title: "Qt designer compile error"
date: 2006-06-24
forum: Programming Talk
---

### Post by Kakistos on 2006-06-24
I've been following the Qt designer online manual.  Going through the quick start I've been making the conversion program.

I cd to the drive as a su, and type in 

qmake -o Makefile Metric.pro

and I get the Makefile, I then type in 

make

and get the following

root@Daffy-Duck:~/Desktop/Programs/Metric# make
/usr/share/qt3/bin/uic conversionform.ui -o conversionform.h
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o main.o main.cpp
make: g++: Command not found
make: *** [main.o] Error 127

So I was wondering what the error was, and how I finish creating this project.

Thanks in advance

Chris :-D

---

### Post by hod139 on 2006-06-24
Have you installed the build-essential package?

---

### Post by Kakistos on 2006-06-24
Yeah that was it thanks.  

C ;0)

---

### Post by snisarg on 2011-04-12
I am getting the same error. I am new to Qt, can someone please elaborate as to what's wrong and how can i solve the problem.

---

### Post by Iowan on 2011-04-12
Closed...
Please start a new thread.

---

