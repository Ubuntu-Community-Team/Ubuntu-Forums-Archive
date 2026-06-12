---
title: "How compiz ezoom plugin works?"
date: 2013-03-04
forum: Programming Talk
---

### Post by odabart on 2013-03-04
Hello to everyone, i enter in this forum for ask this question, how the plugin ezoom of compiz works? i downloaded the code that i attached here, but i dont get how it works, i try using the XComposite extension of xlib for get the entire desktop screenshot and showing it in a overlay window created using XCompositeGetOverlayWindow but that gives me an repetition of the screen, here is my code wrote in Qt: 

**the header file:**

```
#ifndef MAPPLICATION_H
#define MAPPLICATION_H


#include <QApplication>
#include <QDebug>
#include <QVBoxLayout>
#include <QPaintDevice>
#include <QX11Info>
#include <X11/Xlib.h>
#include <X11/Xutil.h>
#include <X11/Xatom.h>
#include <X11/extensions/Xcomposite.h>
#include <X11/extensions/Xrender.h>
#include <X11/extensions/shape.h>
#include <X11/extensions/Xdamage.h>


#include <QPainter>
#include <QPixmap>
#include <QWidget>
#include <QLabel>
#include <QDesktopWidget>




class MApplication : public QApplication{
    Q_OBJECT
signals:
    void renderReady();
public:
    MApplication(int argc,char *argv[]) ;
    bool x11EventFilter(XEvent *event);
    Window wId;
    int damage_event;
    int damage_error;
    Display *dpy;
};


class MWindow : public QWidget {
    Q_OBJECT




public:
    MWindow(QWidget *parent = 0);


    void init();
    void reparenting();
    void paintEvent(QPaintEvent *event);


    Display *dpy;
    Window rootw;
    bool hasNamePixmap;


    int event_base;
    int error_base;


    ::XWindowAttributes attr;
    ::Window wId;


    ::XRenderPictFormat *format;
    bool hasAlpha;
    int x;
    int y;
    int width ;
    int height ;


    ::XRenderPictureAttributes pa;


    int damage_event;
    int damage_error;
    ::Damage damage;
    ::Picture picture;


    Picture frontBuffer;


    QDesktopWidget desk;
public:
    QPixmap pixmap;
public slots:
    void onUpdate();
};


#endif // MAPPLICATION_H

```

[B]the source file: 

[/B]```
#include "mapplication.h"


MWindow::MWindow(QWidget *parent) :
    QWidget(parent)
{


}


void MWindow::init()
{
    //setGraphicsSystem("native");
    dpy = QX11Info::display();
    rootw =QX11Info::appRootWindow();


    qDebug("display %d, rootw %d",dpy,rootw);


    hasNamePixmap = false;




    if (::XCompositeQueryExtension(dpy, &event_base, &error_base)) {
        int major = 0;
        int minor = 2;
        ::XCompositeQueryVersion(dpy, &major, &minor);


        if (major > 0 || minor >= 2){
            qDebug("Has NamePixmap");
            hasNamePixmap = true;
        }
    }


    ::XGrabServer(dpy);
    ::XCompositeRedirectSubwindows(dpy,RootWindow(dpy,DefaultScreen(dpy)),
                                   CompositeRedirectAutomatic);
    ::XSelectInput( dpy, RootWindow(dpy,DefaultScreen(dpy)),
                SubstructureNotifyMask | ExposureMask |
                StructureNotifyMask | PropertyChangeMask );


    wId = rootw;//XDefaultRootWindow(dpy);


    //XCompositeRedirectWindow(dpy,wId,CompositeRedirectAutomatic);
    ::XSelectInput( dpy, wId,
                SubstructureNotifyMask | ExposureMask |
                StructureNotifyMask | PropertyChangeMask );


    ::XGetWindowAttributes(dpy, wId, &attr);


    format = ::XRenderFindVisualFormat(dpy, attr.visual);
    hasAlpha = (format->type == PictTypeDirect && format->direct.alphaMask);
    x         = attr.x;
    y         = attr.y;
    width     = attr.width;
    height    = attr.height;


    qDebug("x %d y %d w %d h %d\n", x, y, width, height);






    XRenderPictFormat *defformat = ::XRenderFindVisualFormat(dpy,  DefaultVisual( dpy, DefaultScreen(dpy) ));


    pa.subwindow_mode = IncludeInferiors;
    picture = XRenderCreatePicture(dpy, wId, format, CPSubwindowMode, &pa);
    frontBuffer = XRenderCreatePicture( dpy, XDefaultRootWindow(dpy), defformat, CPSubwindowMode, &pa );


   
    ::XUngrabServer(dpy);
    


    pixmap = QPixmap::fromX11Pixmap(wId,QPixmap::ExplicitlyShared);


    // Tracking damage
    ::XDamageQueryExtension(dpy, &damage_event, &damage_error);
    damage = ::XDamageCreate(dpy, wId, XDamageReportNonEmpty);


}


void MWindow::reparenting()
{
    Window overlay = XCompositeGetOverlayWindow(dpy,XDefaultRootWindow(dpy));


    qDebug("efective win id %d",this->effectiveWinId());




    XserverRegion region = XFixesCreateRegion (dpy, NULL, 0);


    XFixesSetWindowShapeRegion (dpy, this->effectiveWinId(), ShapeBounding, 0, 0, 0);
    XFixesSetWindowShapeRegion (dpy, this->effectiveWinId(), ShapeInput, 0, 0, region);


    XFixesDestroyRegion (dpy, region);


     XReparentWindow(dpy,this->effectiveWinId(),overlay,50,0);
}


void MWindow::paintEvent(QPaintEvent *event)
{
    QPainter painter(this);


    if(!pixmap.isNull()){
        qDebug("pixmap is not empty");
        painter.drawImage(0,0,pixmap.toImage());
    }


    painter.end();
}






void MWindow::onUpdate()
{
    pixmap = QPixmap::fromX11Pixmap(wId,QPixmap::ExplicitlyShared);
    update();


}




MApplication::MApplication(int argc, char *argv[]):
    QApplication(argc,argv)
{


}


bool MApplication::x11EventFilter(XEvent *event)
{
    if (event->type == damage_event + XDamageNotify) {
        ::XDamageNotifyEvent *e = reinterpret_cast<XDamageNotifyEvent *>(event);
        if (e->drawable == wId) {
            qDebug("drawing...");
            XDamageSubtract(dpy, e->damage, None, None);
            /*::XRenderComposite(dpy, hasAlpha ? PictOpOver : PictOpSrc, picture, None,
                           frontBuffer, 0, 0, 0, 0,
                           0, 0, e->geometry.width, e->geometry.height);*/
            //Pixmap pix = XCompositeNameWindowPixmap(dpy,wId);
            emit renderReady();
        }
    }


//        else if (event->type == ConfigureNotify) {
//            XConfigureEvent *e = &event->xconfigure;
//        }


    return false;
}

```

[B]the main file:

[/B]```
#include "mapplication.h"






int main(int argc, char *argv[])
{
    MApplication app(argc, argv);


    MWindow *wind = new MWindow();
     wind->init();


    app.wId = wind->wId;
    app.damage_error = wind->damage_error;
    app.damage_event = wind->damage_event;
    app.dpy = wind->dpy;


     wind->show();
     wind->reparenting();


    return app.exec();
}

```

i know that compiz is written using opengl, but ¿how they got an entire transformation of the screen?

---

