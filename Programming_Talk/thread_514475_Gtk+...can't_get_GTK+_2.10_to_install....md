---
title: "Gtk+...can't get GTK+ 2.10 to install..."
date: 2007-07-31
forum: Programming Talk
---

### Post by Earthwormzim on 2007-07-31
I'm a newb programmer, and I'm interested in programming with Gtk+, but it seems that I can't even get the dern thing setup on my computer.

First of all, I went to [http://www.gtk.org/download/](http://www.gtk.org/download/) and downloaded the latest versions of GTK+ Source (2.10.9), GLib Source (2.12.9), and Pango Source (1.16.4).  So, I did
$ ./configure
$ make
$ sudo make install

for both Pango and and GLib, and it seems that all went well.  But when I did ./configure for Gtk+-2.10.9, I got this error:
-----------
checking for GLIB - version >= 2.12.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.12.9, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.12.0 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/pub/gtk/](ftp://ftp.gtk.org/pub/gtk/).
-----------
So, how do I fix this problem, exactly?  From what I gather from looking on other webpages, and forums, I think it might be a path variable problem.  If so, how, exactly, do I change/set this variable, and what do I change/set it to?  If this is not the case, then...what is? 

I have more questions...but I'll get to those when I get this problem fixed.

---

### Post by Earthwormzim on 2007-07-31
Ok...nm.  I think I figured it out.  On the command line, I typed:
----------
$ LD_LIBRARY_PATH="/opt/glib2/lib"
$ PATH="/opt/glib2/bin:$PATH"
$ export LD_LIBRARY_PATH PATH
$ ./configure --prefix=/opt/gtk
----------
...and it seemed to have worked.  So, I ran make, and sudo make install, and everything seemed to have gone well.

So, now, I went to [http://www.gtk.org/tutorial/c39.html](http://www.gtk.org/tutorial/c39.html) and cut & paste this example:
----------
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
----------
and compiled it with 
$ gcc test.cpp -o test `pkg-config --cflags --libs gtk+-2.0`

And I got this error:
----------
/tmp/ccAQIuxp.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
----------

Am I missing something?  What next?

---

### Post by loell on 2007-07-31
just install the development files from ubuntu repo, to get you up and running :) .

in the terminal, type..

```
sudo apt-get install libgtk2.0-dev 
```

---

### Post by Earthwormzim on 2007-07-31
EUREKA!!!!
I GOT IT! 

I compiled it with g++ instead of gcc, and it worked great!  Fantastic!  My first GTK+ Window!  SWEEEEEEET!  

Now...time to figure out how to scroll large fonts across it...

---

### Post by Earthwormzim on 2007-07-31
> **loell said:**
> just install the development files from ubuntu repo, to get you up and running :) .

in the terminal, type..

```
sudo apt-get install libgtk2.0-dev 
```

Thanks for the reply...but apparently the g++ thing was the problem.

---

### Post by loell on 2007-08-01
:) you compiled a c source code on a c++ compiler ,

in the future , just use **gcc **, since you are learning c gtk.

---

