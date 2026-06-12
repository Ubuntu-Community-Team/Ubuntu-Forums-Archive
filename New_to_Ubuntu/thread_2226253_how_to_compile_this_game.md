---
title: "how to compile this game?"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by vivek_roy on 2014-05-26
Im new user of ubuntu and not familiar with linux. I've just downloaded a game from [http://sourceforge.net/projects/classicsudoku/?source=directory](http://sourceforge.net/projects/classicsudoku/?source=directory) . and dont know how to compile it. coz there is not configure file. and autogen.sh command shows "autogen.sh: command not found". Im totally confused. 
HELP!

---

### Post by howefield on 2014-05-26
Are you aware that a default install of Ubuntu includes a sudoku game ?

---

### Post by vivek_roy on 2014-05-26
I know  there is many games in Ubuntu software center. But I want to compile it for learn Linux for future usage. And from now I don't want to use Microsoft windows. Never.

---

### Post by spjackson on 2014-05-26
If you have the right packages installed for compiling Qt4 programs, this should work:
```

unzip sudoku_classic_0.9.1_beta_source.zip
cd 0.9.1/sudoku
qmake
make

```

---

### Post by vivek_roy on 2014-05-26
qmake: could not find a Qt installation of ''                  NOW WHAT IS THIS?

---

### Post by vivek_roy on 2014-05-26
vivek@vivek-N61PB-M2S:/usr/local/src/0.9.1/sudoku$ make
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -I../../../../share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o main.o main.cpp
main.cpp:1:24: fatal error: QApplication: No such file or directory
 #include <QApplication>
                        ^
compilation terminated.

---

### Post by spjackson on 2014-05-26
Well, I did say "[COLOR=#000000]If you have the right packages installed for compiling Qt4 programs". What you need to get there depends on what you have installed and what platform you are on. For a fresh install of 14.04, the required commands to get here are:
```

sudo apt-get install build-essential
sudo apt-get install qt4-dev-tools

```
Then proceed as per my previous post. For me, the resulting program crashes on program startup, but I haven't tried to debug it.
[B]
Edit:[/B] It doesn't crash if you take -O2 out of the Makefile and make it again.
 
[/COLOR]

---

### Post by su:bhatta on 2014-05-26
> Qt is a cross-platform C++ application framework. Qt's primary feature
is its rich set of widgets that provide standard GUI functionality.

Did you take a look here : [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
Step 3 :Resolving dependencies section of that page is what you are getting stuck at.

---

