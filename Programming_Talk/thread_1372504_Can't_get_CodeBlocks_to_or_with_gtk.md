---
title: "Can't get CodeBlocks to or with gtk"
date: 2010-01-04
forum: Programming Talk
---

### Post by TheHimself on 2010-01-04
I've written a C program for gtk. When I compile it from command line using gcc with option `pkg-config --cflags --libs gtk+-2.0` it's compiled fine. However when I want to compile it in CodeBlocks with the same compiler and options, I get NO errors like " Can't find #include <gtk/gtk.h> " but still gtk functions, etc. are not recognized and so I get errors! What's happening?

---

### Post by TheHimself on 2010-01-04
Sorry the title should be to "work" with.

---

### Post by TheHimself on 2010-01-05
Problem is caused by the linker but I still don't know how to resolve it.

---

### Post by mutex023 on 2010-01-05
You must specify the library to link to in codeblocks.
Project > Build options > Linker settings
Click on add, and browse for the gtk library in /usr/lib .
I've never compiled any gtk app, but to my knowledge most libraries are present in /usr/lib. Usually the file name is libxxx.a or libxx.so

---

### Post by TheHimself on 2010-01-05
Yes. But there are so many of them. The option `pkg-config --cflags --libs gtk+-2.0` when you compile from command line, produces the names/paths of the libraries to include. But even when I add the output of the command

```
pkg-config --cflags --libs gtk+-2.0
``` 

in compiler's options in CodeBlocks, it doesn't work. Is linker a separate application than the compiler?

---

### Post by akashiraffee on 2010-01-05
I haven't used Code Blocks (can't stand IDE's) but I would guess that all of the "-l" (small L) and "-I" (capital i) gcc switches here need to be set under the "Linker" menu option that mutex023 refers to. 

For gtk, as I think you know:
**-I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0**

---

### Post by WitchCraft on 2010-01-05
> **TheHimself said:**
> 
in compiler's options in CodeBlocks, it doesn't work. Is linker a separate application than the compiler?

Yes. Unless the linker has been embedded in the compiler executable.

Codeblocks has a tab for compiler and one for linker.

If you added the switches only to the compiler, then maybe you have to add them to the linker as well.

---

### Post by mutex023 on 2010-01-05
Codeblocks provides the ability to create a gtk+ project.
Did you try that?
May be that will take care of automatically linking to the required 
libraries.

---

### Post by TheHimself on 2010-01-06
Thank you guys. When I start a "gtk project", because of the way I've arranged my files, I get errors. I did what akashiraffee suggested and the program was compiled fine but now the Debugger doesn't work (and debugging was what I wanted from CodeBlocks).


> **akashiraffee said:**
> I haven't used Code Blocks (can't stand IDE's) 

What do you use then? I've recently come back to programming after ages. In old times I used Borland C. Now I've been using gedit with command line compiling but I want to be able to debug my program. So far I've been putting printf commands at suspicious points to see what's going on but that gets cumbersome.   



Now that I've caught your attention let me ask a related question (but not related to the subject of this thread). It's about C-C++ compatibility. My program is in C and uses gtk. I want to use C++ but what I want out of C++ is string operations, it's library and maybe the boost libraries. I don't have the time to re-learn the C++ methodology right now and so don't want to use gtkmm. My program compiles fine  with g++ but when I run it, gtk can't find the handler functions that I've written. I guess this is related to linking but don't now how to solve it.

---

