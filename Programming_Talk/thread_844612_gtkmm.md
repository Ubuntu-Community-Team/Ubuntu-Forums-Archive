---
title: "gtkmm"
date: 2008-06-29
forum: Programming Talk
---

### Post by chris200x9 on 2008-06-29
Hi I'm new to gtkmm and am following the tutorial here: [http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-basics.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-basics.html) but when I input ```
 #include <gtkmm.h>
Gtk::Main kit(argc, argv);
Gtk::Window window;
Gtk::Main::run(window);

``` like it shows me I get this error: ```
 simple.cc:2: error: 'argc' was not declared in this scope
simple.cc:2: error: 'argv' was not declared in this scope
simple.cc:4: error: expected constructor, destructor, or type conversion before '(' token

```

---

### Post by WW on 2008-06-29
What you have shown is not the complete example.  In the tutorial, click on the "Source Code" link.  You'll see a list of files.  One of them is base.cc:

**base.cc**
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

---

### Post by chris200x9 on 2008-06-29
oops, sorry, thank you.

---

