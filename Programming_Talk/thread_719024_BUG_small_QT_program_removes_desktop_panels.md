---
title: "BUG: small QT program removes desktop panels"
date: 2008-03-08
forum: Programming Talk
---

### Post by KjSlag on 2008-03-08
I'm not sure if this is a QT widgets bug, or an ubuntu bug. Please move this thread if it should be somewhere else.


But anyways, running the sort file in the bad_sort.tar.gz archive from the terminal (by running "./sort") will make my screen flicker and then remove my panel (I only use one).
Running the program by double clicking on the sort file works fine.

The bad_sort.tar.gz archive contains a sort file that always works fine.

The difference between the two files is that the bad one has source files with capital letters, such as "SortDialog.cpp" and the good one has all lowercase letter file names (of course the #include headers are changed accordingly).

Note that the buttons aren't supposed to do anything.


My point is that disappearing panels seems to be a common problem and this simple program, which actually came from the QT manual, shouldn't create this kind of behavior (Ubuntu shouldn't be this fragile).

You can recompile with "make" if you delete the sort file. You can do a full recompile if you delete all the files that don't end in a .h or .cpp, delete the file that begins with _ui, and then run
qmake -project
qmake sort
make


Computer info:
Ubuntu 7.1 Gutsy
fully updated
Athlon 3500+
Radion x850 using the default open source fglrx drivers (not the propriety ones)
g++ version 4.3.2
fresh install of QT 4.3.2

---

### Post by mssever on 2008-03-08
Bug reports live on [http://bugs.launchpad.net](http://bugs.launchpad.net). It's unlikely that this thread will be seen by the proper people.

---

### Post by KjSlag on 2008-03-08
oops, forgot to include files

---

