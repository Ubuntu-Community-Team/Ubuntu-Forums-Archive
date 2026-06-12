---
title: "OpenGL library files missing"
date: 2009-03-14
forum: Programming Talk
---

### Post by Firestom on 2009-03-14
Welcome!

I have been trying to use OpenGL with Qt to try the QtOpenGL module and start 3D programming with it. However, each time I tried to compile, a linker error appeared saying: ```
collect2: ld returned 1 exit status
```. I quickly realised that was due to missing library files. I tried to install packages that were supposed to contain the library files. However, I have them all installed already.

Where can I get the library files and where do I put them? I can't seem to remember, I don't know why. I used to know, I went on today but still.

Thanks for replying!

---

### Post by slavik on 2009-03-14
1. try running sudo ldconfig
2. telling us that ld returned 1 is as useless as telling us "it's broken" ... we will need to know WHY ld returned 1 which is usually found within about 10 lines prior to that message.

---

### Post by abhilashm86 on 2009-03-14
this add neceesary files for glut and execute opengl,it just adds missing files

```

sudo apt-get install freeglut3-dev libglut3-dev

```

usually files are saved in this path, to compile

> -lm -lGL -L/usr/X11R6/lib -lGLU -lglut


---

### Post by Firestom on 2009-03-15
Here is what make returns:

```
make -f Makefile.Debug
make[1]: Entering directory `/home/firestom/OpenGL'
g++ -Wl,-rpath,/home/firestom/qtsdk-2009.01/qt/lib -o OpenGL debug/main.o debug/abstractglwidget.o debug/baseglwidget.o debug/moc_abstractglwidget.o    -L/home/firestom/qtsdk-2009.01/qt/lib -L/usr/X11R6/lib -lQtOpenGL -L/home/firestom/qtsdk-2009.01/qt/lib -L/usr/X11R6/lib -pthread -pthread -pthread -pthread -pthread -pthread -pthread -pthread -lQtGui -pthread -lfreetype -lgobject-2.0 -lSM -lICE -pthread -pthread -lXrender -lfontconfig -lXext -lX11 -lQtCore -lm -pthread -lgthread-2.0 -lrt -lglib-2.0 -ldl -lGLU -lGL -lpthread
debug/moc_abstractglwidget.o:(.rodata._ZTV16AbstractGLWidget[vtable for AbstractGLWidget]+0x64): undefined reference to `AbstractGLWidget::keyPressEvent(QKeyEvent*)'
debug/moc_abstractglwidget.o:(.rodata._ZTV16AbstractGLWidget[vtable for AbstractGLWidget]+0x108): undefined reference to `AbstractGLWidget::timeOut()'
debug/moc_abstractglwidget.o:(.rodata._ZTV16AbstractGLWidget[vtable for AbstractGLWidget]+0x10c): undefined reference to `AbstractGLWidget::timeOutSlot()'
collect2: ld returned 1 exit status
make[1]: *** [OpenGL] Error 1
make[1]: Leaving directory `/home/firestom/OpenGL'
make: *** [debug] Error 2
```

These lines are the error lines but I can't figure them out:

```
debug/moc_abstractglwidget.o:(.rodata._ZTV16AbstractGLWidget[vtable for AbstractGLWidget]+0x64): undefined reference to `AbstractGLWidget::keyPressEvent(QKeyEvent*)'

debug/moc_abstractglwidget.o:(.rodata._ZTV16AbstractGLWidget[vtable for AbstractGLWidget]+0x108): undefined reference to `AbstractGLWidget::timeOut()'

debug/moc_abstractglwidget.o:(.rodata._ZTV16AbstractGLWidget[vtable for AbstractGLWidget]+0x10c): undefined reference to `AbstractGLWidget::timeOutSlot()'
```

I made two OpenGL classes: One is Abstract and the other one is the one I am working on. I made an abstract class to include a timer, which is not in the original QGLWidget class. All functions but the constructor are pure virtual functions, ex: *'virtual void keyPressEvent(QKeyEvent*) = 0;'*. In the constructor I connected QTimer's timeout signal to my class timeOutSlot. In my Base Class, the second one, every function is implemented. They are empty except timeOutSlot calls timeOut function.

And sudo ldconfig doesn't return nothing...

However, I am sure the problem resides in the missing library files. Neither libopengl.a or libglu.a is found on my hard drive. And I guess there are going to be .so parts for them so...

@abhilashm86: These packages are installed. And if you look at the make instructions these options are included. I still can't find the opengl library files.

---

### Post by Zugzwang on 2009-03-15
The problem lies in your implementation. The error message states that the implementation of "AbstractGLWidget::keyPressEvent(QKeyEvent*)" cannot be found. It looks like you declared this function but have not defined it in any .cpp/.C/whatever function referenced in your Makefile. So either you forgot to define them or you are not compiling/linking against the source/compiled files where you defined them.

---

### Post by Firestom on 2009-03-15
This function is a pure virtual function. You cannot implement a pure virtual function, so how do you want me to solve this?

Here is the .cpp source:
```
#include "abstractglwidget.h"

AbstractGLWidget::AbstractGLWidget(int timerInterval, QWidget *parent) : QGLWidget(parent)
{
    m_timer = new QTimer();//Pointeur sur QTimer
    m_timer->setInterval(timerInterval);//On met l'intervalle du timer à l'intervalle demandée

    QObject::connect(m_timer, SIGNAL(timeout()), this, SLOT(timeOutSlot()));//À chaque timeout, appeler le timeOutSlot
}
```

Here is the .h source:
```
#ifndef ABSTRACTGLWIDGET_H
#define ABSTRACTGLWIDGET_H

#include <QWidget>
#include <QtOpenGL>
#include <QGLWidget>
#include <QTimer>

class AbstractGLWidget : public QGLWidget
{
    Q_OBJECT

public:
    AbstractGLWidget(int timerInterval, QWidget *parent);//Constructeur

protected:
    virtual void initializeGL() = 0;//Initialisation d'OpenGL
    virtual void resizeGL(int width, int height) = 0;//Redimensionnement de la fenêtre d'OpenGL
    virtual void paintGL() = 0;//"Peindre" les objets sur la fenêtre

    virtual void keyPressEvent(QKeyEvent *e);//Quand une touche est enfoncée
    virtual void timeOut();//Quand le timer arrive à un temps mort

protected slots:
    virtual void timeOutSlot();//Slot connecté au Timeout du timer

private:
    QTimer *m_timer;//Timer
};

#endif // ABSTRACTGLWIDGET_H
```

---

### Post by Zugzwang on 2009-03-15
> **Firestom said:**
> This function is a pure virtual function. You cannot implement a pure virtual function, so how do you want me to solve this?


It seems like you did not declare these three function to be purely virtual, since you wrote:
```

virtual void keyPressEvent(QKeyEvent *e);//Quand une touche est enfoncée

```
and not:
```

virtual void keyPressEvent(QKeyEvent *e) = 0;//Quand une touche est enfoncée

```
in your header file. The same goes for the other two functions.

---

### Post by Firestom on 2009-03-15
Oh, that was a simple inattention that caused me this trouble. It works now, thanks! (So no, I was not lacking any library file)

---

### Post by Firestom on 2009-03-15
q

---

