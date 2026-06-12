---
title: "Compile FLTK-program"
date: 2006-05-15
forum: Programming Talk
---

### Post by mucha on 2006-05-15
I've tried to compile my first fltk-application but I can't. I get these compileerrors: 
```
simon@mucha:~$ gcc -I /usr/include/ -L /usr/lib -o test test.cpp
/tmp/ccOvfLQb.o: In function `main':test.cpp:(.text+0x25): undefined reference to `operator new(unsigned int)'
:test.cpp:(.text+0x4b): undefined reference to `Fl_Window::Fl_Window(int, int, char const*)'
:test.cpp:(.text+0x5d): undefined reference to `operator new(unsigned int)'
:test.cpp:(.text+0xa6): undefined reference to `operator delete(void*)'
:test.cpp:(.text+0xf8): undefined reference to `fl_define_FL_SHADOW_LABEL()'
:test.cpp:(.text+0x112): undefined reference to `Fl_Group::end()'
:test.cpp:(.text+0x12b): undefined reference to `Fl_Window::show(int, char**)'
:test.cpp:(.text+0x130): undefined reference to `Fl::run()'
:test.cpp:(.text+0x146): undefined reference to `operator delete(void*)'
/tmp/ccOvfLQb.o: In function `Fl_Box::Fl_Box(int, int, int, int, char const*)':test.cpp:(.gnu.linkonce.t._ZN6Fl_BoxC1EiiiiPKc[Fl_Box::Fl_Box(int, int, int, int, char const*)]+0x30): undefined reference to `Fl_Widget::Fl_Widget(int, int, int, int, char const*)'
:test.cpp:(.gnu.linkonce.t._ZN6Fl_BoxC1EiiiiPKc[Fl_Box::Fl_Box(int, int, int, int, char const*)]+0x35): undefined reference to `vtable for Fl_Box'
/tmp/ccOvfLQb.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```

test.cpp
```
#include <FL/Fl.H>
#include <FL/Fl_Window.H>
#include <FL/Fl_Box.H>

int main(int argc, char **argv) {
  Fl_Window *window = new Fl_Window(300,180);
  Fl_Box *box = new Fl_Box(20,40,260,100,"Hello, World!");
  box->box(FL_UP_BOX);
  box->labelsize(36);
  box->labelfont(FL_BOLD+FL_ITALIC);
  box->labeltype(FL_SHADOW_LABEL);
  window->end();
  window->show(argc, argv);
  return Fl::run();
}
```

I installed libfltk1.1-dev from apt for this.

---

### Post by llonesmiz on 2006-05-15
I think you should compile the program with g++ since the code is in C++.

---

### Post by mucha on 2006-05-15
Okey, but then I get these errors:

```
simon@mucha:~$ g++ -I /usr/include/ -L /usr/lib -o test test.cpp
/tmp/ccIDzds6.o: In function `main':test.cpp:(.text+0x4b): undefined reference to `Fl_Window::Fl_Window(int, int, char const*)'
:test.cpp:(.text+0xf8): undefined reference to `fl_define_FL_SHADOW_LABEL()'
:test.cpp:(.text+0x112): undefined reference to `Fl_Group::end()'
:test.cpp:(.text+0x12b): undefined reference to `Fl_Window::show(int, char**)'
:test.cpp:(.text+0x130): undefined reference to `Fl::run()'
/tmp/ccIDzds6.o: In function `Fl_Box::Fl_Box(int, int, int, int, char const*)':test.cpp:(.gnu.linkonce.t._ZN6Fl_BoxC1EiiiiPKc[Fl_Box::Fl_Box(int, int, int, int, char const*)]+0x30): undefined reference to `Fl_Widget::Fl_Widget(int, int, int, int, char const*)'
:test.cpp:(.gnu.linkonce.t._ZN6Fl_BoxC1EiiiiPKc[Fl_Box::Fl_Box(int, int, int, int, char const*)]+0x35): undefined reference to `vtable for Fl_Box'
collect2: ld returned 1 exit status
```


EDIT: Found how to do:
```
fltk-config --compile test.cpp
```

or

```
g++ $(fltk-config --cxxflags) -lfltk -o test test.cpp
```

---

### Post by LastStarfighter on 2012-12-02
Thank you for replying to your own question with the solution. I wish everyone would do that. Very helpful!

---

