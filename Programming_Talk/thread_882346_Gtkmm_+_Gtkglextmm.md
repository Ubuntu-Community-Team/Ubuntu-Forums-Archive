---
title: "Gtkmm + Gtkglextmm"
date: 2008-08-06
forum: Programming Talk
---

### Post by wild13 on 2008-08-06
Hi im trying to create a opengl context inside of a Gtk window using gtkmm. Only problem is when my widget gets to configure_event_callback() it segfualts so in short i see nothing. Please help me if you can code is below.

```

#include <gtkmm.h>
#include <gtkglmm.h>

class cHordeWidget : public Gtk::DrawingArea, public Gtk::GL::Widget<cHordeWidget>{
    public:
        cHordeWidget();
        virtual ~cHordeWidget();

    protected:
        virtual void on_realize();
        virtual bool on_configure_event(GdkEventConfigure* event);
        virtual bool on_expose_event(GdkEventExpose* event);
    private:
        ResHandle logoRes;
};

```

```
#include "../include/cHordeWidget.hpp"


cHordeWidget::cHordeWidget(){

    Glib::RefPtr<Gdk::GL::Config> glconfig;

    glconfig = Gdk::GL::Config::create(Gdk::GL::MODE_RGB | Gdk::GL::MODE_DEPTH | Gdk::GL::MODE_DOUBLE);

    set_gl_capability(glconfig);

}

cHordeWidget::~cHordeWidget(){
}

void cHordeWidget::on_realize(){
    Gtk::DrawingArea::on_realize();

    //get gl::window
    Glib::RefPtr<Gdk::GL::Window> glwindow = get_gl_window();

    glwindow->gl_begin(get_gl_context());


    glwindow->gl_end();
}

bool cHordeWidget::on_configure_event(GdkEventConfigure* event){

    //get gl::window
    Glib::RefPtr<Gdk::GL::Window> glwindow = get_gl_window();

    glwindow->gl_begin(get_gl_context());
 

    glwindow->gl_end();

    return true;
}

bool cHordeWidget::on_expose_event(GdkEventExpose* event){

    //get gl::window
    Glib::RefPtr<Gdk::GL::Window> glwindow = get_gl_window();

    glwindow->gl_begin(get_gl_context());

    //main loop
    glwindow->gl_end();
    return true;
}



```

The other code is just the window creation and the main.cpp. I would appreciate any help you could give me. 

Version numbers:
gtk 2.0
gtkmm-2.4
gtkgl-2.0
gtkglet-1.0
gtkglextmm-1.2
gdk-2.0
gdkmm-2.4

---

### Post by nrs on 2008-08-07
I don't have access to my Linux machine at the moment, so I can't compile and test your code, I will soon though. Might as well start with the simple stuff, are you calling Gtk::GL::init from main? Not calling it is one of the many fun ways to get a segfault with it.

You should also be testing GL::Config::create for failure,

---

### Post by wild13 on 2008-08-07
Yes i do call it and thanks for the reply :)

here is the updated code with the main.cpp

```
#ifndef CHORDEWIDGET_HPP_INCLUDED
#define CHORDEWIDGET_HPP_INCLUDED
#include <iostream>
#include <Horde3D.h>
#include <Horde3DUtils.h>
#include <cstdlib>
#include <gtkmm.h>
#include <gtkglmm.h>

class cHordeWidget : public Gtk::GL::DrawingArea{
    public:
        cHordeWidget();
        virtual ~cHordeWidget();

    protected:
        virtual void on_realize();
        virtual bool on_configure_event(GdkEventConfigure* event);
        virtual bool on_expose_event(GdkEventExpose* event);
    private:
        ResHandle logoRes;
};

#endif // CHORDEWIDGET_HPP_INCLUDED

```

```
#include "../include/cHordeWidget.hpp"


cHordeWidget::cHordeWidget(){

    Glib::RefPtr<Gdk::GL::Config> glconfig;

    glconfig = Gdk::GL::Config::create(Gdk::GL::MODE_RGB | Gdk::GL::MODE_DEPTH | Gdk::GL::MODE_DOUBLE);

    set_gl_capability(glconfig);

}

cHordeWidget::~cHordeWidget(){
}

void cHordeWidget::on_realize(){
    Gtk::GL::DrawingArea::on_realize();

    //get gl::window
    Glib::RefPtr<Gdk::GL::Window> glwindow = get_gl_window();

    glwindow->gl_begin(get_gl_context());


    glwindow->gl_end();
}

bool cHordeWidget::on_configure_event(GdkEventConfigure* event){

    //get gl::window
    Glib::RefPtr<Gdk::GL::Window> glwindow = get_gl_window();

    glwindow->gl_begin(get_gl_context());

    glwindow->gl_end();

    return true;
}

bool cHordeWidget::on_expose_event(GdkEventExpose* event){

    //get gl::window
    Glib::RefPtr<Gdk::GL::Window> glwindow = get_gl_window();

    glwindow->gl_begin(get_gl_context());
    glClear(GL_COLOR_BUFFER_BIT);

    //main loop
    glwindow->gl_end();
    glwindow->swap_buffers ();

    return true;
}



```

```
#include <gtkmm.h>
#include "include/cHordeWidget.hpp"

int main(int argc, char *argv[]){
    Gtk::Main init (argc, argv);
    Gtk::GL::init (argc, argv);

    Gtk::Window window;
    window.set_title ("Widget Demo");

    cHordeWidget drawing;
    window.add (drawing);

    window.show_all ();

    Gtk::Main::run (window);

    return EXIT_SUCCESS;

}

```

---

### Post by nrs on 2008-08-07
Both versions compile & run fine for me. Interesting.

---

### Post by wild13 on 2008-08-07
Maybe its becuase im on gutsy?
Everything i got from synaptic except gtkglextmm << i had to compile and build that myself.

I cant understand why it wont work for me..

Edit:

Progress i switched it from a gui application to a console and now the window opens but segfualts right after.

---

### Post by nrs on 2008-08-07
> **wild13 said:**
> Maybe its becuase im on gutsy?
Everything i got from synaptic except gtkglextmm << i had to compile and build that myself.

I cant understand why it wont work for me..

Edit:

Progress i switched it from a gui application to a console and now the window opens but segfualts right after.

Well, if you're already compiling it yourself maybe go back and enable full debugging support for it and its immediate dependencies (usually Ubuntu provinces -dbg packages) + your program and post the GDB results. Apparently I'm also using gtkglext 1.2.0.

I'm using Gentoo personally ATM.

---

### Post by wild13 on 2008-08-07
YAY! solved it. it seemed to be a problem with my auto generated make file from cmake.

I spent 30 minutes setting up codeblocks manually with all dependencys and such and it compiled fine. Thansk for your help.

---

