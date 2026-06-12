---
title: "QT - Strange layout problem with QStackedWidget"
date: 2009-09-19
forum: Programming Talk
---

### Post by Ultra Magnus on 2009-09-19
Hi. I'm having a strange problem using QStackedWidget. 

I'm trying to create a window with a QGLWidget and QStackedWidget next to one-another. The stacked widget should be of fixed size and the glwidget should expand to fill all the remaining available space. 

What actually happens is that the glwidget takes up the minimum width, the stacked widget remains fixed in size and the rest of the space is empty. I get different results depending on whether I ask the stacked widget to be fixed size or its contents but I can't get it to act the way I'd like.

I've posted a simplified bit of code, the glwidget hasn't been inherited so it will look strange if you run it but it illustrates the problem i'm having/. If anyone can illuminate me as to what I'm doing wrong it would be a great help.

Thanks,

James

```

#include <QHBoxLayout>
#include <QGLWidget>
#include <QPushButton>
#include <QStackedWidget>
#include <QMainWindow>
#include <QApplication>
#include <QString>

int main(int argc, char *argv[])
{
    QApplication a(argc, argv);

    // create main window
    QMainWindow *mainwindow = new QMainWindow() ;

    // create main widget
    QWidget *mainwidget = new QWidget() ;

    // create gl widget
    QGLWidget *glwidget = new QGLWidget() ;
    glwidget->setMinimumWidth(200) ;

    // create button
    QPushButton *button = new QPushButton("Button") ;
    button->setFixedWidth(200) ;

    // create stacked widget and add button
    QStackedWidget *stack = new QStackedWidget() ;
    stack->addWidget(button) ;

    // create layout
    QHBoxLayout *mainlayout = new QHBoxLayout() ;
    mainlayout->setMargin(5) ;
    mainlayout->addWidget(glwidget) ;
    mainlayout->addWidget(stack) ;
    mainwidget->setLayout(mainlayout) ;
    mainwindow->setCentralWidget(mainwidget) ;
    mainwindow->show();
    return a.exec();
}

```

---

### Post by Ultra Magnus on 2009-09-20
The same sort of thing seems to happen if I replace the QGLWidget with say a QPushButton so I suspect I'm doing something fairly obviously wrong. So any ideas would be useful.

Thanks again. James

---

### Post by Colonel Kilkenny on 2009-09-20
Well, this would be easy if you'd use Qt Creator / Qt Designer to build GUI.

Anyway, I think you need to tell the glwidget to expand (with setSizePolicy()). This is just a guess but I think it should be something like this (the first parameter is horizontal and second vertical):
glwidget->setSizePolicy(QSizePolicy::Expanding, QSizePolicy::Expanding)

edit. setSizePolicy() is inherited from QWidget

---

### Post by Ultra Magnus on 2009-09-21
Thanks, that worked, I knew it must be something simple.

---

