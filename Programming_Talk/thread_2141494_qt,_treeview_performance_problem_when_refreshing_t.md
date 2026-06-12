---
title: "qt, treeview performance problem when refreshing the model."
date: 2013-05-02
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2013-05-02
Hi, I was debugging an open source project that had this issue: When the rows in the treeview grow above 200/300 the gui freezes for almost a second when updating and also raises the CPU usage quite a lot. This is how the logic is implemented. The treeview uses a custom treemodel which is derived from qabstractitemmodel. It also uses a custom delegate which is based on qitemdelegate. The custom model has a timer which when it expires it updates the data in the model.(it retrieves any new updates to the rows/columns). As an optimization the datachanged event is emitted once and includes the whole model. If it is emitted once per row(or per setdata()) the program practically locks up. I initially thought that the freeze of the gui was due to slow retrieval of the new values. But this is not the case. The freeze is caused by the redrawing/repainting of the widget. So to better illustrate my problem I provide an example program. It exhibits exactly the same freeze, although it doesn't derive directly from qabstractmodel. In this example program I just output random numbers so to be sure that the retrieval of the values isn't the bottleneck. The timeout is set to 750ms to get the freeze quicker.

Just click on the scrollbar and drag it up and down eventually you will notice the freeze. Note: on the actual project the freeze also affects the while application(menus,dialogs etc).
Do you have any ideas on how to solve this? Maybe custom treeview? Some other trick?

main.cpp
[php]#include <QApplication>
#include "mainwindow.h"

#include <cstdlib>
#include <ctime>
int main(int argc, char *argv[])
{
  srand(time(NULL));
  QApplication a(argc, argv);
  MainWindow w;
  w.show();
  
  return a.exec();
}
[/php]

mainwindow.h
[php]#ifndef MAINWINDOW_H
#define MAINWINDOW_H

#include <QMainWindow>
#include <QStandardItemModel>
#include <QTimer>
#include <QTreeView>


class TModel : public QStandardItemModel
{
  Q_OBJECT

public:
  TModel( int rows, int columns, QObject * parent = 0 );
  bool setData(const QModelIndex &index, const QVariant &value, int role = Qt::DisplayRole);
  void setTimer(const int &msec);

private:
  bool expired_timer;
  QTimer timer;

private slots:
  void forceUpdate();
};

namespace Ui {
class MainWindow;
}

class MainWindow : public QMainWindow
{
  Q_OBJECT
  
public:
  explicit MainWindow(QWidget *parent = 0);
  ~MainWindow();
  
private:
  Ui::MainWindow *ui;  
  TModel *model;
  QTreeView *view;
};

#endif // MAINWINDOW_H
[/php]

mainwindow.cpp
[php]#include "mainwindow.h"
#include "ui_mainwindow.h"

#include <cstdlib>

MainWindow::MainWindow(QWidget *parent) :
  QMainWindow(parent),
  ui(new Ui::MainWindow)
{
  ui->setupUi(this);
  view = new QTreeView();  
  model = new TModel(0, 22, view);
  view->setModel(model);  
  setCentralWidget(view);

  for (unsigned int i = 0; i < 300; i++)
  {
    model->insertRow(model->rowCount());
    model->setData(model->index(i,0), i+1);
    for (unsigned int c = 1; c < model->columnCount(); c++)
    {
      model->setData(model->index(i,c), rand());
    }
  }
  model->setTimer(750);
}

MainWindow::~MainWindow()
{
  delete ui;
  delete view;
  delete model;
}

TModel::TModel( int rows, int columns, QObject * parent): QStandardItemModel(rows, columns, parent), expired_timer(false)
{
  connect(&timer, SIGNAL(timeout()), SLOT(forceUpdate()));
}

void TModel::setTimer(const int &msec)
{
  timer.stop();
  timer.start(msec);
}

bool TModel::setData(const QModelIndex &index, const QVariant &value, int role)
{
  if (expired_timer) blockSignals(true);
  bool ret = QStandardItemModel::setData(index, value, role);
  if (expired_timer) blockSignals(false);
  return ret;
}

void TModel::forceUpdate()
{
  expired_timer = true;
  for (unsigned int i = 0; i < rowCount(); i++)
  {
    for (unsigned int c = 1; c < columnCount(); c++)
    {
      setData(index(i,c), rand());
    }    
  }

  emit dataChanged(index(0,0), index(rowCount()-1 ,columnCount()-1));
  expired_timer = false;
}
[/php]

mainwindow.ui
[php]<?xml version="1.0" encoding="UTF-8"?>
<ui version="4.0">
 <class>MainWindow</class>
 <widget class="QMainWindow" name="MainWindow">
  <property name="geometry">
   <rect>
    <x>0</x>
    <y>0</y>
    <width>400</width>
    <height>300</height>
   </rect>
  </property>
  <property name="windowTitle">
   <string>MainWindow</string>
  </property>
  <widget class="QWidget" name="centralWidget"/>
 </widget>
 <layoutdefault spacing="6" margin="11"/>
 <resources/>
 <connections/>
</ui>
[/php]

untitled.pro
[php]#-------------------------------------------------
#
# Project created by QtCreator 2013-04-28T15:53:26
#
#-------------------------------------------------

QT       += core gui

greaterThan(QT_MAJOR_VERSION, 4): QT += widgets

TARGET = untitled
TEMPLATE = app


SOURCES += main.cpp\
        mainwindow.cpp

HEADERS  += mainwindow.h

FORMS    += mainwindow.ui
[/php]

Attaching files for convinience too.

---

