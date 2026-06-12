---
title: "error in qt programme compilation"
date: 2011-04-01
forum: Programming Talk
---

### Post by Praveen30 on 2011-04-01
After running qmake command i am getting this error---

[PHP]
praveen@praveen-laptop:~/projects$ qmake -project
praveen@praveen-laptop:~/projects$ qmake
praveen@praveen-laptop:~/projects$ make
Makefile:214: warning: overriding commands for target `main.o'
Makefile:211: warning: ignoring old commands for target `main.o'
Makefile:225: warning: overriding commands for target `main.o'
Makefile:214: warning: ignoring old commands for target `main.o'
Makefile:228: warning: overriding commands for target `main.o'
Makefile:225: warning: ignoring old commands for target `main.o'
/usr/bin/uic-qt4 hello/widget.ui -o ui_widget.h
make: /usr/bin/uic-qt4: Command not found
make: *** [ui_widget.h] Error 127
[/PHP]

how to remove it?????

---

### Post by GeneralZod on 2011-04-01
Have you installed libqt4-dev?

---

### Post by Praveen30 on 2011-04-01
> **GeneralZod said:**
> Have you installed libqt4-dev?

thanks for your reply...i am a newbie just started learning qt....i have installed qt from here--
[http://qt.nokia.com/downloads/](http://qt.nokia.com/downloads/)

Sorry to say but i don't know whether it is installed or not..how to look for this???

---

### Post by cgroza on 2011-04-01
To install it, just run this command into your terminal:
```

sudo apt-get install libqt4-dev
```

If it is not installed it will install it. If it is installed, it will tell you.

---

### Post by Praveen30 on 2011-04-01
> **cgroza said:**
> To install it, just run this command into your terminal:
```

sudo apt-get install libqt4-dev
```If it is not installed it will install it. If it is installed, it will tell you.

it was not installed so i have installed it----
My code is this--

[PHP]
 #include <QApplication>
 #include <QPushButton>

 int main(int argc, char *argv[])
 {
     QApplication app(argc, argv);

     QPushButton hello("Hello world!");
     hello.resize(100, 30);

     hello.show();
     return app.exec();
 }[/PHP]

after running qmake now i am getting this--

[PHP]
praveen@praveen-laptop:~/projects$ qmake -project
praveen@praveen-laptop:~/projects$ qmake
praveen@praveen-laptop:~/projects$ make
Makefile:218: warning: overriding commands for target `main.o'
Makefile:215: warning: ignoring old commands for target `main.o'
Makefile:229: warning: overriding commands for target `main.o'
Makefile:218: warning: ignoring old commands for target `main.o'
Makefile:232: warning: overriding commands for target `main.o'
Makefile:229: warning: ignoring old commands for target `main.o'
/usr/bin/uic-qt4 hello/widget.ui -o ui_widget.h
/usr/bin/uic-qt4 MyFirst/helloworlddialog.ui -o ui_helloworlddialog.h
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Ihello -IMyFirst -IMyFirst-build-desktop -I. -I. -o main.o MyfirstConsole/main.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Ihello -IMyFirst -IMyFirst-build-desktop -I. -I. -o widget.o hello/widget.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Ihello -IMyFirst -IMyFirst-build-desktop -I. -I. -o helloworlddialog.o MyFirst/helloworlddialog.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Ihello -IMyFirst -IMyFirst-build-desktop -I. -I. hello/widget.h -o moc_widget.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Ihello -IMyFirst -IMyFirst-build-desktop -I. -I. -o moc_widget.o moc_widget.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Ihello -IMyFirst -IMyFirst-build-desktop -I. -I. MyFirst/helloworlddialog.h -o moc_helloworlddialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Ihello -IMyFirst -IMyFirst-build-desktop -I. -I. -o moc_helloworlddialog.o moc_helloworlddialog.cpp
g++ -Wl,-O1 -o projects main.o main.o widget.o helloworlddialog.o main.o main.o moc_widget.o moc_helloworlddialog.o    -L/usr/lib -lQtGui -lQtCore -lpthread 
main.o: In function `main':
main.cpp:(.text+0x0): multiple definition of `main'
main.o:main.cpp:(.text+0x0): first defined here
main.o: In function `main':
main.cpp:(.text+0x0): multiple definition of `main'
main.o:main.cpp:(.text+0x0): first defined here
main.o: In function `main':
main.cpp:(.text+0x0): multiple definition of `main'
main.o:main.cpp:(.text+0x0): first defined here
collect2: ld returned 1 exit status
make: *** [projects] Error 1
[/PHP]

---

### Post by GeneralZod on 2011-04-01
Is main.cpp the only C++ file in your project?

---

### Post by Praveen30 on 2011-04-01
> **GeneralZod said:**
> Is main.cpp the only C++ file in your project?
  
yes...it is my first programme which i am trying to run..
i have written the code in gedit and save it as main.cpp then i have made a folder and put .cpp file inside it..
now i am trying to run qmake commands but i am getting these errors....

---

### Post by GeneralZod on 2011-04-01
I ask because I'm seeing weird references to "widget.o" and "helloworlddialog.o" in the output.

---

### Post by Praveen30 on 2011-04-01
> **GeneralZod said:**
> I ask because I'm seeing weird references to "widget.o" and "helloworlddialog.o" in the output.

oh..that was some applications which i have made on qcreator but i want to make this applications on without any ide...i think now it is clear--

[PHP]
praveen@praveen-laptop:~/projects/first$ qmake -project
praveen@praveen-laptop:~/projects/first$ qmake
praveen@praveen-laptop:~/projects/first$ make
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o main.o main.cpp
make: Circular all <- first dependency dropped.
g++ -Wl,-O1 -o first main.o    -L/usr/lib -lQtGui -lQtCore -lpthread 
praveen@praveen-laptop:~/projects/first$ 
[/PHP]

---

### Post by cgroza on 2011-04-01
If it works, mark as solved.

---

### Post by Praveen30 on 2011-04-01
> **Praveen30 said:**
> oh..that was some applications which i have made on qcreator but i want to make this applications on without any ide...i think now it is clear--

[PHP]
praveen@praveen-laptop:~/projects/first$ qmake -project
praveen@praveen-laptop:~/projects/first$ qmake
praveen@praveen-laptop:~/projects/first$ make
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o main.o main.cpp
make: Circular all <- first dependency dropped.
g++ -Wl,-O1 -o first main.o    -L/usr/lib -lQtGui -lQtCore -lpthread 
praveen@praveen-laptop:~/projects/first$ 
[/PHP]

i have updated my system and now this error is coming---
raveen@praveen-laptop:~/projects/first$ qmake -project
praveen@praveen-laptop:~/projects/first$ qmake
praveen@praveen-laptop:~/projects/first$ make
make: Circular all <- first dependency dropped.
g++ -Wl,-O1 -o first main.o    -L/usr/lib -lQtGui -lQtCore -lpthread

---

### Post by Praveen30 on 2011-04-01
> **cgroza said:**
> If it works, mark as solved.

definitely,i will but it is not working yet..i am still getting errors...

---

### Post by cgroza on 2011-04-01
> **Praveen30 said:**
> definitely,i will but it is not working yet..i am still getting errors...
I am not sure that is an error. Check if it generated a binary.

---

### Post by Praveen30 on 2011-04-01
> **cgroza said:**
> I am not sure that is an error. Check if it generated a binary.
there are some files--
main.cpp
main.o
makefile

when i open makefile there are some lines--
CC            = gcc
CXX           = g++
DEFINES       = -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED
CFLAGS        = -pipe -O2 -Wall -W -D_REENTRANT $(DEFINES)
CXXFLAGS      = -pipe -O2 -Wall -W -D_REENTRANT $(DEFINES)
INCPATH       = -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I.
LINK          = g++
LFLAGS        = -Wl,-O1
LIBS          = $(SUBLIBS)  -L/usr/lib -lQtGui -lQtCore -lpthread 
AR            = ar cqs
RANLIB        = 
QMAKE         = /usr/bin/qmake
TAR           = tar -cf

and this LIBS line is coming in error..frankly i don't know what does it mean....

---

### Post by GeneralZod on 2011-04-01
According to Google, it's because you're in a directory called "first", which, by a rather astonishing stroke of bad luck, appears to be a built-in term that Qt uses in its generated Make files.

Rename the directory and re-try.

Edit:

Although, according to my experiments, it should still be creating a binary, apparently called "first".  Can you post the complete list of files that are in that directory?

---

### Post by Praveen30 on 2011-04-01
> **GeneralZod said:**
> According to Google, it's because you're in a directory called "first", which, by a rather astonishing stroke of bad luck, appears to be a built-in term that Qt uses in its generated Make files.

Rename the directory and re-try.

Edit:

Although, according to my experiments, it should still be creating a binary, apparently called "first".  Can you post the complete list of files that are in that directory?

ok i have renamed it second...but still the error is same....

files are--
main.cpp
main.o
makefile
second (executable)
second.pro

and one interesting fact second.pro by default is opening in qt creator so when i press the run command then it displays the output....but on the terminal after typing make command same error is coming

---

### Post by cgroza on 2011-04-01
> **Praveen30 said:**
> ok i have renamed it second...but still the error is same....

files are--
main.cpp
main.o
makefile
second (executable)
second.pro

and one interesting fact second.pro by default is opening in qt creator so when i press the run command then it displays the output....but on the terminal after typing make command same error is coming

Maybe second is a reserved name too!:D:D Try renaming it to "chicken" or something.

---

### Post by GeneralZod on 2011-04-01
> **Praveen30 said:**
> 
files are--
...
second (executable)
...

Run this.

---

### Post by Praveen30 on 2011-04-01
> **cgroza said:**
> Maybe second is a reserved name too!:D:D Try renaming it to "chicken" or something.
  
no avail.same error is coming,,,,,,,,,,,,,

---

### Post by Praveen30 on 2011-04-01
> **GeneralZod said:**
> Run this.

it displays the output......:P

is this the way output comes in qt??? means everytime i have to click the executable file manually???

---

