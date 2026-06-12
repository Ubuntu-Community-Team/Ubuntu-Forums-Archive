---
title: "QT3 'Hello world' failure"
date: 2007-03-03
forum: Programming Talk
---

### Post by LordOfTheCows on 2007-03-03
Hey all,

I am trying to compile the 'Hello world' example from qt3 to no avail (note : I know we are now at qt4, but external pressures compel me to use qt3). From what I could gather, I think this is a problem with the way that the qt3 packages are configured in Ubuntu (6.10) since the same procedure works like a charm on my work computer (mac osx with qt3).

Here is the simple example :
```
#include <qapplication.h>
#include <qpushbutton.h>

int main( int argc, char **argv )
{
    QApplication a( argc, argv );

    QPushButton hello( "Hello world!", 0 );
    hello.resize( 100, 30 );

    a.setMainWidget( &hello );
    hello.show();
    return a.exec();
}
```

Nothing fancy. Just a simple application with a non-working button in the middle. The problem comes when I try to compile it using the default procedure :
[INDENT]qmake -project
qmake
make[/INDENT]

Compilation goes fine, but the link fails since it does not even try to link with either qt-mt (or qt for that mather) :

[INDENT]g++  -o qt test.o    -L/usr/X11R6/lib -lXext -lX11 -lm -lpthread[/INDENT]

Here is the generated .pro file : ```
TEMPLATE = app
CONFIG -= moc
INCLUDEPATH += .
# Input
SOURCES += test.cxx
```

I can fiddle with the Makefile to add the correct compilation flags (-lqt-mt) but that does not solve the problem, it just patches it and the problem reappears when I need the moc to run. I have noticed that the QTDIR and QMAKESPEC flags are not defined, but even if I do, the process does not work. 
[INDENT]QMAKESPEC=linux-g++
QTDIR=/usr/share/qt3[/INDENT]

I am therefore at a loss. I have seen this problem on another post here, but they solved it by moving to qt-4, which is not an option. I also do not want to use any IDEs or external tools. 

Help!

---

### Post by LordOfTheCows on 2007-03-03
Here is an update : On my mac workstation and on the ubuntu system, the generated .pro files are identical. So far so good. However, in the next stage, when I run 'qmake -d' (which gives me some debug output), I noticed that the ubuntu version does not parse the 'libqt-mt.prl' file which contains the information needed to link to the qt library. On the bright side, I found someone else with the same problem ... [http://ubuntuforums.org/showthread.php?p=1716185](http://ubuntuforums.org/showthread.php?p=1716185) :(

All we need to do now is find out why the .prl file is not parsed...

The saga continues!

---

### Post by LordOfTheCows on 2007-03-04
Oh I am loving this. I just found out by trial and error (and dumb luck) that the directory in which the project is located cannot be named 'qt' (!). 

For those at home who wish to try this out, here is a minimal source code file that shows the error :```
#include <qapplication.h>

int main( int argc, char **argv )
{
    QApplication a( argc, argv );

    return a.exec();
}

```

Put that file in a clean directory named 'qt'. Follow this procedure :
[INDENT]qmake -project
qmake
make[/INDENT]
Failure! :lolflag: 

On linux and mac, the same result happens (qt 3.3.6 and 3.3.7 respectively).
Cheers!

---

### Post by Hendrixski on 2007-03-12
Cool.. thanks for posting this.  It's good to know.  I'm actually just starting out with QT myself (after almost 7 years of programming mostly Java), and your post actually helped me get a grasp on the order compiling tools.  Also, now I know about the directory thing.  :) thanks

---

