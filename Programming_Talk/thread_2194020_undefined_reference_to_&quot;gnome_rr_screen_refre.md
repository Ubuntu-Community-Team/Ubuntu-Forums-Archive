---
title: "undefined reference to &quot;gnome_rr_screen_refresh(GnomeRRScreen*, _GError**)'"
date: 2013-12-15
forum: Programming Talk
---

### Post by holovati on 2013-12-15
Hi,

I am trying to write a small application in C++ using C::B, the code seems to compile successfully but something goes wrong in the linking stage and i can't figure out what.
 
```

#include <iostream>
#define GNOME_DESKTOP_USE_UNSTABLE_API
#include <gnome-desktop-3.0/libgnome-desktop/gnome-rr-config.h>
using namespace std;


int main()
{
    GnomeRRConfig *myconfig;
    GnomeRRScreen* myscreen;
    GError*        myerror;


   gboolean result = gnome_rr_screen_refresh(myscreen,NULL);






    return 0;
}

``` 

```

Build started on: _16-12-2013 at 05:17.16_
Build ended on: _16-12-2013 at 05:17.16_[COLOR=#000000][FONT=Times New Roman]**-------------- Build: Debug in Test (compiler: GNU GCC Compiler)---------------**
g++ -Wall -fexceptions -g -Iinclude -I/usr/include/glib-2.0/ -I/usr/include/gnome-desktop-3.0/ -I/usr/include/gtk-2.0 -I/usr/include/cairo/ -I/usr/include/pango-1.0/ -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include/ -I/usr/include/gdk-pixbuf-2.0/ -c /home/damir/Documents/Programming/Test/main.cpp -o obj/Debug/main.o
/home/damir/Documents/Programming/Test/main.cpp: In function ‘int main()’:
[COLOR=#0000ff]/home/damir/Documents/Programming/Test/main.cpp:8:20: warning: unused variable ‘myconfig’ [-Wunused-variable][/COLOR]
GnomeRRConfig *myconfig;
^
[COLOR=#0000ff]/home/damir/Documents/Programming/Test/main.cpp:10:20: warning: unused variable ‘myerror’ [-Wunused-variable][/COLOR]
GError* myerror;
^
[COLOR=#0000ff]/home/damir/Documents/Programming/Test/main.cpp:12:13: warning: unused variable ‘result’ [-Wunused-variable][/COLOR]
gboolean result = gnome_rr_screen_refresh(myscreen,NULL);
^
[COLOR=#0000ff]/home/damir/Documents/Programming/Test/main.cpp:12:59: warning: ‘myscreen’ is used uninitialized in this function [-Wuninitialized][/COLOR]
gboolean result = gnome_rr_screen_refresh(myscreen,NULL);
^
g++ -L/usr/lib/x86_64-linux-gnu/glib-2.0/include/ -L/usr/lib -L/usr/lib -o bin/Debug/Test obj/Debug/main.o /usr/lib/x86_64-linux-gnu/libglib-2.0.so /usr/lib/x86_64-linux-gnu/control-center-1/panels/libdisplay.so /usr/lib/libgnome-desktop-3.so /usr/lib/x86_64-linux-gnu/libglib-2.0.so /usr/lib/libgnome-desktop-3.so
obj/Debug/main.o: In function "main':
[COLOR=#ff0000]/home/damir/Documents/Programming/Test/main.cpp:12: undefined reference to "gnome_rr_screen_refresh(GnomeRRScreen*, _GError**)'[/COLOR]
collect2: error: ld returned 1 exit status
[COLOR=#a00000]Process terminated with status 1 (0 minute(s), 0 second(s))[/COLOR]
[COLOR=#a00000]1 error(s), 4 warning(s) (0 minute(s), 0 second(s))[/COLOR][/FONT][/COLOR]

```

By the looks of it, [COLOR=#000000][FONT=monospace]libgnome-desktop-3.so which contains "[/FONT][/COLOR]000000000001aa30 T gnome_rr_screen_refresh"[COLOR=#000000][FONT=monospace] is being linked with main.o.[/FONT]

[FONT=monospace]Any suggestions on how to resolve this problem are greatly appreciated. [/FONT][/COLOR]:neutral:

---

### Post by Bachstelze on 2013-12-16
Libraries are normally linked with the [font=monospace]-l[/font] flag, not by typing their full filename.

---

### Post by holovati on 2013-12-16
I tried linking with 
> g++ -L/usr/lib/x86_64-linux-gnu/glib-2.0/include/ -L/usr/lib -L/usr/lib -o bin/Debug/Test obj/Debug/main.o -lgnome-desktop-3



and I still get the same error. It seems like the linker finds the library but can't find the method inside it? :(

---

### Post by spjackson on 2013-12-17
I apologise in advance if these observations are incorrect or unhelpful, but I don't have time to check at the moment, and there is a chance that they might help.
> 
By the looks of it, libgnome-desktop-3.so which contains "000000000001aa30 T gnome_rr_screen_refresh" is being linked with main.o.

That looks like a C function to me.
> /home/damir/Documents/Programming/Test/main.cpp:12: undefined reference to "gnome_rr_screen_refresh(GnomeRRScreen*, _GError**)'

That looks like a C++ function, i.e. the argument types are part of the linkage. If you run nm on main.o you might be able to confirm this. If that's the case then it suggests that you are missing an "extern C" when the function is declared... but if you are including the proper headers, I don't know why that would happen.

Another thing that surprises me, but probably has nothing to do with your problem is this.
> -I/usr/include/gtk-2.0
Now I thought Gnome3 used gtk3, so why gtk-2.0?

---

### Post by speiedy on 2013-12-17
> **holovati said:**
> [COLOR=#000000][FONT=monospace]Any suggestions on how to resolve this problem are greatly appreciated. [/FONT][/COLOR]:neutral:

Include the header file gnome-rr.h

---

