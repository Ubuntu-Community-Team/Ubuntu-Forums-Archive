---
title: "How to use GTK?"
date: 2014-10-12
forum: Programming Talk
---

### Post by goghvv on 2014-10-12
Hi. 
I'm trying to install GTK for using with C, but I'm having some difficulties...

After reading [this thread]("http://ubuntuforums.org/showthread.php?t=403647"), I installed GTK by running:
```
sudo aptitude install gnome-core-devel build-essential
```

and indeed, after doing that, when I run:
```
sudo apt-get install libgtk2.0-dev
```
I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
So it seems like it is installed, but when I try to get this code to compile:

```
#include<gtk/gtk.h>


int main(int argc, char *argv[]) {

    GtkWidget* window;

    gtk_init(&argc,&argv);

    window=gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_show(window);

    gtk_main();

    return 0;
    
}
```

with: ```
gcc prog.c -o prog `pkg-config --cflags --libs gtk-2.0`
```,
I get the following message:

```
Package gtk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk-2.0' found
prog.c:1:20: fatal error: gtk/gtk.h: No such file or directory
 #include<gtk/gtk.h>
                    ^
compilation terminated.
```

I couldn't find the file gtk-2.0.pc anywhere, and the gtk-2.0 is installed, so what's going on here?
What am I missing here, and how can I solve it?

---

### Post by Toz on 2014-10-12
> gcc prog.c -o prog `pkg-config --cflags --libs gtk-2.0`
You're missing a "+" in the gtk library name. It should be:
```
gcc prog.c -o prog `pkg-config --cflags --libs gtk+-2.0`
```

Also, there is an error in the code snippet. "gtk_window_show(window);" should actually be:
```
gtk_widget_show(window);
```

---

