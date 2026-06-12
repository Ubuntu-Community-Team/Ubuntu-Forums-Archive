---
title: "[Cairo] question about expose event"
date: 2010-02-18
forum: Programming Talk
---

### Post by kahumba on 2010-02-18
Hi,
the first few lines at
[http://library.gnome.org/devel/gtkmm-tutorial/unstable/chapter-drawingarea.html.en](http://library.gnome.org/devel/gtkmm-tutorial/unstable/chapter-drawingarea.html.en)
say that
> 
When a     widget is first shown, or **when it is covered and then uncovered  again** it     needs to redraw itself [...] This is     most often done by overriding the virtual     on_expose_event() member  function.
But, after using their following example, I discovered that the widget doesn't redraw itself after cover/uncover (I mean it doesn't call that function). I extended the method to print a message when it gets redrawn and it doesn't print anything on cover/uncover (of the gtk window which holds the widget).

So, anyone knows what's up?
Is the tutorial wrong or am I misunderstanding something?

---

### Post by napsy on 2010-02-18
the "expose-event" is triggered when X marks dirty regions and sends them to Gtk+. Gtk+ handles the dirty regions by default but you can override that if you hook up to that expose event.

---

### Post by kahumba on 2010-02-18
I'm not sure I get you. So, didn't I "hook up"? (I did override the on_expose_event function, is that hooking?) If so, why doesn't it get called on cover/uncover but only when resizing or minimizing the window?

---

### Post by kahumba on 2010-02-18
Btw, here's the example:

main.cpp
```

#include "MyArea.h"

#include <gtkmm/main.h>
#include <gtkmm/window.h>

int main(int argc, char **argv) {
    Gtk::Main kit(argc, argv);
    Gtk::Window win;
    win.set_title("DrawingArea");
    MyArea area;
    win.add(area);
    area.show();
    
    Gtk::Main::run(win);
    return 0;
}

```MyArea.h:
```

#ifndef MY_AREA_H
#define MY_AREA_H

#include <gtkmm/drawingarea.h>

class MyArea : public Gtk::DrawingArea {
public:
    MyArea();
    virtual ~MyArea();
    
protected:
    virtual bool on_expose_event(GdkEventExpose *event);
    
};
#endif

```MyArea.cpp:
```

#include "MyArea.h"
#include <cairomm/context.h>
#include <iostream>

MyArea::MyArea() {
}

MyArea::~MyArea() {
}

bool MyArea::on_expose_event(GdkEventExpose *event) {
    Glib::RefPtr<Gdk::Window> window = get_window();
    if(!window) {
        std::cout << "no window!" << std::endl;
        return true;
    }
    
    Gtk::Allocation allocation = get_allocation();
    const int width = allocation.get_width();
    const int height = allocation.get_height();
    
    int xc = width / 2;
    int yc = height / 2;
    
    Cairo::RefPtr<Cairo::Context> cr = window->create_cairo_context();
    cr->set_line_width(10.0);
    
    cr->rectangle(event->area.x, event->area.y, event->area.width, event->area.height);
    cr->clip();
    static int counter = 0;
    const char *sep = "::";
    //print out that it's getting repainted
    std::cout << "(" << counter++ << ")" << event->area.x << sep << event->area.y
            << sep << event->area.width << sep << event->area.height << std::endl;
    
    cr->set_source_rgb(0.8, 0.0, 0.0);
    cr->move_to(0, 0);
    cr->line_to(xc, yc);
    cr->line_to(0, height);
    cr->move_to(xc, yc);
    cr->line_to(width, yc);
    cr->stroke();
    return true;
}

```

---

### Post by napsy on 2010-02-18
I don't know how that's handled in C++ but if you did the right thing and your callback isn't called, then there probably no need to.

---

