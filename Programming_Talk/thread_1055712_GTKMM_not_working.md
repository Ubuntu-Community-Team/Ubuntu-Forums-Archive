---
title: "GTKMM not working"
date: 2009-01-31
forum: Programming Talk
---

### Post by wenren on 2009-01-31
I've been trying to get gtkmm to work. It seems that all of the #include files are in place, and an application is ready to be created. So, before, I got into any useful project with gtk, I decided to first try out the most basic tutorial: the creation of a single window. On a gtkmm tutorial, I found the following code:

```

#include <gtkmm.h>

int main(int argc, char *argv[])
{
    Gtk::Main kit(argc, argv);
    Gtk::Window window;
    Gtk::Main::run(window);
    return 0;
}
```

When built, the following errors are returned:
```

Compiling: /home/sven/c++/gtkmm_test.cpp
Linking console executable: /home/sven/c++/gtkmm_test
/home/sven/c++/gtkmm_test.o: In function `__static_initialization_and_destruction_0(int, int)':
gtkmm_test.cpp:(.text+0x2d): undefined reference to `Glib::ustring::ustring(char const*)'
gtkmm_test.cpp:(.text+0x32): undefined reference to `Glib::ustring::~ustring()'
gtkmm_test.cpp:(.text+0x5e): undefined reference to `Glib::ustring::ustring(char const*)'
gtkmm_test.cpp:(.text+0x63): undefined reference to `Glib::ustring::~ustring()'
gtkmm_test.cpp:(.text+0x8f): undefined reference to `Glib::ustring::ustring(char const*)'
gtkmm_test.cpp:(.text+0x94): undefined reference to `Glib::ustring::~ustring()'
gtkmm_test.cpp:(.text+0xc0): undefined reference to `Glib::ustring::ustring(char const*)'
gtkmm_test.cpp:(.text+0xc5): undefined reference to `Glib::ustring::~ustring()'
gtkmm_test.cpp:(.text+0xf1): undefined reference to `Glib::ustring::ustring(char const*)'
gtkmm_test.cpp:(.text+0xf6): undefined reference to `Glib::ustring::~ustring()'
gtkmm_test.cpp:(.text+0x122): undefined reference to `Glib::ustring::ustring(char const*)'
gtkmm_test.cpp:(.text+0x127): undefined reference to `Glib::ustring::~ustring()'
gtkmm_test.cpp:(.text+0x153): undefined reference to `Glib::ustring::ustring(char const*)'
gtkmm_test.cpp:(.text+0x158): undefined reference to `Glib::ustring::~ustring()'
/home/sven/c++/gtkmm_test.o: In function `main':
gtkmm_test.cpp:(.text+0x1bf): undefined reference to `Gtk::Main::Main(int&, char**&, bool)'
gtkmm_test.cpp:(.text+0x1d2): undefined reference to `Gtk::Window::Window(Gtk::WindowType)'
gtkmm_test.cpp:(.text+0x1dd): undefined reference to `Gtk::Main::run(Gtk::Window&)'
gtkmm_test.cpp:(.text+0x1ef): undefined reference to `Gtk::Window::~Window()'
gtkmm_test.cpp:(.text+0x208): undefined reference to `Gtk::Window::~Window()'
gtkmm_test.cpp:(.text+0x21b): undefined reference to `Gtk::Main::~Main()'
gtkmm_test.cpp:(.text+0x240): undefined reference to `Gtk::Main::~Main()'
collect2: ld returned 1 exit status
Process terminated with status 1 (0 minutes, 6 seconds)
21 errors, 0 warnings
```

I'm confused as to why the functions remain undefined. Can anyone help me?

---

### Post by JupiterV2 on 2009-01-31
Please include the command you used to compile the code, most especially, let us know what flags you passed to the compiler/linker.

Basically, an undefined reference error tells you that a reference (a function you've called within' your code for example) exists (read: has a prototype) but has no implementation. Therefore, the likely cause is a missing library. In this case, did you use the pkg-config flags to link the necessary libraries and flags with pkg-config's '--cflags' and '--libs'?

You should be able to find how to do it in the docs.

---

### Post by wenren on 2009-01-31
I'm a bit confused. I was only using the standard commands, either the code blocks ide or:
```
g++ gtkmm_test.cpp
```

---

### Post by wenren on 2009-01-31
Alright. So, I checked the gtkmm docs, and did everything it said. This then sent me in a different direction. Here's the new output I get:
```
sven@sven-laptop:~/c++$ g++ gtkmm_test.cpp -o gtkmm_test `pkg-config gtkmm-2.4 --cflags --libs`
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libpangomm-1.4.so: undefined reference to `pango_cairo_font_map_set_default'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libpangomm-1.4.so: undefined reference to `pango_language_get_scripts'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libpangomm-1.4.so: undefined reference to `pango_layout_get_baseline'
collect2: ld returned 1 exit status
sven@sven-laptop:~/c++$ 

```

So...how do I fix this problem?
I'm fairly certain I followed every instruction listed here:
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-basics.html]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-basics.html")

---

### Post by SledgeHammer_999 on 2009-01-31
have you installed the right dev packages for gtkmm? usually gtkmm-dev

---

### Post by MeduZa on 2009-01-31
you can use anjuta to made your projects, maybe you have missing the dev package or forgot to link the libraries.
Anjuta made all of that for you

PD: try this :  -lglademm-2.4 -lgtkmm-2.4 -lglade-2.0 -lgdkmm-2.4 -lglibmm-2.4

---

### Post by bruce89 on 2009-01-31
> **SledgeHammer_999 said:**
> have you installed the right dev packages for gtkmm? usually gtkmm-dev

Actually, it's libgtkmm-2.4-dev.

---

