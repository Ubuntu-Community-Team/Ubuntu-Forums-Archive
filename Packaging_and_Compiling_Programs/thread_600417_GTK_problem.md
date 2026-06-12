---
title: "GTK problem"
date: 2007-11-02
forum: Packaging and Compiling Programs
---

### Post by ondrisko on 2007-11-02
Hello, I would appreciate very much some help with GTK. 

I'd like to develop using GTK libraries, so I've installed package libgtk2.0-dev. I already solved problem with #include<gtk/gtk.h> which was not found at first, I added additional include directories to gcc. 

Compilation works now ok, but there are linker errors like 'undefined reference to `gtk_init''. I cannot make him to find the libraries he wants and I dont know where to look for them.

 Can anybody help please?

---

### Post by mlind on 2007-11-02
gtk_init() is from gtk.h.
[http://library.gnome.org/devel/gtk/unstable/gtk-General.html#gtk-init](http://library.gnome.org/devel/gtk/unstable/gtk-General.html#gtk-init)

Are you calling the function correctly?


This should work for you, compile using *gcc `pkg-config --cflags --libs gtk+-2.0`* foo.c
```

#include <gtk/gtk.h>

int
main (int argc, char **argv)
{
  **gtk_init (&argc, &argv);**
  GtkWidget *win = gtk_window_new (GTK_WINDOW_TOPLEVEL);
  gtk_widget_show_all (win);
  gtk_main ();
  return 0;
}

```

---

### Post by tony.morse on 2009-09-03
I'm having similar problems.  I can get my code to compile ok using gcc as you said, but I have to use cmake for other reasons.

So I found FindGTK2.cmake [here]("http://cmake-modules.googlecode.com/svn/trunk/Modules/GTK2/FindGTK2.cmake")

put that in the correct place and modify my CMakeLists.txt to include the following lines...
    ```
FIND_PACKAGE(GTK2 COMPONENTS gtk)
    include_directories (${GTK2_INCLUDE_DIRS})
    TARGET_LINK_LIBRARIES(foo ${GTK2_LIBRARY_DIRS})

```
Now I can compile with cmake, programs with the following includes...
```
#include <cairo.h>
#include <gtk/gtk.h>
```

However, while it has no problem with the includes any more and commands such as GtkWidget *window; are fine, I get a huge list of undefined references when I make my program...
```
CMakeFiles/ch.dir/main.o: In function `clicked(_GtkWidget*, _GdkEventButton*, void*)':
main.cpp:(.text+0x3ee): undefined reference to `gtk_widget_queue_draw'
main.cpp:(.text+0x404): undefined reference to `gtk_widget_queue_draw'
CMakeFiles/ch.dir/main.o: In function `on_expose_event(_GtkWidget*, _GdkEventExpose*, void*)':
main.cpp:(.text+0x420): undefined reference to `gdk_cairo_create'
main.cpp:(.text+0x440): undefined reference to `cairo_set_source_rgb'
main.cpp:(.text+0x455): undefined reference to `cairo_set_line_width'
main.cpp:(.text+0x4c3): undefined reference to `cairo_move_to'
main.cpp:(.text+0x4f2): undefined reference to `cairo_line_to'
main.cpp:(.text+0x52a): undefined reference to `cairo_move_to'
main.cpp:(.text+0x559): undefined reference to `cairo_line_to'
main.cpp:(.text+0x576): undefined reference to `cairo_stroke'
main.cpp:(.text+0x581): undefined reference to `cairo_destroy'
CMakeFiles/ch.dir/main.o: In function `main':
main.cpp:(.text+0x1fb6): undefined reference to `gtk_init'
main.cpp:(.text+0x1fc2): undefined reference to `gtk_window_new'
main.cpp:(.text+0x1fd8): undefined reference to `gtk_widget_add_events'
main.cpp:(.text+0x200c): undefined reference to `g_signal_connect_data'
main.cpp:(.text+0x202c): undefined reference to `gtk_main_quit'
main.cpp:(.text+0x203f): undefined reference to `g_signal_connect_data'
main.cpp:(.text+0x2073): undefined reference to `g_signal_connect_data'
main.cpp:(.text+0x2078): undefined reference to `gtk_window_get_type'
main.cpp:(.text+0x2087): undefined reference to `g_type_check_instance_cast'
main.cpp:(.text+0x2097): undefined reference to `gtk_window_set_position'
main.cpp:(.text+0x209c): undefined reference to `gtk_window_get_type'
main.cpp:(.text+0x20ab): undefined reference to `g_type_check_instance_cast'
main.cpp:(.text+0x20bb): undefined reference to `gtk_window_set_title'
main.cpp:(.text+0x20c0): undefined reference to `gtk_window_get_type'
main.cpp:(.text+0x20cf): undefined reference to `g_type_check_instance_cast'
main.cpp:(.text+0x20e7): undefined reference to `gtk_window_set_default_size'
main.cpp:(.text+0x20fa): undefined reference to `gtk_widget_set_app_paintable'
main.cpp:(.text+0x2105): undefined reference to `gtk_widget_show_all'
main.cpp:(.text+0x210a): undefined reference to `gtk_main'
```


So err what now??

---

### Post by tony.morse on 2009-09-03
Ok solved that, I needed the following line in my cmakelists.txt file...
    ```
LINK_LIBRARIES(${MyProject} ${GTK2_LIBRARIES} )
```

---

### Post by tony.morse on 2009-09-08
P.S. the correct location for FindGTK2.cmake  (at least on my machine) is...
/usr/share/cmake-2.6/Modules

---

### Post by cyqotiq on 2010-01-26
This thread is pretty old, but it was never resolved.  I have a similar issue, and would like to try to find the cause.

I'm a seasoned Visual Studio (C#/VB.Net) programmer whose major interaction with C/C++ has traditionally been maintenance and minor script-like programs that required 1 source file.  I have been running Linux as my primary operating system for several months after trying for almost 8 years.  Now that I've finally been able to get completely moved over to Ubuntu, I would like to start programming in C/C++ more and learning the ins and outs of GTK+.

After creating a project in Code::Blocks, it created the main.c file with the helloWorld function and two references: #include <stdlib.h> and #include <gtk/gtk.h>.  At first, it complained that it couldn't gtk.h, so after a little research, I added -I /usr/include/gtk-2.0 (and then subsequently a long list of other directories under /usr/include) to the project's compile options.

Now that I've gotten all of the appropriate directories included using the -I argument, it's no longer complaining about missing header files.  But it is complaining about references to undefined functions.

It appears that the header files are being included now, but the compiler/linker isn't actually loading the libraries, so calls to GTK+ functions aren't working.  I've added the compiler switch mentioned at the top of this thread (`pkg-config --cflags --libs gtk+-2.0`), but this doesn't seem to help at all.

Does anyone have any idea what might be going wrong?  Any help would be appreciated?

(Sorry to hijack this thread.  I didn't think it was necessary to create a new post, since this thread seems to cover my exact problem, and has yet to be resolved.)

---

### Post by cyqotiq on 2010-01-26
I'm not certain that this qualifies as a solution, but I did find a work-around.  Monodevelop supports creating non-CLR programs using C and C++.  Once one of these types of solutions has been created, references to system packages may be added and this seems to work OOTB without having to specify special include paths.

I hadn't planned on using Monodevelop for this, but since it's working and it's similar enough to Visual Studio, I can't say that I have any reason to complain.

---

### Post by wkbittner on 2010-06-22
> **cyqotiq said:**
> 
It appears that the header files are being included now, but the compiler/linker isn't actually loading the libraries, so calls to GTK+ functions aren't working.  I've added the compiler switch mentioned at the top of this thread (`pkg-config --cflags --libs gtk+-2.0`), but this doesn't seem to help at all.

Does anyone have any idea what might be going wrong?  Any help would be appreciated?
)
Sure, can you please post your output from the command pkg-config --cflags --libs gtk+-2.0
Doing the following works fine for me, just wanted to double check this is what your doing:
gcc `pkg-config --cflags --libs gtk+-2.0` main.c

main.c has a line in it of:
dialog = gtk_message_dialog_new (GTK_WINDOW (win), GTK_DIALOG_MODAL, GTK_MESSAGE_INFO, GTK_BUTTONS_CLOSE, "Hello World!");

and seems to compile fine for me.

Cheers!

---

### Post by Kai Zhou on 2012-06-11
[B]For example, if you're compiling a source file named hello.c. 
Then compile it like this:

abc@ubuntug:~/Documents$ gcc hello.c [/B] \  **                       `pkg-config --cflags gtk+-2.0` -o hello **\  [B]                       `pkg-config --libs gtk+-2.0`

Have a try:p
[/B]

---

