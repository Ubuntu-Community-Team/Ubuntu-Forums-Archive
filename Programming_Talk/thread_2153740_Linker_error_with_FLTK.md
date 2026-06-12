---
title: "Linker error with FLTK"
date: 2013-06-12
forum: Programming Talk
---

### Post by invoices on 2013-06-12
Hello,
I'm having troubles using FLTK.

I found following in some fltk tutorial:

```

#include <FL/Fl.H>
#include <FL/Fl_Window.H>
#include <FL/Fl_Button.H>
using namespace std;

//--------------------------------------------
void but_cb( Fl_Widget* o, void*  ) {
   Fl_Button* b=(Fl_Button*)o;
   b->label("Good job"); //redraw not necessary
 
   b->resize(10,150,140,30); //redraw needed
   b->redraw();
}

//-------------------------------------------- 
int main() {

    Fl_Window win( 300,200,"Testing" );
    win.begin();
       Fl_Button but( 10, 150, 70, 30, "Click me" );
    win.end();
    but.callback( but_cb );
    win.show();
    return Fl::run();
}

```

If I try to run this we eclipse, I'm getting following error:

```
11:58:45 **** Incremental Build of configuration Debug for project fltk ****
make all 
Building target: fltk
Invoking: Cross G++ Linker
g++  -o "fltk"  ./src/fltk.o   
../src/fltk.cpp:9: error: undefined reference to 'Fl_Widget::label(char const*)'
../src/fltk.cpp:12: error: undefined reference to 'Fl_Widget::redraw()'
../src/fltk.cpp:18: error: undefined reference to 'Fl_Window::Fl_Window(int, int, char const*)'
../src/fltk.cpp:19: error: undefined reference to 'Fl_Group::begin()'
../src/fltk.cpp:20: error: undefined reference to 'Fl_Button::Fl_Button(int, int, int, int, char const*)'
../src/fltk.cpp:21: error: undefined reference to 'Fl_Group::end()'
../src/fltk.cpp:23: error: undefined reference to 'Fl_Window::show()'
../src/fltk.cpp:24: error: undefined reference to 'Fl::run()'
../src/fltk.cpp:24: error: undefined reference to 'Fl_Window::~Fl_Window()'
../src/fltk.cpp:24: error: undefined reference to 'Fl_Window::~Fl_Window()'
/usr/local/include/FL/Fl_Button.H:75: error: undefined reference to 'vtable for Fl_Button'
/usr/local/include/FL/Fl_Button.H:75: error: undefined reference to 'Fl_Widget::~Fl_Widget()'
collect2: ld gab 1 als Ende-Status zurück
make: *** [fltk] Fehler 1

11:58:45 Build Finished (took 115ms)


```

I'm facing the same problem in a different project that uses fltk with qtcreator. I'm using Ubuntu 12.04 64bit running on a i5 notebook (acer 4820tg).

Thank you

---

### Post by spjackson on 2013-06-12
Welcome to the forums.

> **invoices said:**
> 
```
11:58:45 **** Incremental Build of configuration Debug for project fltk ****
make all 
Building target: fltk
Invoking: Cross G++ Linker
g++  -o "fltk"  ./src/fltk.o   
../src/fltk.cpp:9: error: undefined reference to 'Fl_Widget::label(char const*)'
../src/fltk.cpp:12: error: undefined reference to 'Fl_Widget::redraw()'
../src/fltk.cpp:18: error: undefined reference to 'Fl_Window::Fl_Window(int, int, char const*)'
../src/fltk.cpp:19: error: undefined reference to 'Fl_Group::begin()'
../src/fltk.cpp:20: error: undefined reference to 'Fl_Button::Fl_Button(int, int, int, int, char const*)'
../src/fltk.cpp:21: error: undefined reference to 'Fl_Group::end()'
../src/fltk.cpp:23: error: undefined reference to 'Fl_Window::show()'
../src/fltk.cpp:24: error: undefined reference to 'Fl::run()'
../src/fltk.cpp:24: error: undefined reference to 'Fl_Window::~Fl_Window()'
../src/fltk.cpp:24: error: undefined reference to 'Fl_Window::~Fl_Window()'
/usr/local/include/FL/Fl_Button.H:75: error: undefined reference to 'vtable for Fl_Button'
/usr/local/include/FL/Fl_Button.H:75: error: undefined reference to 'Fl_Widget::~Fl_Widget()'
collect2: ld gab 1 als Ende-Status zurück
make: *** [fltk] Fehler 1

11:58:45 Build Finished (took 115ms)

```

The error message implies that you are not linking to a library that you need. The location of /usr/local/include/FL/Fl_Button.H suggests that the library may well be in /usr/local/lib. If the library is, say, /usr/local/lib/libfl.so then you would need:
```

g++  -o "fltk"  ./src/fltk.o  -L/usr/local/lib -lfl

```
I'm afraid I don't know what you need to do in eclipse (or qtcreator) to make it do that.

---

