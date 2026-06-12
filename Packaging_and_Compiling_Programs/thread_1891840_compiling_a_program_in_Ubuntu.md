---
title: "compiling a program in Ubuntu"
date: 2011-12-06
forum: Packaging and Compiling Programs
---

### Post by ryoussef on 2011-12-06
Hi, I'm trying to compile a program using the Terminal in Ubuntu but it doesn't work .. can someone help please? I've been trying for sooo long Im starting to just to exhausted of trying, The source code That I'm trying to compile in this link. [http://fabathome.org/installers/](http://fabathome.org/installers/). 

Source code is also attached.

it shows that its the source code once you see it.. If anyone can send me some kind of instructions to how this process goes I would be very grateful. 

Thanks ,

---

### Post by deonis on 2011-12-06
Is it QT based ? if so you will need to have QT dev libs and to compile it you will need to type the following:
qmake (qt-version here) make

---

### Post by ryoussef on 2011-12-07
How would I know if it's QT based ? and how do I get QT dev libs ?

---

### Post by deonis on 2011-12-07
it's written in the name of your program. Can you try to build it and post the output in here ... thanks

---

### Post by cgroza on 2011-12-07
Usually, the installation instructions are present in one of the files.
I am not sure which, but the chances are it's either README or INSTALL.

---

### Post by deonis on 2011-12-07
Do you know that you have already a build copy in the bin folder ? and it actually works !  Make it executable and run it....

---

