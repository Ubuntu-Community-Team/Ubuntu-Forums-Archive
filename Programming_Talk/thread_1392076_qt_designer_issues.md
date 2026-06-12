---
title: "qt designer issues"
date: 2010-01-27
forum: Programming Talk
---

### Post by hollowhead on 2010-01-27
I've started learning to use qt designer 4.5 and I've got a couple of what seem like basic questions. I've read and re-read all the tutorials I can find and looked at the QT examples.  I installed Qdevelop, followed the instructions in one of the tutorials.   I've created the start of my app GUI and set up some menus and buttons and created the requisite source and header file.

What I wish to do first is simply add the code for quitting the program so that when you click on file exit, it exits, just to get me started.  I cannot quite get my head around what to call how for slots and signals.

mainwindowimpl.h

#ifndef MAINWINDOWIMPL_H
#define MAINWINDOWIMPL_H
//
#include <QMainWindow>
#include "ui_mainwindow.h"
//
class MainWindowImpl : public QMainWindow, public Ui::MainWindow
{
Q_OBJECT
public:
	MainWindowImpl( QWidget * parent = 0, Qt::WFlags f = 0 );
private slots:
};
#endif


// mainwindowimpl.cpp

#include "mainwindowimpl.h"
//
MainWindowImpl::MainWindowImpl( QWidget * parent, Qt::WFlags f) 
	: QMainWindow(parent, f)
{
	setupUi(this);
}
//


In the object inspector the object is action_Quit_2 and the class QAction.

The second question relates to how I create multiple top level windows like the gimp.  I want my results to appear on the a richedit in a separate window that loads blank with the program. The richedit is in the examples stuff but I cannot see how to design this second window seperate from the main one in qt designer.

Any help on these points would be appreciated.

---

