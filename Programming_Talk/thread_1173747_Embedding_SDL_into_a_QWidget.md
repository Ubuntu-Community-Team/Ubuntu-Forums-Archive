---
title: "Embedding SDL into a QWidget"
date: 2009-05-30
forum: Programming Talk
---

### Post by skullmunky on 2009-05-30
Following up on the MLT code sample I posted below, I'm now trying to embed the MLT player into a Qt application.  Mlt provides a player that uses SDL, and it appears that the way you're supposed to use it is by simply setting the window ID to make it use your Qt window instead of creating its own.  

I can make this work fine, by getting the winId() from my QMainWindow.  But I'd really like to have it embedded into another widget inside the window, not the whole window.  

When I do that, though, I get this X error:
```

X Error: BadGC (invalid GC parameter) 13                                              
  Extension:    133 (Uknown extension)                                                
  Minor opcode: 19 (Unknown request)                                                  
  Resource id:  0x380000b  

```

here's my code, or at least the main.cpp : 
```

#include <QtGui/QApplication>
#include "mainwindow.h"
#include <iostream>
#include <Mlt.h>

int main(int argc, char *argv[])
{
    Mlt::Profile *profile;
    Mlt::Repository *repository;
    Mlt::Consumer *consumer;
    Mlt::Producer *producer;
    int winid;

    QApplication a(argc, argv);
    MainWindow w;
    QWidget *ViewWidget;

    ViewWidget = w.findChild<QWidget *>("ViewWidget");

    profile = new Mlt::Profile();
    repository = Mlt::Factory::init();

    if (repository)
    {
        consumer = new Mlt::Consumer(*profile,"sdl_preview");
        producer = new Mlt::Producer(*profile,NULL,argv[1]);
        consumer->connect(*producer);

        w.show();

        winid = ViewWidget->winId();
        std::cout << "Window ID: " << winid << "\n";
        consumer->set("window_id",winid);

        consumer->start();

        a.exec();

        delete(consumer);
        delete(producer);
        Mlt::Factory::close();
    }
    else
    {
        std::cerr << "Unable to locate factory modules\n";
    }
    return 0;
}

```

---

### Post by haTem on 2009-06-01
I'm not sure what MLT is, but you can try having Qt handle the embedding using a QX11EmbedContainer.

Have Mlt create its own window, or if that's not possible, create a second QMainWindow to embed it as you're doing now. Then you just have to make your ViewWidget a QX11EmbedContainer, and get the winId of the Mlt window and do:
```
ViewWidget->embedClient(theMltWinId);
```

Have a look here [http://doc.trolltech.com/4.5/qx11embedcontainer.html](http://doc.trolltech.com/4.5/qx11embedcontainer.html)

I haven't tried this myself, but it might be worth a try.

---

### Post by skullmunky on 2009-06-02
Thanks, I'll try that.  

MLT is the media handling toolkit that powers Kdenlive:

[http://www.mltframework.org](http://www.mltframework.org)

---

### Post by skullmunky on 2009-06-02
Turns out you can make this work just by ensuring that the Qt app uses native windows for its widgets:

```

  QApplication app(argc, argv);
  
  app.setAttribute(Qt::AA_NativeWindows,true);

```

---

