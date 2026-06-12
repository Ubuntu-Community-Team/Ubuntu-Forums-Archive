---
title: "[C++] sigc::mem_fun / GTKmm question (pointers and classes)"
date: 2011-08-14
forum: Programming Talk
---

### Post by Temppu on 2011-08-14
Hi,

And thanks in advance if somebody is able to help me.

I started programming again, having missed seven to eight years. As my history is in TPascal->Java->VB, I decided to learn some C++. While learning, I tried to get rid of bad habits, so I went in classes and such, trying to build easily manageable files.

I am using Ubuntu and wanted to do GUI, so I went for GTKmm. My whole project is now about 6 different header files, from file operations to drawing in Cairo. I am now getting into situations where I have to put information both ways from classes to others. Biggest problem (where I am stuck now) is the signals from buttons to do something in another class:

```
 m_buttonrefresh.signal_clicked().connect( sigc::mem_fun(*this, &Window::on_clicked) );
```

If Window is not the class in who's constructor I this is in, it does not work. For better idea what I am talking about, I made this example:

apu.h
```
#ifndef INDEKSI
#define INDEKSI

#include <gtkmm.h>

class Indeksi
{
public:
  Indeksi();
  virtual ~Indeksi();

	void on_button_clicked();

};

#endif //INDEKSI
```

apu.cc
```
#include "apu.h"
#include <iostream>

Indeksi::Indeksi()
{
}

Indeksi::~Indeksi()
{
}


void Indeksi::on_button_clicked()
{
 std::cout << "teksti";
}
```

helloworld.h
```
#ifndef GTKMM_EXAMPLE_HELLOWORLD_H
#define GTKMM_EXAMPLE_HELLOWORLD_H
#include "apu.h"
#include <gtkmm/button.h>
#include <gtkmm/window.h>



class HelloWorld : public Gtk::Window
{

public:
  HelloWorld();
  virtual ~HelloWorld();

protected: 

  void on_button_clicked(); 
  Gtk::Button m_button;
};

#endif // GTKMM_EXAMPLE_HELLOWORLD_H
```

helloworld.cc
```

#include "helloworld.h"
#include <iostream>



HelloWorld::HelloWorld()
: m_button("Hello World")   
{
  
  set_border_width(10);

  m_button.signal_clicked().connect(sigc::mem_fun(*this, &Indeksi::on_button_clicked));           
  add(m_button);	
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

main.cc
```
#include "helloworld.h"
#include <gtkmm/main.h>

int main (int argc, char *argv[])
{
  Gtk::Main kit(argc, argv);
  HelloWorld helloworld;
  Gtk::Main::run(helloworld); 

  return 0;
}
```

Output:
```

In file included from /usr/include/sigc++-2.0/sigc++/adaptors/adaptor_trait.h:9:0,
                 from /usr/include/sigc++-2.0/sigc++/functors/slot.h:7,
                 from /usr/include/sigc++-2.0/sigc++/signal_base.h:31,
                 from /usr/include/sigc++-2.0/sigc++/signal.h:8,
                 from /usr/include/sigc++-2.0/sigc++/sigc++.h:23,
                 from /usr/include/glibmm-2.4/glibmm/signalproxy.h:13,
                 from /usr/include/glibmm-2.4/glibmm/objectbase.h:23,
                 from /usr/include/glibmm-2.4/glibmm/wrap.h:26,
                 from /usr/include/glibmm-2.4/glibmm/containerhandle_shared.h:25,
                 from /usr/include/glibmm-2.4/glibmm/arrayhandle.h:23,
                 from /usr/include/glibmm-2.4/glibmm.h:83,
                 from /usr/include/gtkmm-2.4/gtkmm.h:87,
                 from apu.h:4,
                 from helloworld.h:3,
                 from helloworld.cc:2:
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h: In function ‘sigc::bound_mem_functor0<T_return, T_obj> sigc::mem_fun(T_obj&, T_return (T_obj2::*)()) [with T_return = void, T_obj = HelloWorld, T_obj2 = Indeksi]’:
helloworld.cc:13:85:   instantiated from here
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h:5453:61: error: no matching function for call to ‘sigc::bound_mem_functor0<void, HelloWorld>::bound_mem_functor0(HelloWorld&, void (Indeksi::*&)())’
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h:1778:3: note: candidates are: sigc::bound_mem_functor0<T_return, T_obj>::bound_mem_functor0(T_obj&, sigc::bound_mem_functor0<T_return, T_obj>::function_type) [with T_return = void, T_obj = HelloWorld, sigc::bound_mem_functor0<T_return, T_obj>::function_type = void (HelloWorld::*)()]
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h:1769:3: note:                 sigc::bound_mem_functor0<T_return, T_obj>::bound_mem_functor0(T_obj*, sigc::bound_mem_functor0<T_return, T_obj>::function_type) [with T_return = void, T_obj = HelloWorld, sigc::bound_mem_functor0<T_return, T_obj>::function_type = void (HelloWorld::*)()]
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h:1760:1: note:                 sigc::bound_mem_functor0<void, HelloWorld>::bound_mem_functor0(const sigc::bound_mem_functor0<void, HelloWorld>&)

```

If I replace &Indeksi::on_button_clicked with &HelloWorld::on_button_clicked, it works nicely. 

I only know that this probably something to do with pointers and sigc::mem_fun, but have no clue how to fix it. Help is truly appreciated!

---

### Post by Temppu on 2011-08-16
Solved. I had to pass the pointer to Indeksi. I was passing it to Helloworld, by using "this".

---

