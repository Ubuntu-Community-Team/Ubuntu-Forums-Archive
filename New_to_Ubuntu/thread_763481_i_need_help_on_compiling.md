---
title: "i need help on compiling"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by nerddy on 2008-04-23
hi guys.. i have been compiling this codes for weeks.. but i cant seem to compile it with makefiles.. is there anyway i can compile these source codes?

File: [COLOR="Blue"]myarea.h[/COLOR] 

#ifndef GTKMM_EXAMPLE_MYAREA_H
#define GTKMM_EXAMPLE_MYAREA_H

#include <gtkmm/drawingarea.h>

class MyArea : public Gtk::DrawingArea
{
public:
  MyArea();
  virtual ~MyArea();

protected:
  //Override default signal handler:
  virtual bool on_expose_event(GdkEventExpose* event);
};

#endif // GTKMM_EXAMPLE_MYAREA_H


[COLOR="Blue"]main.cc[/COLOR] 

#include "myarea.h"
#include <gtkmm/main.h>
#include <gtkmm/window.h>

int main(int argc, char** argv)
{
   Gtk::Main kit(argc, argv);

   Gtk::Window win;
   win.set_title("DrawingArea");

   MyArea area;
   win.add(area);
   area.show();

   Gtk::Main::run(win);

   return 0;
}

[COLOR="Blue"]myarea.cc [/COLOR]

#include "myarea.h"
#include <cairomm/context.h>

MyArea::MyArea()
{
}

MyArea::~MyArea()
{
}

bool MyArea::on_expose_event(GdkEventExpose* event)
{
  // This is where we draw on the window
  Glib::RefPtr<Gdk::Window> window = get_window();
  if(window)
  {
    Gtk::Allocation allocation = get_allocation();
    const int width = allocation.get_width();
    const int height = allocation.get_height();

    // coordinates for the center of the window
    int xc, yc;
    xc = width / 2;
    yc = height / 2;

    Cairo::RefPtr<Cairo::Context> cr = window->create_cairo_context();
    cr->set_line_width(10.0);

    // clip to the area indicated by the expose event so that we only redraw
    // the portion of the window that needs to be redrawn
    cr->rectangle(event->area.x, event->area.y,
            event->area.width, event->area.height);
    cr->clip();

    // draw red lines out from the center of the window
    cr->set_source_rgb(0.8, 0.0, 0.0);
    cr->move_to(0, 0);
    cr->line_to(xc, yc);
    cr->line_to(0, height);
    cr->move_to(xc, yc);
    cr->line_to(width, yc);
    cr->stroke();
  }

  return true;
}

Please help me out!!! THANKS!!!

---

### Post by Xiong Chiamiov on 2008-04-23
I'm sorry, but this isn't a coding forum.  There are plenty out there with lots of people willing to help you; codingforums.com is a good one.

---

### Post by Wim Sturkenboom on 2008-04-23
@xiong
But [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39) is

@nerddy
please use code tags in your next post (when posting source code)

---

