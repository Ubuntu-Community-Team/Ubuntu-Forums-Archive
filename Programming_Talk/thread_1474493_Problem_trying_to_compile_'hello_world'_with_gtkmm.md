---
title: "Problem trying to compile 'hello world' with gtkmm"
date: 2010-05-06
forum: Programming Talk
---

### Post by LoneStar++ on 2010-05-06
I have been trying to learn how to use gtkmm by following the guide found at:

[http://library.gnome.org/devel/gtkmm-tutorial/](http://library.gnome.org/devel/gtkmm-tutorial/) I am trying to compile the hello world program (code found below) that they go through in the tutorial by running

```
g++ helloworld.cc -o helloworld `pkg-config --cflags --libs gtkmm-2.4`
```When I do this I get the following error:

```
/usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/crt1.o: In function `_start':
/build/buildd/eglibc-2.10.1/csu/../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status
```I have search all over the place trying to figure out why this is happening, but I keep coming up empty.

Any assistance would be greatly appreciated!

File: helloworld.h

```
#ifndef GTKMM_EXAMPLE_HELLOWORLD_H
#define GTKMM_EXAMPLE_HELLOWORLD_H

#include <gtkmm/button.h>
#include <gtkmm/window.h>

class HelloWorld : public Gtk::Window
{

public:
  HelloWorld();
  virtual ~HelloWorld();

protected:
  //Signal handlers:
  void on_button_clicked();

  //Member widgets:
  Gtk::Button m_button;
};

#endif // GTKMM_EXAMPLE_HELLOWORLD_H
```
File: main.cc
```
#include <gtkmm/main.h>
#include "helloworld.h"

int main (int argc, char *argv[])
{
  Gtk::Main kit(argc, argv);

  HelloWorld helloworld;
  //Shows the window and returns when it is closed.
  Gtk::Main::run(helloworld);

  return 0;
}
```File: helloworld.cc 
```
#include "helloworld.h"
#include <iostream>

HelloWorld::HelloWorld()
: m_button("Hello World")   // creates a new button with label "Hello World".
{
  // Sets the border width of the window.
  set_border_width(10);

  // When the button receives the "clicked" signal, it will call the
  // on_button_clicked() method defined below.
  m_button.signal_clicked().connect(sigc::mem_fun(*this,
              &HelloWorld::on_button_clicked));

  // This packs the button into the Window (a container).
  add(m_button);

  // The final step is to display this newly created widget...
  m_button.show();
}

HelloWorld::~HelloWorld()
{
}

void HelloWorld::on_button_clicked()
{
  std::cout << "Hello World" << std::endl;
}
```

---

### Post by Compyx on 2010-05-06
You need to compile both helloworld.cc and main.cc into object files and then link them together into an executable (called helloworld in my example):
```

g++ -c main.cc `pkg-config --cflags --libs gtkmm-2.4`
g++ -c helloworld.cc `pkg-config --cflags --libs gtkmm-2.4`
g++ main.o helloworld.o -o helloword `pkg-config --cflags --libs gtkmm-2.4`

```

---

### Post by LoneStar++ on 2010-05-06
Oh yeah that makes sense now. Thanks for your help!

---

