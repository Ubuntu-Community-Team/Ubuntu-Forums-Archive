---
title: "Need help with QT libraries"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Jimnast on 2008-10-15
Ok I have to compile some QT programs for university but I can't compile because ubuntu or I don't know what can't find the #include (included files)

Example of one program:
#include <qapplication.h>

#include <QAbstractGraphicsShapeItem>

#include <QGraphicsScene>

#include <QWidget>

#include <QGraphicsView>

#include <QGraphicsRectItem>

#include <QGraphicsEllipseItem>



int main(int argc, char **argv)

{

    QApplication a(argc, argv);

    //On creer une scene

    QGraphicsScene *c1=new QGraphicsScene(0,0,300,300);

    //on creer une vue pour voir la scene

    QGraphicsView *vue=new QGraphicsView(c1);

    //On change la couleur de fond de la scene en jaune

    c1->setBackgroundBrush (QBrush(Qt::yellow));

    //On declare un rectangle posX=10;posY=20;Witdh=20;Height=50

    QGraphicsRectItem *rec = new QGraphicsRectItem(0,0,20,50);

    //On declare un Qpen et un QBrush (pas necessaire mais jai u des souci avec rec->setPen(Qt::blue) pas reconnu

    QPen p(Qt::green);

    QBrush b(Qt::blue);

    //On affecte le Qpen et le QBrush

    rec->setPen(p);

    rec->setBrush(b);

    //On ajoute sa a la scene

    c1->addItem(rec);

    

    //on declare un rond   

    

    

    //on fait deux boucle pour avoir 4 rangé de 5 rond

    //on declare 2 variable pour la position

    int x=4;//on commence a 4 pour pas touche le carre 

    int y=0;

    

    for (int i=0;i<4;i++)

    {

      x+=20;  y=0;

        for (int j=0;j<5;j++)

        {

            QGraphicsEllipseItem *el =new QGraphicsEllipseItem (x,y,20,20);

            el->setPen(p);

            el->setBrush(b);

            c1->addItem(el);

            y+= 20;

            }

            }

    

    

    vue->show();

    

    

    return a.exec();

}




And when I try to compile I get these errors:


g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o tp3q1.o tp3q1.cc
tp3q1.cc:2:38: error: QAbstractGraphicsShapeItem: No such file or directory
tp3q1.cc:3:26: error: QGraphicsScene: No such file or directory
tp3q1.cc:4:19: error: QWidget: No such file or directory
tp3q1.cc:5:25: error: QGraphicsView: No such file or directory
tp3q1.cc:6:29: error: QGraphicsRectItem: No such file or directory
tp3q1.cc:7:32: error: QGraphicsEllipseItem: No such file or directory
tp3q1.cc: In function ‘int main(int, char**)’:
tp3q1.cc:13: error: ‘QGraphicsScene’ was not declared in this scope
tp3q1.cc:13: error: ‘c1’ was not declared in this scope
tp3q1.cc:13: error: expected type-specifier before ‘QGraphicsScene’
tp3q1.cc:13: error: expected `;' before ‘QGraphicsScene’
tp3q1.cc:15: error: ‘QGraphicsView’ was not declared in this scope
tp3q1.cc:15: error: ‘vue’ was not declared in this scope
tp3q1.cc:15: error: expected type-specifier before ‘QGraphicsView’
tp3q1.cc:15: error: expected `;' before ‘QGraphicsView’
tp3q1.cc:19: error: ‘QGraphicsRectItem’ was not declared in this scope
tp3q1.cc:19: error: ‘rec’ was not declared in this scope
tp3q1.cc:19: error: expected type-specifier before ‘QGraphicsRectItem’
tp3q1.cc:19: error: expected `;' before ‘QGraphicsRectItem’
tp3q1.cc:21: error: variable ‘QPen p’ has initializer but incomplete type
tp3q1.cc:42: error: ‘QGraphicsEllipseItem’ was not declared in this scope
tp3q1.cc:42: error: ‘el’ was not declared in this scope
tp3q1.cc:42: error: expected type-specifier before ‘QGraphicsEllipseItem’
tp3q1.cc:42: error: expected `;' before ‘QGraphicsEllipseItem’
make: *** [tp3q1.o] Error 1



I assume it's because these qt libraries aren't installed or perhaps they are installed but the make file is looking in the wrong place. However the make file is created by qmake so I don't know what to do. I've installed every qt package I can find that seems coherent. Still no help. 

Any ideas?

---

### Post by SunnyRabbiera on 2008-10-15
Ubuntu doesnt use qt by default, you may need to install the qt development packages with synaptic located under system> administration> synaptic package manager.
Now what exactly you will need to do this I am uncertain but you can do some brushing up hopefully with some forum searches.

---

### Post by Jimnast on 2008-10-15
Not exactly sure what you mean, but I've installed through synaptic, qt4, qt3, qt4-dev, and many other devs, which are normally development files are they not? Unless you've got specific ones in mind?

---

### Post by SunnyRabbiera on 2008-10-15
> **Jimnast said:**
> Not exactly sure what you mean, but I've installed through synaptic, qt4, qt3, qt4-dev, and many other devs, which are normally development files are they not? Unless you've got specific ones in mind?

yeh ones with -dev are for development.
Now do you know what version of QT you need for your stuff?
Did your university specify?

---

### Post by Jimnast on 2008-10-15
My brother fixed it, he said I had qt3 and qt4 installed, he removed both and then re-installed qt4, now it works. Sorry to bother you. Man I hate computing.

---

