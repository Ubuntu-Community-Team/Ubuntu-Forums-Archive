---
title: "Gtkmm: Modify background colour of DrawingArea"
date: 2012-04-09
forum: Programming Talk
---

### Post by fallenshadow on 2012-04-09
This is starting to wreck my head with the lack of good useful non-outdated information.

How does one change the background colour of a drawing area? Note that I am using a .glade file, so a get_widget will most likely be involved.

Here is my current attempt:

[PHP]
refBuilder->get_widget("imageArea", imageArea);
imageArea->override_background_color(Gdk::RGBA("red"));
[/PHP]

Any help on this will be greatly appreciated!

---

### Post by fallenshadow on 2012-04-10
Do I need something above this to do with GDK?

---

### Post by CynicRus on 2012-04-10
try this:
```

Gdk::Color color;
color = //you color
imageArea->modify_bg(Gtk::STATE_NORMAL, color);

```

---

### Post by t1497f35 on 2012-04-10
It's weird.. I'm using a DrawingArea and I'm drawing the background myself the way I want, if want I can make it blue with pink dots and a photo of Santa Claus in the background. Can't you do it from your on_draw() method?

---

### Post by fallenshadow on 2012-04-10
CynicRus: I tried your code with some of mine and I got this:

```
error: ‘class Gtk::DrawingArea’ has no member named ‘modify_bg’
```

Also what format does the colour have to be in?

> Can't you do it from your on_draw() method? 

I don't have a method for this, Im just trying to set the background colour at startup.

---

### Post by CynicRus on 2012-04-10
> **t1497f35 said:**
> It's weird.. I'm using a DrawingArea and I'm drawing the background myself the way I want, if want I can make it blue with pink dots and a photo of Santa Claus in the background. Can't you do it from your on_draw() method?

```

Gtk::Widget*
Window::Drawing(int width, int height)
{
    Gtk::Fixed* box = manage(new Gtk::Fixed);
    box->set_size_request(width, height);
    Gtk::DrawingArea* borders[4];
    for (int i = 0; i < 4; i++) {
        borders[i] = manage(new Gtk::DrawingArea);
        borders[i]->modify_bg_pixmap(Gtk::STATE_NORMAL, "<none>");
        borders[i]->modify_bg(Gtk::STATE_NORMAL, Gdk::Color("#ac40ef"));
    }
    borders[0]->set_size_request(width, DebugLayout::CONN_BORDER);
    borders[1]->set_size_request(DebugLayout::CONN_BORDER, height-DebugLayout::CONN_BORDER*2);
    borders[2]->set_size_request(DebugLayout::CONN_BORDER, height-DebugLayout::CONN_BORDER*2);
    borders[3]->set_size_request(width, DebugLayout::CONN_BORDER);
    box->put(*borders[0], 0, 0);
    box->put(*borders[1], 0, DebugLayout::CONN_BORDER);
    box->put(*borders[2], width-DebugLayout::CONN_BORDER, DebugLayout::CONN_BORDER);
    box->put(*borders[3], 0, height-DebugLayout::CONN_BORDER);
    
    return box;
}


```If i understand you.

@fallenshadow
#include <gtkmm/drawingarea.h> or #include <gtkmm.h> - If my memory does not fail

---

### Post by fallenshadow on 2012-04-10
I still get this message... are you using Gtkmm2 or Gtkmm3? (Gtk2 or Gtk3?)

```
error: ‘class Gtk::DrawingArea’ has no member named ‘modify_bg’
```

---

### Post by t1497f35 on 2012-04-10
This sets the default bg color to yellow:

```

#include <gtkmm.h>

class Canvas : public Gtk::DrawingArea {
    public:
    Canvas(){}
    virtual ~Canvas(){}
    
    virtual bool
    on_draw(const Cairo::RefPtr<Cairo::Context> &cr) {
        cr->set_source_rgb(1, 1, 0);
        cr->rectangle(0, 0, get_width(), get_height());
        cr->fill();
        return true;
    }
};

int main(int argc, char *argv[]) {
    Gtk::Main kit(argc, argv);
    Gtk::Window win;
    Canvas canvas;
    win.add(canvas);
    win.show_all();
    kit.run(win);
    return 0;
}

```But if the OP wants a glide-only solution then I dunno, logically the DrawingArea isn't supposed to have any default background color since the very idea of a DrawingArea is for the programmer to paint it by hand from the on_draw() method.

---

### Post by fallenshadow on 2012-04-11
Im not sure is it the DrawingArea I want to modify. Basically I want the background of the area around where the canvas will be to be the same dark colour in the picture on this blog post.

[http://kapo-cpp.blogspot.com/2008/05/resize-pixbuf.html](http://kapo-cpp.blogspot.com/2008/05/resize-pixbuf.html)

---

### Post by t1497f35 on 2012-04-11
When I have issues I usually post an example that compiles with a screenshot pointing to what's exactly wrong so people know exactly what I need so I don't waste hours/days explaining.

---

### Post by fallenshadow on 2012-04-12
Ok I think I will give up on doing this.. I thought it could easily be done with one line of code but as with most things in GTK its just not as easy as it should be!

---

