---
title: "Glade And C++"
date: 2011-06-05
forum: Packaging and Compiling Programs
---

### Post by scott-ian on 2011-06-05
[LEFT]How can I use Glade files in C++?  I already have included the GTK and Glade headers.
[/LEFT]

---

### Post by scott-ian on 2011-06-06
Could any one help?

---

### Post by SevenMachines on 2011-06-07
Have a look at [http://developer.gnome.org/gtkmm-tutorial/2.24/chapter-builder.html.en](http://developer.gnome.org/gtkmm-tutorial/2.24/chapter-builder.html.en) should explain everything pretty quickly

---

### Post by scott-ian on 2011-06-07
Thanks.

---

### Post by scott-ian on 2011-06-07
It doesn't work.  The error message I get is:
[B]g++ `pkg-config --cflags --libs gtk+-2.0 libglade-2.0` -Wall -o "main" "main.cxx" (in directory: /home/ian/Documents/Programming/quick-deb/code)
main.cxx: In function 'int main(int, char**)':
main.cxx:30:5: error: 'Glib' has not been declared
main.cxx:30:18: error: 'Gtk' has not been declared
main.cxx:30:32: error: 'builder' was not declared in this scope
main.cxx:30:42: error: 'Gtk' has not been declared
Compilation failed.

[/B]I think I must be missing an include:
[B]#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <gtk/gtk.h>
#include <gdk/gdkx.h>
#include <glade/glade.h>[/B]
Also, which of these are only needed in command lines?

---

### Post by scott-ian on 2011-06-07
I got it to compile:
[B]//#include <stdio.h>
//#include <stdlib.h>
#include <string.h>
//#include <gtk/gtk.h>
//#include <gdk/gdkx.h>
//#include <glade/glade.h>
#include <libglademm.h>
#include <gtkmm.h>[/B]

But when the program is run, I receive this error message:
[B](process:21740): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `quark > 0' failed

(process:21740): glibmm-WARNING **: Glib::Error::throw_exception():
  unknown error domain 'gtk-builder-error-quark': throwing generic Glib::Error exception

terminate called after throwing an instance of 'Glib::Error'
Aborted[/B]

What went wrong?

---

### Post by scott-ian on 2011-06-08
Will someone please help?  The error doesn't make sense to me.

---

### Post by SevenMachines on 2011-06-08
You would need to post some code to know. Theres often a few instance types of Glib::error thrown on problems setting up the builder, loading the file, that sort of thing. Can't tell which one without code. Attached is a simple example from the docs as a guide, it should compile and run fine with 
```
 $ g++ -o main main.cc `pkg-config --cflags --libs gtkmm-2.4`
```

---

### Post by SevenMachines on 2011-06-08
Just a general recap checklist for using gtkmm
1. Initialise builder main 'kit' ( Gtk::Main kit(argc, argv) )
2. Create builder from file 
3. Get widget references from builder 
4. Connect widget signals to actual methods
These are the pretty much all you need to know how to do to use builder files with gtkmm, the previous attached doc example covers them all pretty well, signal connecting is always the bit i forget :)

---

### Post by scott-ian on 2011-06-08
Well, here is the exact code:
```
//      main.cxx
//      
//      Copyright 2011 Ian Scott <ian@ian-pc>
//      
//      This program is free software; you can redistribute it and/or modify
//      it under the terms of the GNU General Public License as published by
//      the Free Software Foundation; either version 2 of the License, or
//      (at your option) any later version.
//      
//      This program is distributed in the hope that it will be useful,
//      but WITHOUT ANY WARRANTY; without even the implied warranty of
//      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
//      GNU General Public License for more details.
//      
//      You should have received a copy of the GNU General Public License
//      along with this program; if not, write to the Free Software
//      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
//      MA 02110-1301, USA.


//#include <stdio.h>
//#include <stdlib.h>
#include <string.h>
//#include <gtk/gtk.h>
//#include <gdk/gdkx.h>
//#include <glade/glade.h>
#include <libglademm.h>
#include <gtkmm.h>

int main(int argc, char **argv)
{
    g_type_init();
    Glib::RefPtr<Gtk::Builder> builder = Gtk::Builder::create_from_file("ui/main.glade");
    return 0;
}


```

I compile and build with this command:
```
g++ `pkg-config --cflags --libs gtk+-2.0 libglade-2.0 libglademm-2.4 gtkmm-2.4` -Wall -o "%e" "%f"
```
(Note that it includes libraries I do not need)

It compiles and builds, but running the program results in the error code I posted earlier.

---

### Post by SevenMachines on 2011-06-08
I'd say, 
* Dont include libglademm, its deprecated and you dont need/want it
* Let gtkmm sort out its compile includes on the command line, no need to add them by hand so 'pkg-config --cflags --libs gtkmm-2.4' only will be fine
* You need to initialise gtk before use, so your code would be
```
int main(int argc, char **argv) {
 Gtk::Main kit(argc, argv);     
Glib::RefPtr<Gtk::Builder> builder = Gtk::Builder::create_from_file("ui/main.glade");     return 0; 
}
```Gtk::Main intialisation deals with gtk_type_init itself so you dont need that deperately

Obviously to actually see anything you'd need to get a main window reference and call kit.run(*widget_ref) on it as shown in the example.

[EDIT] The example also shows how to catch the Builder errors on loading from file which i'd say is probably good practice, the program would probably not be saved and should exit anyway but you could generate clearer debug output by catching the errors

---

### Post by scott-ian on 2011-06-08
I get the following error:
**(main:13316): gtkmm-CRITICAL **: gtkmm: widget `Main' (in GtkBuilder file) is of type `gtkmm__GtkWindow' but `GtkDialog' was expected**

How should I change the code to use gtkmm__GtkWindow?  I used the code in the example, but may change it once it works.

---

### Post by SevenMachines on 2011-06-08
Declare a pointer of the widget type you want to get a reference to, the example uses ```
Gtk::Dialog * pDialog;
```a main window would be
```
 Gtk::Window * pMyWindow;
```A button
```
 Gtk::Button * psomeButton;
```and so on. Actually getting the reference is the same in all cases...
  refBuilder->get_widget("Name of widget in glade", pointerThatWeDeclared);
So,
```
 refBuilder->get_widget("DialogBasic", pDialog);
```If you called your main window MyMainWindow in glade designer then using the pointer example above...
```
   refBuilder->get_widget("MyMainWindow", pWindow);
```

---

### Post by scott-ian on 2011-06-08
It worked, thanks.

---

