---
title: "Unable to build-  Not recgonizing gtkmm libs?"
date: 2007-07-29
forum: Programming Talk
---

### Post by xl_cheese on 2007-07-29
I'm trying to compile the helloworld program featured here:

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

However the compilier cannot find gtkmm.h?

I have these installed:

    
  ```
    libsigc++ 2.0
      GTK+ 2.4
     cairomm
     pkg-config
     glib
     ATK
    Pango
     cairo
```

compiling using this:

```
g++ simple.cc -o simple `pkg-config gtkmm-2.4 --cflags --libs`

```

Help would be apprecitated.  Thanks.

---

### Post by Paul820 on 2007-07-29
You need 
> libgtkmm-2.4-dev
from synaptic

---

### Post by xl_cheese on 2007-07-29
> **Paul820 said:**
> You need 

from synaptic

DEV.  Thanks.  I had that one, but not dev.  Works now!  Time to brush off my programming skillz.

---

