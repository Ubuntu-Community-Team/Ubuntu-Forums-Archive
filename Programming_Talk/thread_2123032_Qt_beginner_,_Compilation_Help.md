---
title: "Qt beginner , Compilation Help"
date: 2013-03-06
forum: Programming Talk
---

### Post by Ubuntee1 on 2013-03-06
Hi  ,

I wrote below by following a random site.

 w.cpp
```

#include <QApplication>
#include <QWidget>

int main(int argc , char **argv)
{       QApplication app(argc , argv);
        QWidget window;
        window.resize(250,150);
        window.setWindowTitle("Simple Example");
        window.show();

        return app.exec();
}

```

I have installed **qt3-dev-tools **and **qt4-make** on suggestion, using synaptic pakage manager , and i have not set any configuration paths for libraries or include files. 
And  i have done following 

> skl@skl:~/GUI/window$ ls
note  w.cpp
skl@skl:~/GUI/window$ qmake -project
skl@skl:~/GUI/window$ ls
note  w.cpp  window.pro
skl@skl:~/GUI/window$ qmake window.pro 
skl@skl:~/GUI/window$ ls
Makefile  note  w.cpp  window.pro
skl@skl:~/GUI/window$ make
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o w.o w.cpp
w.cpp:2:24: fatal error: QApplication: No such file or directory
compilation terminated.
make: *** [w.o] Error 1
skl@skl:~/GUI/window$ 

Well , i checked for this, "-I/usr/share/qt4/mkspecs/linux-g++",  and is present in the same location but , the others(-I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4) are not present in the same location as mentioned in the command.

I would like to know qt3-dev-tools and qt4-make are compatible to each other or am i missing something for compilation. If i am wrong in any order request you to let me know some references on latest qt tools for compilation.

---

### Post by spjackson on 2013-03-07
You don't want qt3-dev-tools unless you have to maintain some very old code. Qt 4 was released about 10 years ago. Qt 5 is here or hereabouts.

I think you want to remove qt3-dev-tools and install libqt4-dev and qt4-dev-tools.

---

### Post by Ubuntee1 on 2013-03-07
Thanks for the reply spjackson.

I need this for some kind of user interface where i have a provisions for open , close , run etc.
The backend of this is gstreamer/QT for media handing like play , pause etc, and it is not simple media player.
please let me know are there any open source reference codes available .

---

### Post by Ubuntee1 on 2013-03-08
Request some one to provide some references

---

### Post by r-senior on 2013-03-08
Could you be more specific?

An introductory tutorial?

[http://zetcode.com/gui/qt4/](http://zetcode.com/gui/qt4/)

---

### Post by Ubuntee1 on 2013-03-08
> **r-senior said:**
> Could you be more specific?

An introductory tutorial?

[http://zetcode.com/gui/qt4/](http://zetcode.com/gui/qt4/)


I have gone through it already, it is having very basic tutorial.
I need to create few windows , one main window and few sub windows inside the main window.
One of the  sub windows is for displaying the video/image content , and should be controlled from other control sub window.
Attached is just a sample UI where i have two windows outer ( main window ) and inner ( sub window) , similarly i have 2 , 3 sub windows for controls.
Ths entire set up is oing to be in a normal window with close , min , max buttons.

I am just looking for some sample code how to create windows in windows and display content(video/graphics/images) in a particular window and controlled by other windows.

---

