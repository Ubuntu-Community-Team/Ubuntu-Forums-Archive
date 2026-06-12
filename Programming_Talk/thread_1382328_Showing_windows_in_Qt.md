---
title: "Showing windows in Qt"
date: 2010-01-15
forum: Programming Talk
---

### Post by Saxcore on 2010-01-15
Hi there!

I'm currently having a go with Qt. I'm just about getting my head around the basics, however am stuck on a pretty simple concept; I'm using Qt Designer to help design a Dialog (actually, would a Dialog be the right choice for an application that runs in one "window"?), and can get my code from the .xml-style output from Designer (the .ui format), to creating a C++ header file. My main program is creating an instance of the Dialog in memory (as far as I know..), but I'm failing to find the single method to call that will "show" the window (..if there IS such a method..).

Sorry about the potentially extremely simple question, but for some reason I'm really struggling to find an answer!

Cheers, Sam.

---

### Post by caelestis2 on 2010-01-15
I don't really know what your talking about, but to show a basic window, you must first start with a widget. If you a define a widget with no parent, (for example, you might put a circle in a box, and the box will be the parent) then the widget becomes a window.

[PHP]#include <QApplication>
#include <QWidget>
#include <QLabel>

int main(int argc, char** argv) {
  QApplication app(argc, argv);
  QWidget window;
  window.resize(400,400);
  window.setWindowTitle("Hello World");
  
  QLabel * hi = new QLabel("Hello World!", &window); //Child of window
  hi->show();

  window.show();
  return app.exec();
}[/PHP]

then to compile this c++ file, first change into your files directory and open a terminal and type:

```
qmake -project
qmake .
make
```

Please install an IDE with code completion support. If you have an IDE, simply typing window and then dot will bring up all the methods of the window object, and you could've easily found show()

If you are having any more difficulty, I learned from this tutorial: [http://zetcode.com/tutorials/qt4tutorial/](http://zetcode.com/tutorials/qt4tutorial/)

---

### Post by Saxcore on 2010-01-16
Hi, thanks for your help!

The thing is, I'd already found the show() method, but it doesn't seem to be a part of the class that is created by the UIC from the .ui file. I realise that it's a bad idea to be editing this output header file, but the Dialog class within this file (as far as I can see) doesn't seem to be inheriting from anything, and as a result doesn't have the show() method.

I'm clearly misunderstanding something here, I'll have a look at your link now and see if that sheds any light.

Cheers!



EDIT: Right, it looks like I've got it working. I think I was just struggling to understand how to use the generated class. Would it right to say that the generated class is more of a means to set up a separate window? ...what I wasn't realising is that a separate window would need to be created, so that the generated class's setupUI() method could be called... It's begining to make sense. Thanks a lot for your help!

Sam

---

### Post by Colonel Kilkenny on 2010-01-16
You need to introduce the ui file in your project file (*.pro), put a private member (Ui::MyDialog ui) to your MyDialog.h file and in MyDialog.cpp constructor call ui.setupUi(this).
Or something like that. Go to qt.nokia.com and documentation and search for qt designer examples.

However, I'd really really suggest that you would download Qt Creator (IDE which has Qt Designer builtin) which makes things a lot more easier. You don't need to manually do anything with project file etc. etc.

---

