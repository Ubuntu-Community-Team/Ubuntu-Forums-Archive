---
title: "[ C++ ] Gtk on Windows shows both, console and Gtk window."
date: 2009-10-27
forum: Programming Talk
---

### Post by OpenGuard on 2009-10-27
How do I get rid of the console window ?

```
#include <gtkmm.h>

using namespace Gtk;

int main(int argc, char *argv[])
{
    Main kit(argc, argv);
    Window window;
    Main::run(window);
    
    return 0;
}

```[[IMG]http://img12.imageshack.us/img12/5085/gtkconsole.th.png[/IMG]]("http://img12.imageshack.us/i/gtkconsole.png/")

---

