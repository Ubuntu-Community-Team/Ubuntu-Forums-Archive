---
title: "C++/Qt Beginner"
date: 2011-07-20
forum: Programming Talk
---

### Post by shashanksingh on 2011-07-20
Hi, any experienced C++ and Qt developers please help.

Im trying to make a simple Qt application from scratch in C++, but Its hard to comprehend what's exactly happening. 
First, I read that a QApplication is the basic structure that handles lifecycle and event. This is how I made the QApp: 

main.cpp :-

```
#include <QtGui/QApplication>

int main(int argc,char ** argv)
{
	QApplication app(argc,argv);
	return app.exec();
}
```

This compiled fine.
The next step I read was to make a MainWindow, which will be my parent GUI Widget, on top of which ill make all.

I did make this as : MainWindow.h :-

```
#ifndef MAINWINDOW_H
#define MAINWINDOW_H

#include <QtGui/QMainWindow>

namespace Ui
{
	class MainWindow;
}

class MainWindow: public QMainWindow
{
	Q_OBJECT
	
	public:
		MainWindow(QWidget *parent = 0);
		~MainWindow();
			
	protected:
		
		void changeEvent(QEvent *e);
		
	private:
		Ui::MainWindow *ui;	//Pointer to self

	//slots will go here
		
};

#endif

```

This too compiled without any problems.
What is Difficult for me to understand is this: MainWindow.cpp (implementation of the mainwindow)

```

#include "MainWindow.h"

MainWindow::MainWindow(QWidget *parent) : QMainWindow(parent), ui(new Ui::MainWindow)
{
	ui->setupUi(this);
}

MainWindow::~MainWindow()
{
	delete ui;
}

```

When I compile the above, I get this:
> 
g++ -I /usr/include/qt4 -Wall -c "MainWindow.cpp"  (in directory: /home/shashank/workspace/Convert_C++)
MainWindow.cpp: In constructor MainWindow::MainWindow(QWidget*)’:
MainWindow.cpp:3:75: error: invalid use of incomplete type ‘struct Ui::MainWindow’
MainWindow.h:8:8: error: forward declaration of ‘struct Ui::MainWindow’


Maybe I should use make instead of g++, but my "make fundas" are nill, also read [this]("http://ubuntuforums.org/showthread.php?p=11068075#post11068075")

Thanks

---

### Post by karlson on 2011-07-20
> **shashanksingh said:**
> 
```
#ifndef MAINWINDOW_H
#define MAINWINDOW_H

#include <QtGui/QMainWindow>

namespace Ui
{
	class MainWindow;
}


#endif

```


What exactly are you trying to do with this?  

From here it looks like you are forward declaring class MainWindow, but nowhere in your code do I see declaration of class Ui::MainWindow.  The class MainWindow you have declared you have declared outside the scope of the namespace.

I would very seriously start with QT Designer and using qmake and uic to create the UI header files rather then trying to get them written by hand.

Also,

