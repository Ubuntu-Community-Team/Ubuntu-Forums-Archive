---
title: "GTK+ with G++"
date: 2009-02-23
forum: Programming Talk
---

### Post by Java Geek on 2009-02-23
Hello, I am running into a very persistant error. I use the G++ compiler in NEtbeans IDE. The error code is like so...
```
g++    -c -g -o build/Debug/GNU-Linux-x86/Main.o Main.cpp
Main.cpp:8:21: error: gtk/gtk.h: No such file or directory
```

Following is my simple program code. Is there a way to include the header file into the claspath?
```

/* 
 * File:   Main.cpp
 * Author: stephen
 *
 * Created on February 23, 2009, 5:01 PM
 */

#include <gtk/gtk.h>

/*
 * 
 */
int main(int argc, char** argv) {
    
    GtkWidget *window;
    
    gtk_init (&argc, &argv);
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show (window);
    
    gtk_main ();
    
    return 0;
}

```
Thanks all!

---

### Post by cabalas on 2009-02-23
You need to tell the compiler where to find the include files for gtk. Try compiling it with this command:

```
g++ -c -g -o build/Debug/GNU-Linux-x86/Main.o Main.cpp `pkg-config --cflags gtk+-2.0`

```

---

### Post by SledgeHammer_999 on 2009-02-23
Don't forget the libs for the linking:
```
g++ -c -g -o build/Debug/GNU-Linux-x86/Main.o Main.cpp `pkg-config --cflags --libs gtk+-2.0`
```

---

### Post by cl333r on 2009-02-23
I also add the include directories to ProjectName->right-click->Properties->C Compiler->Include Directories
which should contain entries like /usr/include/libgtk..
Otherwise the "suggestions & autocomplete" will not work (or might not even compile, can't remember).
I use Gtkmm, so here's a screenshot for my type of project.

---

