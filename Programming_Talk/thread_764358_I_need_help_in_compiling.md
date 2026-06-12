---
title: "I need help in compiling"
date: 2008-04-23
forum: Programming Talk
---

### Post by nerddy on 2008-04-23
hi guys.. i have been compiling this codes for weeks.. but i cant seem to compile it with makefiles.. is there anyway i can compile these source codes?

File: myarea.h 

[PHP]#ifndef GTKMM_EXAMPLE_MYAREA_H
#define GTKMM_EXAMPLE_MYAREA_H

#include <gtkmm/drawingarea.h>

class MyArea : public Gtk:: DrawingArea
{
public:
MyArea();
virtual ~MyArea();

protected:
//Override default signal handler:
virtual bool on_expose_event(GdkEventExpose* event);
};

#endif // GTKMM_EXAMPLE_MYAREA_H


main.cc 

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

myarea.cc 

#include "myarea.h"
#include <cairomm/context.h>

MyArea::MyArea()
{
}

MyArea::~MyArea()
{
}

bool MyArea:: on_expose_event(GdkEventExpose* event)
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
}[/PHP]

Please help me out!!! THANKS!!!

---

### Post by lnostdal on 2008-04-23
i don't know what your current problem is and i'm too lazy to copy/paste the files to check etc. 

..but..

..maybe i suggest SCons or CMake instead of using Makefiles? you will find these tools way less painful than the old make tool

---

### Post by WW on 2008-04-23
> **nerddy said:**
> hi guys.. i have been compiling this codes for weeks.. but i cant seem to compile it with makefiles.. is there anyway i can compile these source codes?

So you can compile and link them "by hand" in the command line, and you are just having trouble getting a Makefile to work?  Show the Makefile that you are trying to use.

---

### Post by nerddy on 2008-04-23
what is Cmake? yah im trying to link them together.. 

i got my makefile.am as well as the source code from this website [http://www.gtkmm.org/docs/gtkmm-2.4/examples/book/drawingarea/arcs/](http://www.gtkmm.org/docs/gtkmm-2.4/examples/book/drawingarea/arcs/).. 

the makefile.am goes like this

include $(top_srcdir)/examples/Makefile.am_fragment

#Build the executable, but don't install it.
noinst_PROGRAMS = drawingarea
drawingarea_SOURCES = main.cc myarea.h myarea.cc

---

### Post by WW on 2008-04-23
"makefile.am" is an input to the command **automake**, which is part of the "autotools" suite.  Are you trying to use **automake**, or plain old **make**?  The manual for **make** is [here](http://www.gnu.org/software/make/manual/html_node/index.html); you can also find an assortment of tutorials by googling for "gnu make".

---

### Post by nerddy on 2008-04-23
i read it before , that is just to difficult for me to understand.. now i wanna use Cmake.. can u teach me how to use it?

---

### Post by lnostdal on 2008-04-23
create a file SConstruct with this in it:
```

dbg = Environment(CCFLAGS = ['-g', '-Wall', '-std=c99'],
                  CXXFLAGS = ['-g', '-Wall'])

# Current set environment
#########################
env = dbg
env.ParseConfig('pkg-config --cflags --libs gtkmm-2.4')

env.Program('main', ['main.cc', 'myarea.cc'])

```

..place it in the same folder as your source files, then type scons and press enter to compile and link

---

### Post by lnostdal on 2008-04-23
ok, i just noticed that you are also using the cairo libraries:

```

root@ibmr52:/home/lars# pkg-config --list-all | grep cairo
...
cairomm-1.0                 cairomm - C++ wrapper for cairo
...

```

..so in other words, add this to SConstruct:

```

env.ParseConfig('pkg-config --cflags --libs cairomm-1.0')

```

---

### Post by dwhitney67 on 2008-04-23
Makefiles are pretty easy; it's too bad that you gave up on learning how to create one so easily.

Here's a simple Makefile you can use to build your project:
```
SRCS     := $(wildcard *.cc)
OBJS     := $(SRCS:.cc=.o)

APP      := my_area

CXXFLAGS := -g

# Expand the following if necessary to specify the header-file and
# library paths for the GTK source and library files.
#
INCPATH  := -I./
LIBPATH  := 
LIBS     :=

DEP_FILE := .depend

.PHONY: clean distclean


# Link all object files to create the executable (run 'make')
$(APP): $(OBJS)
        @echo Makefile - linking $@
        @$(CXX) $^ $(LIBPATH) $(LIBS) -o $@

# Create the object file(s)
.cc.o:
        @echo Makefile - compiling $<
        @$(CXX) $(CXXFLAGS) $(INCPATH) -c $< -o $@

clean:
        $(RM) *.o

distclean: clean
        $(RM) $(APP)
        $(RM) $(DEP_FILE)

# Setup the dependencies (run 'make depend')
depend $(DEP_FILE):
        @echo Makefile - creating dependencies for: $(SRCS)
        @$(RM) $(DEP_FILE)
        @$(CXX) -E -MM $(INCPATH) $(SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
```

P.S.  Tab-spaces are required to indent command statements.

---

### Post by nerddy on 2008-04-24
hey i type scons on the terminal, it says bash:scons:command not found

---

### Post by LaRoza on 2008-04-24
> **nerddy said:**
> hey i type scons on the terminal, it says bash:scons:command not found

Install scons first.

```

sudo aptitude install scons

```

---

### Post by tseliot on 2008-04-24
nerddy:
I put your code between PHP tags so that it doesn't take up too much space.

---

### Post by nerddy on 2008-04-24
HEY SCONS IS USEABLE!!! BUT I HAVE A LAST QUESTIONS..
I faced an error when compiling.. it says myarea.cc:45::error: 'class gdk::window' has no member named 'create_cairo_context'.. what it meant by that?? can somehelp me out??

---