You might want to invest into [http://www.pearsonhighered.com/educator/product/C-GUI-Programming-with-Qt4/9780132354165.page](http://www.pearsonhighered.com/educator/product/C-GUI-Programming-with-Qt4/9780132354165.page)

---

### Post by shashanksingh on 2011-07-21
> **karlson said:**
> What exactly are you trying to do with this?  

From here it looks like you are forward declaring class MainWindow, but nowhere in your code do I see declaration of class Ui::MainWindow.  The class MainWindow you have declared you have declared outside the scope of the namespace.

I would very seriously start with QT Designer and using qmake and uic to create the UI header files rather then trying to get them written by hand.

Also,

You might want to invest into [http://www.pearsonhighered.com/educator/product/C-GUI-Programming-with-Qt4/9780132354165.page](http://www.pearsonhighered.com/educator/product/C-GUI-Programming-with-Qt4/9780132354165.page)

I actually got where I went wrong. I was trying to code a simple Qt app without the Qt Creator, just to get the feel of it first...

But the tutorial I refered to was the one that shows how to do it with Qt Creator.

Thats where the Ui::MainWindow comes into picture, and also the Multiple inheritence, sice I did not know about ui_mainwindow.h and how its created.

Anyways, thanks a lot for the link, but I really cant buy books because of financial constraints. 65$ is pretty high for us Indians.
Would be grateful for any great free learning material references.

Thanks. :)

---

### Post by shashanksingh on 2011-07-21
hey Karlson could you pls help me comprehend this?

I havn't even made the gui, I was just checking the QApplication and how to make an executable of it.

file: main.cpp
```

#include <QtGui/QApplication>

int main(int argc,char ** argv)
{
	QApplication app(argc,argv);
	return app.exec();
}
```

The above file compiles fine with g++, but heres what I got when I tried to link it to make an executable.

```
g++ -I /usr/include/qt4 main.cpp 

/tmp/cc2TmQ1z.o: In function `main':
main.cpp:(.text+0x25): undefined reference to `QApplication::QApplication(int&, char**, int)'
main.cpp:(.text+0x2a): undefined reference to `QApplication::exec()'
main.cpp:(.text+0x38): undefined reference to `QApplication::~QApplication()'
main.cpp:(.text+0x50): undefined reference to `QApplication::~QApplication()'
collect2: ld returned 1 exit status

```

I assumed that by including the qt4 library path, g++ may link and make the executable. That didnt happen.

But when I read online to write this and it worked, I got an executable:

```
qmake -project
qmake
make

```

even though I gave the qt4 path to g++, why couldnt it make it??

---

### Post by dwhitney67 on 2011-07-21
```

g++ -I /usr/include/qt4 main.cpp

```
The statement above instructs g++ to look at /usr/include/qt4 for additional header files.  These files are NOT to be confused with the Qt library itself.  The Qt library is presumably located in /usr/lib (or thereabouts).

You need to link with the Qt library, once you locate it.  Something like:
```

g++ -I /usr/include/qt4 main.cpp -lqt4

```
You should verify "qt4" above is correct.

---

### Post by shashanksingh on 2011-07-24
> **dwhitney67 said:**
> ```

g++ -I /usr/include/qt4 main.cpp

```
The statement above instructs g++ to look at /usr/include/qt4 for additional header files.  These files are NOT to be confused with the Qt library itself.  The Qt library is presumably located in /usr/lib (or thereabouts).

You need to link with the Qt library, once you locate it.  Something like:
```

g++ -I /usr/include/qt4 main.cpp -lqt4

```
You should verify "qt4" above is correct.

I tried finding the exact library but I failed to identify the exact path.
I tried -qt4, I tried:

```

g++ -I /usr/include/qt4 main.cpp -L /usr/lib64/qt4

g++ -I /usr/include/qt4 main.cpp -lqt4

```

both give me the same output:
```
/tmp/ccuef63c.o: In function `main':
main.cpp:(.text+0x25): undefined reference to `QApplication::QApplication(int&, char**, int)'
main.cpp:(.text+0x2a): undefined reference to `QApplication::exec()'
main.cpp:(.text+0x38): undefined reference to `QApplication::~QApplication()'
main.cpp:(.text+0x50): undefined reference to `QApplication::~QApplication()'
collect2: ld returned 1 exit status
```

So, I assume it isn't getting the library path, and Im really unable to recognize it from these possible paths:

```

/usr/lib/qt4
/usr/lib/qt4/plugins/accessible/libqtaccessiblecompatwidgets.so
/usr/lib/qt4/plugins/accessible/libqtaccessiblewidgets.so
/usr/lib/qt4/plugins/codecs/libqtwcodecs.so
/usr/lib/qt4/plugins/imageformats/libqtiff.so
/usr/lib/qt4/plugins/designer/libqt3supportwidgets.so
/usr/lib/qt4/plugins/graphicssystems/libqtracegraphicssystem.so
/usr/lib/qt4/plugins/script/libqtscriptdbus.so
/usr/lib/qt4/plugins/menubar/libappmenu-qt.so


```

I tried googling but maybe Im not doing it correctly...

---

### Post by dwhitney67 on 2011-07-24
I think you are approaching the solution to compiling a Qt application in the wrong direction.

I would suggest that you simplify the build process by creating a .pro file.  For example, say you create a file called *mygui.pro* with the following contents:
```

SOURCES += Main.cpp \
           MainWindow.cpp

HEADERS += MainWindow.h

TARGET       = mygui
DEPENDPATH  += .ui .moc
UI_DIR       = .ui
MOC_DIR      = .moc
OBJECTS_DIR += .obj

FORMS        =
IMAGES       =

TEMPLATE     = app
CONFIG      +=
INCLUDEPATH  = . .ui
LANGUAGE     = C++

```
Then use this file to generate a Makefile that can be used to build your project.
```

qmake mygui.pro     # Should only need to be done once, unless you edit the .pro file.

make

```
Of course, the code you posted earlier has syntax errors in it.  Correct those, polish up your C++ skills, and you should be ready to go.


P.S.  The Makefile produces statements such as the following; do you really want to enter a command like that for each file you want to compile?
```

g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I.ui -I.moc -o .obj/Main.o Main.cpp

```

---

### Post by shashanksingh on 2011-07-24
Thanks a lot.

Pretty clear now.
:)

Ive done most of my coding till date in java, I sure have to work a lot here.

---

### Post by benson444 on 2011-07-27
> **shashanksingh said:**
> Anyways, thanks a lot for the link, but I really cant buy books because of financial constraints. 65$ is pretty high for us Indians.
Would be grateful for any great free learning material references.

Thanks. :)

You can legally download a free, first edition (2006) PDF of the book that karlson recommended from [_http://www.qtrac.eu/marksummerfield.html_]("http://www.qtrac.eu/marksummerfield.html")

---

### Post by shashanksingh on 2011-07-28
> **benson444 said:**
> You can legally download a free, first edition (2006) PDF of the book that karlson recommended from [_http://www.qtrac.eu/marksummerfield.html_]("http://www.qtrac.eu/marksummerfield.html")

Thanks a lot..
Thats nice
:)

---

