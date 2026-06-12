---
title: "Programing a window in Ubunto 9.10"
date: 2009-11-20
forum: Programming Talk
---

### Post by Bat-man on 2009-11-20
Hello, I would like to slowly get into making applications in Ubuntu using C.
I wold like to know the simplest way to make a window.
Just a regular, blank window with the three buttons at the top right for minimize maximize and close.

Thank you in advance!

---

### Post by scragar on 2009-11-20
[http://doc.trolltech.com/4.3/tutorial-t1.html](http://doc.trolltech.com/4.3/tutorial-t1.html)
```
 #include <QApplication>
 #include <QPushButton>

 int main(int argc, char *argv[])
 {
     QApplication app(argc, argv);

     QPushButton hello("Hello world!");
     hello.resize(100, 30);

     hello.show();
     return app.exec();
 }
```In a terminal:
```
mkdir t1
cd t1
gedit main.cpp
qmake -project
qmake
make
./t1
```

---

### Post by Bat-man on 2009-11-20
Testing it out now

---

### Post by Bat-man on 2009-11-20
./t1.pro: line 5: TEMPLATE: command not found
./t1.pro: line 6: TARGET: command not found
./t1.pro: line 7: DEPENDPATH: command not found
./t1.pro: line 8: INCLUDEPATH: command not found
./t1.pro: line 11: SOURCES: command not found


This is what i get when i run ./t1

---

### Post by scragar on 2009-11-20
Nope, t1.pro is the project file, you don't run that. If you do ```
ls
```You should see the executable or just 3 files(main.cpp the makefile and the t1.pro file), if there's only those 3 run ```
make
``` to build the program.

The executable is just called t1

Step by step, with comments(not missed anything this time :p):
```
mkdir t1 **## make the directory**
cd t1 **## enter the directory**
gedit main.cpp **## edit your file**
qmake -project **## generate the project file**
qmake **## create the makefile based on the project file**
make **## have make do the building for you**
./t1 **## test the program**


```

---

### Post by CptPicard on 2009-11-20
The example is C++, not C. Qt is a C++ library. OP should be looking at GTK instead...

---

### Post by Bat-man on 2009-11-20
Thank you! It was the dependencies that were messing with me.
I didn't have the gcc ++ compiles for C++.

Where would a guy go to read up on some beginner Linux application development?

---

### Post by diesch on 2009-11-20
See [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/) and [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/) for how to use Gtk

---

### Post by Bat-man on 2009-11-20
Thank you :)
I will look into this stuff and probably ask a whole bunch more questions regarding the subject.

---

