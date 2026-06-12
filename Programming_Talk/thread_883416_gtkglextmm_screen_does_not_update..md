---
title: "gtkglextmm screen does not update."
date: 2008-08-07
forum: Programming Talk
---

### Post by wild13 on 2008-08-07
So i finally get the opengl context and horde3d running. Now the problem is it dosn't refresh/update i get one frame and thats it. I have tried to adapt how the exmaples update the screen but to no prevail so please help :(

*Ive stripped the horde stuff to make it readable*

```
#ifndef CHORDEWIDGET_HPP_INCLUDED
#define CHORDEWIDGET_HPP_INCLUDED
#include <iostream>
#include <Horde3D.h>
#include <Horde3DUtils.h>
#include <cstdlib>
#include <gtkmm.h>
#include <gtkglmm.h>
#include <sstream>
#include <math.h>
#include <iomanip>

using namespace std;


class cHordeWidget : public Gtk::GL::DrawingArea{
    public:
        cHordeWidget();
        virtual ~cHordeWidget();

    protected:
        virtual void on_realize();
        virtual bool on_configure_event(GdkEventConfigure* event);
        virtual bool on_expose_event(GdkEventExpose* event);


    private:

};

#endif // CHORDEWIDGET_HPP_INCLUDED

```

```
#include "../include/cHordeWidget.hpp"

NodeHandle model = 0, cam = 0;

cHordeWidget::cHordeWidget(){

    Glib::RefPtr<Gdk::GL::Config> glconfig;

    glconfig = Gdk::GL::Config::create(Gdk::GL::MODE_RGB | Gdk::GL::MODE_DEPTH | Gdk::GL::MODE_DOUBLE);

    set_gl_capability(glconfig);
    add_events(Gdk::VISIBILITY_NOTIFY_MASK);

}

cHordeWidget::~cHordeWidget(){
    Horde3D::release();
}

void cHordeWidget::on_realize(){
    Gtk::GL::DrawingArea::on_realize();

    //get gl::window
    Glib::RefPtr<Gdk::GL::Window> glwindow = get_gl_window();


    glwindow->gl_begin(get_gl_context());
    //reset my camera view and such here

    glwindow->gl_end();
}

bool cHordeWidget::on_configure_event(GdkEventConfigure* event){

    //get gl::window
    Glib::RefPtr<Gdk::GL::Window> glwindow = get_gl_window();

    glwindow->gl_begin(get_gl_context());

    Horde3D::init();

    glwindow->gl_end();

    return true;
}

bool cHordeWidget::on_expose_event(GdkEventExpose* event){

    //get gl::window
    Glib::RefPtr<Gdk::GL::Window> glwindow = get_gl_window();

    glwindow->gl_begin(get_gl_context());
    //i Put my main game loop here *updating and all*
    glwindow->swap_buffers();
    glwindow->gl_end();

    return true;
}

```

```
#ifndef CWINDOW_HPP_INCLUDED
#define CWINDOW_HPP_INCLUDED
#include <gtkmm.h>
#include "cHordeWidget.hpp"

class cWindow : public Gtk::Window{
    public:
        cWindow();
        virtual ~cWindow();

    protected:

        virtual bool on_key_press_event(GdkEventKey* event);

    private:
        Gtk::VBox m_vBox;

        cHordeWidget m_hordeWidget;

};

#endif // CWINDOW_HPP_INCLUDED

```

```
#include "../include/cWindow.hpp"

cWindow::cWindow(){

    set_title("Horde with gtkmm");
    set_reallocate_redraws(true);

    add(m_vBox);

    m_hordeWidget.set_size_request(800,600);

    m_vBox.pack_start(m_hordeWidget);

    show_all();
}

cWindow::~cWindow(){

}

bool cWindow::on_key_press_event(GdkEventKey* event){

    switch (event->keyval)
    {
    case GDK_a:
      std::cout<<"test";
      break;

    case GDK_Escape:
      Gtk::Main::quit();

      break;
      default:
      return true;
    }

    return true;
}

```


```
#include <gtkmm.h>
#include "include/cWindow.hpp"

int main(int argc, char *argv[]){

    Gtk::Main init (argc, argv);
    Gtk::GL::init (argc, argv);

    cWindow window;

    Gtk::Main::run (window);

    return EXIT_SUCCESS;

}

```

Thats everything.

---

### Post by nrs on 2008-08-08
You need to add an idle handler and invalidate the widget, AFAIK.

---

