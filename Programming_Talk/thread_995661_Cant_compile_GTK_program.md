---
title: "Cant compile GTK program"
date: 2008-11-28
forum: Programming Talk
---

### Post by rraj.be on 2008-11-28
I have just started to learn GUI programing . . 

I am through this tutorial

[http://library.gnome.org/devel/gtk-tutorial/stable/c39.html]("http://library.gnome.org/devel/gtk-tutorial/stable/c39.html")

in this page i cant compile the first program itself 


the program is

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

this is what i get as result

```
raj@raj-desktop:~$ cd /home/raj/Documents/PROJECT/gtk
raj@raj-desktop:~/Documents/PROJECT/gtk$ gcc base.c -o base `pkg-config --cflags --libs gtk+-2.0`
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
base.c:1:21: error: gtk/gtk.h: No such file or directory
base.c: In function ‘main’:
base.c:5: error: ‘GtkWidget’ undeclared (first use in this function)
base.c:5: error: (Each undeclared identifier is reported only once
base.c:5: error: for each function it appears in.)
base.c:5: error: ‘window’ undeclared (first use in this function)
base.c:9: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
raj@raj-desktop:~/Documents/PROJECT/gtk$ 


```

i dont know what hearder is missing or what path is mising . .

Could any one help me in this,. .

---

### Post by nvteighen on 2008-11-28
Have you the libgtk2.0-dev package installed in your system?

EDIT: Also, I highly recommend you to install libgtk2.0-doc and devhelp. DevHelp is a nice HTML documentation browser very useful to deal with GNOME/GTK's huge API docs in a sane way (and offline!).

---

### Post by csilviu on 2008-11-28
```
sudo apt-get install gnome-core-devel
```

---

