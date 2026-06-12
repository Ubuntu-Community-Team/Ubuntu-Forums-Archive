---
title: "Qt Menubar issues"
date: 2009-12-13
forum: Programming Talk
---

### Post by Woody1987 on 2009-12-13
Im trying to add a menubar to my Qt application. This application will also use opengl to render stuff in the app. Right now, the only way i can add a menubar is to add it to a layout box. This causes a problem as the menubar is not at the top of the screen. Picture below shows the problem.
[IMG]http://img190.imageshack.us/img190/9686/screenshot1ee.png[/IMG]

If i do some tinkering i can get the menubar where i want it, but it removes the opengl part.
[IMG]http://img692.imageshack.us/img692/238/screenshot2v.png[/IMG]

Code:
window.h
```
#ifndef WINDOW_H
#define WINDOW_H

#include <QWidget>
#include <QtGui>
#include <QMainWindow>

class GLWidget;

class Window : public QWidget
{
    Q_OBJECT

public:
    Window();

private:
    GLWidget *glWidget;

    QMenuBar *menubar;
    QMenu *menuFile;
    QMenu *menuPreferences;
    QMenu *menuSimulation;
    QMenu *menuHelp;
    QToolBar *toolBar;
    QAction *actionRun;
    QAction *actionPause;
    QAction *actionStop;
    QAction *actionSetup;
};

#endif
```

window.cpp
```
#include <QtGui>

#include "glwidget.h"
#include "window.h"
#include <QMainWindow>

Window::Window()
{
    glWidget = new GLWidget;

    menubar = new QMenuBar();
    menuFile = new QMenu("&File");
    menuPreferences = new QMenu("&Preferences");
    menuSimulation = new QMenu("&Simulation");
    menuHelp = new QMenu("&Help");
    menubar->addMenu(menuFile);
    menubar->addMenu(menuPreferences);
    menubar->addMenu(menuSimulation);
    menubar->addMenu(menuHelp);

    QVBoxLayout *mainLayout = new QVBoxLayout;
    //setMenuBar(menubar);
    mainLayout->addWidget(menubar);
    mainLayout->addWidget(glWidget);    
    setLayout(mainLayout);

    setWindowTitle(tr("Particle Simulator"));
}
```

The problem seems to be with window.h, specifically with:
```
class Window : public QWidget
```
Changing QWidget to QMainWindow fixes the menubar issue but removes the opengl. How do i get both?

---

### Post by Woody1987 on 2009-12-14
Yaya i did it!

---

### Post by cneha on 2010-06-04
your post made me able to create a menubar.thanks for that.
I am having a similar kinda problem. i added a menubar but it is not showing it at appropriate place.
it is taking complete space vertically..
can you suggest any solution??
thanks.

---

### Post by cneha on 2010-06-04
i solved the issue.We can use the following in main layout
mainLayout->setMenuBar(menubar);

this will create a menu bar over your windows widgets..
thanks..

---

