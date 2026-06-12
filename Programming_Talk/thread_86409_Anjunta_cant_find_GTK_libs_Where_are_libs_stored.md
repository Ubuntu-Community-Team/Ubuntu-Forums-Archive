---
title: "Anjunta cant find GTK libs? Where are libs stored?"
date: 2005-11-05
forum: Programming Talk
---

### Post by mitchy_g on 2005-11-05
Hi!
Im new to ubuntu and still getting used to the filesystem. I have installed Anjuta, g++, build essentials and the GTK libs, and I am trying to compile the traditional bit of code for gui beginners:

(note: im using g++)

```
#include <gtk/gtk.h>

int main( int   argc,
          char *argv[] )
{
    GtkWidget *window;
    
    gtk_init (&argc, &argv);
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show  (window);
    
    gtk_main ();
    
    return 0;
}
```


The error is:
```
....gtk/gtk.h No Such File or Directory
``` 

My simple question is how can i fix this error in Anjuta? When i create the project I am selecting the GTK2.0 project template.

Secondly where are all the libs stored on a normal ubuntu machine that are used when compiling a peice of code?

Thanks
Mitch :)

---

### Post by Fluffy, the jolly sheep on 2005-11-05
In Ubuntu, the header files which you have to include are seperated from the (binary) libraries, because non-programmers don't have a need for them. The packages with the header files all have a '-dev' suffix. You can easily install all necessary -dev packages to develop for gnome by installing the gnome-core-devel meta-package.
The header files can be found somewhere in a subdirectory of /usr, but the compiler will find them automatically (you shouldn't use the absolute path).

Greets,

Fluffy

---

### Post by mitchy_g on 2005-11-05
Hi,
I have installed the gnome-core-devel package and have found the gtk.h file which I am trying to use, however I am still getting the same compiler issue. Do I need to set a path to this file in the compiler options?

Thanks
Mitch

---

### Post by Fluffy, the jolly sheep on 2005-11-05
Hi Mitch,

make sure you compile with the 'Compile with Make' command instead of the 'Compile' command.  The latter doesn't use the GNU autotools. When creating the project, Anjuta automatically generates some files which the autotools use to find the gtk+-library, so not using make will fail. Using the build command will also do the trick, it generates the executable right away.
You might also have to configure the project again (build menu -> configure) after installing the -dev packages.

btw, if you want to program a gtk application in C++ (and not in a C/C++ mixture) you might want to consider using the gtk C++ bindings. You'll need to install the libgtk2mm-2.4-dev package for that purpose.

good luck,
Fluffy

---

### Post by mitchy_g on 2005-11-05
Fluffy,
Yep! "Compile with make" works!

I re-configured the project when I installed the extra packages and all is well.

Thanks Mate

---

