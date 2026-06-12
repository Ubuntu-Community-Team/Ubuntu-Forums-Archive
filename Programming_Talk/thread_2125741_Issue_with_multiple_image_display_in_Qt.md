---
title: "Issue with multiple image display in Qt"
date: 2013-03-14
forum: Programming Talk
---

### Post by Ubuntee1 on 2013-03-14
[TABLE]
[TR]
[TD="class: codeLineNumbers container-3"][/TD]
[TD="class: codeLines container-4"]I have written the following code to display the images on widget in grid fashion.I want my widget size to be fixed 
and when the images are displayed i am setting the button size to the images size.There are three images to be displayed but the code is displaying only two.
and when ever i maximize the main window the images on push button are getting into different shape.

any help in right direction is appreciated.

I want my images should resize according the mainwindow
by default it should display four images , if any extra should be controlled by scroll bar.


```


#include <QtGui/QApplication>
#include "mainwindow.h"
#include<QtGui>
#include <QGridLayout>

int main(int argc, char *argv[])
{
    QApplication a(argc, argv);
// MainWindow w;
    QWidget *w = new QWidget();
//  QLabel label;
//QPixmap pm("/home/skylab/GUI/Images/fight.jpeg");
//QGridLayout* Gh = new QGridLayout();
    QGridLayout *layout = new QGridLayout;

    w->setLayout(layout);
    //label.setPixmap(pm);


    w->resize(500,500);
    //w.show();

    //label.setFixedSize(pm.size());

    //dailog->setLayout(Gh);

    QPushButton* button1 = new QPushButton;

    QPixmap pm1("/home/skylab/GUI/Images/fight.jpeg");
    QIcon ButtonIcon1(pm1);
    button1->setIcon(ButtonIcon1);
    button1->setIconSize(pm1.rect().size());

    QPushButton* button2 = new QPushButton;

    QPixmap pm2("/home/skylab/GUI/Images/Gun.jpeg");
    QIcon ButtonIcon2(pm2);
    button2->setIcon(ButtonIcon2);
    button2->setIconSize(pm2.rect().size());

    QPushButton* button3 = new QPushButton;
    QPixmap pm3("/home/skylab/GUI/Images/lilly.jpeg");
    QIcon ButtonIcon3(pm3);
    button3->setIcon(ButtonIcon3);
    button3->setIconSize(pm3.rect().size());

    /*
    button1->setIcon(QIcon("/home/skylab/GUI/Images/fight.jpeg"));
    layout->addWidget(button1,0,0);
    button1->setGeometry(23,45,23,56);
    button1->setFixedSize(160,150);
    QPushButton* button2 = new QPushButton(QIcon("/home/skylab/GUI/Images/Gun.jpeg"),"");
    button2->setFixedSize(160,150);
    QPushButton* button3 = new QPushButton(QIcon("/home/skylab/GUI/Images/lilly.jpeg"),"");
    button3->setFixedSize(160,150);
    */
    layout->addWidget(button2,0,1);
    layout->addWidget(button3,0,2);
    //image1->setGeometry(23,45,23,56);
    w->show();
    //label.show();
    return a.exec();
}



```

[/TD]
[/TR]
[/TABLE]

---

