---
title: "Qt 4.0 and Gcc Problem"
date: 2007-07-07
forum: Programming Talk
---

### Post by open_coder on 2007-07-07
Hey guys. I have a very disturbing problem that I am desperately trying to fix. I installed all the libraries to develop with Qt4. I started to run through the Qt4 tutorials, found [here](http://doc.trolltech.com/4.0/examples.html). Well, the first one is a small hello world program. The code is below:

```
    /****************************************************************
    **
    ** Qt tutorial 1
    **
    ****************************************************************/
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
```

However, when I try to compile it, I receive the following error:

```

hello.cpp:7:28: error: QApplication: No such file or directory
hello.cpp:8:27: error: QPushButton: No such file or directory
hello.cpp:21:6: warning: no newline at end of file
hello.cpp: In function ‘int main(int, char**)’:
hello.cpp:14: error: ‘QApplication’ was not declared in this scope
hello.cpp:14: error: expected `;' before ‘app’
hello.cpp:16: error: ‘QPushButton’ was not declared in this scope
hello.cpp:16: error: expected `;' before ‘hello’
hello.cpp:17: error: ‘hello’ was not declared in this scope
hello.cpp:20: error: ‘app’ was not declared in this scope
```

I tried to figure out what was wrong, but as best I can tell, the problem is that gcc doesn't know where the libraries are installed at. How do I fix this? Is there a way to add the path to the libraries to gcc's search path?

Thanks guys,
--Alex

---

### Post by aks44 on 2007-07-07
From memory, this should work :

```
#include <QtGui/QApplication>
#include <QtGui/QPushButton>
```

then

```
g++ hello.cpp -o hello -I /usr/include/qt4 -l QtCore -l QtGui
```

---

### Post by open_coder on 2007-07-07
Thanks aks44. That worked.

---

### Post by Jucato on 2007-07-07
The other way would be to use qmake to compile it, which is, I think, the preferred way.

1. Make a directory for the project and put your source code in it. For example, name the directory hello. It will also be the name of the project.

```
mkdir hello
```

Put the source code (maybe you named it hello.cpp) inside that directory.

2. Go into that directory and make the project file

```
cd hello/
qmake -project
```

This will produce a .pro (project) file based on the name of the current directory, which would be hello.pro

3. Create a (platform-specific) Makefile based on the project file.

```
qmake hello.pro
```

4. Run make to compile the project:

```
make
```

Using this, you won't need to put "QtGui" in the #include lines, nor use the long g++ command with -I and -l switches. In fact, if you read through the whole page you pointed to, the same instructions on how to compile it is there. I only explained it a bit more. :)

---

### Post by open_coder on 2007-07-07
Alright. I finally have everything set-up.. But now I have a new question. If I use qmake, it tries to use the qmake for qt3. I can force Qt4 by using the qmake-qt4 command. When I ran the search, I found that three files exist with the qmake in /usr/bin/:

```
/usr/bin/qmake-qt3
/usr/bin/qmake-qt4
/usr/bin/qmake
```

Is there a way to fix this. I mean I could always symlink qmake to qmake-qt4, but I was wondering if there was another way of doing it. I don't really wanna screw with the files in that folder.

---

### Post by Jucato on 2007-07-07
```
sudo update-alternatives --config qmake
```

Then choose qmake-qt4.

Same goes for designer, assistant, and linguist.

---

### Post by mrchaotica on 2007-08-01
Thank you, OpenCoder and Jucato -- I had exactly the same problem.

However, I've got a new question: why is this so much harder than it needs to be? Why isn't there just a simple "qt4-devel" meta/virtual package we can install that would grab all the headers and tools and qdevelop and whatnot at once, and also run the appropriate 'update-alternatives' commands?

---

### Post by Jucato on 2007-08-01
>  Why isn't there just a simple "qt4-devel" meta/virtual...

There's the libqt4-dev package for that.

> and also run the appropriate 'update-alternatives' commands...

Because KDE 3.x and KDE 3.x apps require Qt 3.x. It is the default. Using Qt 4 is the exception. It would be wiser to keep the default in order to maintain stability, and let users who would need to use Qt 4 to manually change that if they need to. Just IMHO.

---

### Post by p3nn on 2008-05-22
Hi Guys

I ended up coming to another way around this prob. What i did was to create a bash shell script naming it q4make in my instance. The whole script reads

#! /bin/bash

/usr/share/qt4/bin/qmake $1 $2 $3 $4 $5 $6 $7 $8 $9




Then I right clicked and chose properties and in permissions set it to allow to execute. I tested in in the directory with

./q4make -4

to make sure it gave the right version. Then I opened nautilus via

gksu nautilus

and copied it into the /usr/bin directory. No more ./ before the command. Just type q4make (or whatever you choose to name it) instead of qmake

---

### Post by p3nn on 2008-05-22
slight error on the test line. It should read > ./q4make -v


---

