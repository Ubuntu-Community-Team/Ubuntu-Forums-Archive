---
title: "c++ and glade"
date: 2010-06-06
forum: Programming Talk
---

### Post by xealous on 2010-06-06
Hi, I wanna learn building a gui app with glade and c++ but i couldn't find any tutorial or example. can you please help me. even a simple example is ok.

---

### Post by Dr Belka on 2010-06-06
ditto.  I would love to learn more about the whole glade and gtkmm deal.  

I have found some tutorials, but none of them were very good.

---

### Post by tookyourtime on 2010-06-06
This is how I do it, you can use it with any .glade file. It shows 2 separate windows in the same application. Obviously you get the idea, I'm not going to post the Toolbox class files, because it would just be repeating the Canvas class.

When I was starting out, I had lots of setup/compiling issues. So if you have any questions, just ask. It might save you fiddling for hours.

Any widgets that you want to use in the code need to be loaded into pointers with, for example:
```

Gtk::Window * CanvasWindow;
refBuilder->get_widget("CanvasWindow", CanvasWindow);
```Main:
```

#include <gtkmm.h>
#include "Canvas.h"
#include "Toolbox.h"

int main(int argc, char** argv)
{
    Gtk::Main kit(argc, argv);

    Canvas MyCanvas;
    Toolbox MyToolbox;

    Gtk::Main::run();
}

```Canvas.h
```
#pragma once
#include <gtkmm.h>

class Canvas
{
    public:
        Canvas();
        ~Canvas();

        Gtk::Window * CanvasWindow;

    protected:
        //Signal handlers:
        bool on_button_press_event(GdkEventButton *event);
};

```Canvas.cpp
```

#include <gtkmm.h>
#include "Canvas.h"

Canvas::Canvas()
    :CanvasWindow(0)
{
    Glib::RefPtr<Gtk::Builder> refBuilder = Gtk::Builder::create();
    //this is where you'll need to use your file
    refBuilder->add_from_file("glade/canvas.glade");
    refBuilder->get_widget("CanvasWindow", CanvasWindow);

    if(CanvasWindow)
    {
        CanvasWindow->signal_button_press_event().connect( sigc::mem_fun(*this,
                                                                   &Canvas::on_button_press_event) );
        CanvasWindow->show();
    }
}

Canvas::~Canvas()
{}

bool Canvas::on_button_press_event(GdkEventButton *event)
{
    //do stuff
    return true;
}

```

---

