---
title: "Qt complains about missing header files"
date: 2005-07-09
forum: Programming Talk
---

### Post by André on 2005-07-09
Hi everybody,

i am just starting qt programming and tried to compile their helloworld example.

The code is the following:

--> snip
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
--> snip

I did qmake -project && qmake. Then i tried g++-3.3 00-helloworld.cpp and i get:

00-helloworld.cpp:1:26: qapplication.h: Datei oder Verzeichnis nicht gefunden
00-helloworld.cpp:2:25: qpushbutton.h: Datei oder Verzeichnis nicht gefunden
00-helloworld.cpp: In function `int main(int, char**)':
00-helloworld.cpp:7: error: `QApplication' undeclared (first use this function)
00-helloworld.cpp:7: error: (Each undeclared identifier is reported only once
   for each function it appears in.)
00-helloworld.cpp:7: error: Fehler beim Parsen before `(' token
00-helloworld.cpp:9: error: `QPushButton' undeclared (first use this function)
00-helloworld.cpp:10: error: `hello' undeclared (first use this function)
00-helloworld.cpp:12: error: `a' undeclared (first use this function)

It's german but as you might see g++ is complaining about missing qapplication.h and qpushbutton.h.

locate qapplication.h gives me /usr/include/qt3/qapplication.h. This is the correct path that is set in the Makefile: INCPATH  = -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3.

So what's wrong here? Do i have to set another path somewhere? What am i missing?

Any help is greatly appreciated.
Greetings
André

---

### Post by tread on 2005-07-09
Did you try just doing make?
1. "qmake -project"  creates a .pro file
2. "qmake" creates a Makefile with all the correct paths

Therefore, at this point if you type in 
"make"
your code should compile. If it does, take a look at the Makefile to see what you were missing from the commandline later.

---

### Post by André on 2005-07-09
Okay, beside but feeling pretty stupid right now, everything works fine... :-)

I think i still have to learn very(!) much but this is a pretty good start... Hello World ;-)

Greetings
André

---

### Post by tread on 2005-07-09
Hehe .. have fun now :)

---

