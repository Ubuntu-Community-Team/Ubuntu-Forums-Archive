---
title: "[gtkmm]set_resizable doesn't work as expected"
date: 2008-03-09
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-03-09
Hi I am trying to figure out how gtkmm works. So I am just "extending" the functionality of the hello program found in the gtkmm tutorial:
```
int main(int argc, char *argv[])
{
    Gtk::Main kit(argc, argv);

    Gtk::Window window;

    Gtk::Main::run(window);
    
    return 0;
}
```


I was trying to find a way to make my window unresizable from the user. So according to the documentation the "set_resizable()" does the job. But when I try it the resulting window is **really really small** maybe 1x1 pixel. I tried using "resize()" but nothing changes.So here's the code:
```
#include <gtkmm.h>

int main(int argc, char *argv[])
{
    Gtk::Main kit(argc, argv);
    Gtk::Window window;
    window.set_resizable(false);
    window.resize(256,256);
    Gtk::Main::run(window);
    
    return 0;
}
```

---

### Post by SledgeHammer_999 on 2008-03-09
Solved. All I needed to do is add() to the window a **container** widget.

EDIT: **I am sorry, I solved it some other way.** I used window.set_size_request() instead of window.resize().

---

