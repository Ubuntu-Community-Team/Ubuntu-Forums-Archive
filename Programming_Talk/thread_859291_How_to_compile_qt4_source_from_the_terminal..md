---
title: "How to compile qt4 source from the terminal."
date: 2008-07-14
forum: Programming Talk
---

### Post by adredz on 2008-07-14
i just started stduying qt4/c++. now i made a very basic app using qdevelop and i noticed it has generated three files: 2 .cpp files and one .h file in the source folder. my question is, how do i compile them using command "g++ xxx.cpp -o xxx -Wall -0"? i have tried compiling a single .ccp file for one program but not those with multiple .cpp files. how will i do it?

thanks :)

---

### Post by LaRoza on 2008-07-14
> **adredz said:**
> i just started stduying qt4/c++. now i made a very basic app using qdevelop and i noticed it has generated three files: 2 .cpp files and one .h file in the source folder. my question is, how do i compile them using command "g++ xxx.cpp -o xxx -Wall -0"? i have tried compiling a single .ccp file for one program but not those with multiple .cpp files. how will i do it?

thanks :)

You just do ```
g++ source.cpp source2.cpp
```

But you'll have to link them to the qt libs.

---

### Post by scourge on 2008-07-14
> **LaRoza said:**
> You just do ```
g++ source.cpp source2.cpp
```

But you'll have to link them to the qt libs.

Just linking to the Qt libs isn't usually enough because the code first has to be converted to standard C++ by the Meta-Object Compiler. The painless way to compile Qt apps is to create a project file, run qmake (which creates the necessary C++ code and a platform-specific makefile), and then run make.

---

### Post by StOoZ on 2008-07-14
what includes (Qt related ones) did you use in your project?

---

### Post by bfhicks on 2008-07-14
Typically, you'd go into the directory where the files are and...

```

qmake-qt4 -project   #creates the project for you automatically
qmake                #generates the Makefile
make                 #compiles the code

```

---

### Post by alxlabs on 2008-07-14
I'm having a problem doing so..

Here si an example from trolltech
```

#include <QApplication>
#include <QPushButton>

int main (int argc, char *argv[])
{
        QApplication app(argc, argv);

        QPushButton hello ("Hello world!");
        hello.resize (100, 30);

        hello.show();
        return app.exec();
}

```

then i did:

qmake-qt4 -project   
qmake                
make                 

Which ended up with whole bunch of errors..., 
```

alxlabs@alxlabs-laptop:~/hello_qt$ make
gcc -c -pipe -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I. -o hello.o hello.c
In file included from /usr/include/qt4/QtCore/qobjectdefs.h:47,
                 from /usr/include/qt4/QtCore/qobject.h:49,
                 from /usr/include/qt4/QtCore/qcoreapplication.h:47,
                 from /usr/include/qt4/QtGui/qapplication.h:47,
                 from /usr/include/qt4/QtGui/QApplication:1,
                 from hello.c:1:
/usr/include/qt4/QtCore/qnamespace.h:51: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;QT_MODULE&#8217;
/usr/include/qt4/QtCore/qnamespace.h:1429: error: expected &#8216;)&#8217; before &#8216;:&#8217; token
/usr/include/qt4/QtCore/qnamespace.h:1445: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;Q_CORE_EXPORT&#8217;
In file included from /usr/include/qt4/QtCore/qobject.h:49,
                 from /usr/include/qt4/QtCore/qcoreapplication.h:47,
                 from /usr/include/qt4/QtGui/qapplication.h:47,
                 from /usr/include/qt4/QtGui/QApplication:1,
                 from hello.c:1:
/usr/include/qt4/QtCore/qobjectdefs.h:49: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;QT_BEGIN_HEADER&#8217;
/usr/include/qt4/QtCore/qobjectdefs.h:55: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;QByteArray&#8217;
/usr/include/qt4/QtCore/qobjectdefs.h:138: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;<&#8217; token
/usr/include/qt4/QtCore/qobjectdefs.h:141: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;<&#8217; token
/usr/include/qt4/QtCore/qobjectdefs.h:214: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;QObject&#8217;
/usr/include/qt4/QtCore/qobjectdefs.h:215: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;QMetaMethod&#8217;

..................

```

---

### Post by scourge on 2008-07-14
> **alxlabs said:**
> 
...then i did:

qmake-qt4 -project   
qmake                
make                 

Which ended up with whole bunch of errors..., 


I'm guessing that's because you named your source file hello.c, even though it's C++ code. Try renaming it hello.cpp and see what happens.

---

### Post by alxlabs on 2008-07-14
Thanks Scourge, it worked...

---

### Post by adredz on 2008-07-14
wow that works! thanks to all! :)
anyone know the equivalent commands for windows? the story is, i am making a little project in my *buntu box but i should be able to run it on windows as well cos in our school, all computers are "infected with M$". could you help me please..

---

### Post by scourge on 2008-07-15
> **adredz said:**
> wow that works! thanks to all! :)
anyone know the equivalent commands for windows? the story is, i am making a little project in my *buntu box but i should be able to run it on windows as well cos in our school, all computers are "infected with M$". could you help me please..

The qmake commands are the same, and the project file is platform-independent, so you can use it also in Windows. The "make" part depends on the compiler/environment you're using. If you have the MinGW install of Qt, it's "mingw32-make", if you're using Visual Studio it's "nmake".

---

### Post by adredz on 2008-07-15
> **scourge said:**
> The qmake commands are the same, and the project file is platform-independent, so you can use it also in Windows. The "make" part depends on the compiler/environment you're using. If you have the MinGW install of Qt, it's "mingw32-make", if you're using Visual Studio it's "nmake".

thanks so much scourge, that helps a lot :)

----------------
Now playing: [Seether - The Gift](http://www.foxytunes.com/artist/seether/track/the+gift)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by Bhanu Pratap Singh on 2012-08-04
Installed qt4... made a simple cpp program
#include <QApplication>
#include <QWidget>
  
int main(int argc, const char *argv[]) {
    QApplication app(argc, argv);
  
    QWidget window;
  
    window.resize(250, 150);
    window,setWindowTitle("Simple example");
    window.show();
  
    return app.exec();
}
When I do..
qmake-qt4 -project    

it says

Failure to open file: /home/bhanu/qt4//qt4.pro
Unable to generate project file.

Please Help!!

---

### Post by Bhanu Pratap Singh on 2012-08-04
> **Bhanu Pratap Singh said:**
> Installed qt4... made a simple cpp program
#include <QApplication>
#include <QWidget>
  
int main(int argc, const char *argv[]) {
    QApplication app(argc, argv);
  
    QWidget window;
  
    window.resize(250, 150);
    window,setWindowTitle("Simple example");
    window.show();
  
    return app.exec();
}
When I do..
qmake-qt4 -project    

it says

Failure to open file: /home/bhanu/qt4//qt4.pro
Unable to generate project file.

Please Help!!

for some reason there are two "//" in front of the qt4.pro file name. I 
suspect this is the problem but I don't have a clue how to fix it.

---

### Post by keghn on 2013-05-15
I got this to work with:
 With the file manager create a folder to hold the source file.cpp. Such as
in the folder:


/keghn/qt/folder6


 Open up a terminal in a folder where the file.cpp is at.
 In the empty file.cpp place code and save it.
 Type these three lines into the terminal:


qmake-qt4 -project 
qmake 
make 


 This made an executable code name after the folder that it is in.
 To run the program type into a terminal:


./folder6


 This made a small window with "hello world" printed in it with the example in the thread.

---

