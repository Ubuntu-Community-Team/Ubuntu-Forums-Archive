---
title: "Help with installation of GTK+ and compile C source files with gtk+."
date: 2012-10-02
forum: Programming Talk
---

### Post by underdog012 on 2012-10-02
Hello everyone,

I visited the gtk.org website and I downloaded the latest version of GTK+,GLib,Pango,GDK-Pixbuf and ATK.All of them were tar.xz.So first I copied first the GTK+ tar file in the /opt directory and I followed the installation guide from [here]("http://developer.gnome.org/gtk3/stable/gtk-building.html").So I untar the GTK+ in the /opt directory with root privileges and then I typed  ```
./configure --prefix=/opt/gtk 
``` in the gtk+ folder which waS created after the untar procedure.After I did ```
make
``` and ```
make install
```.So far so good.I did the exact same procedure by copying the tar.xz files of the GLib,Pango,GSK-Pixbuf,ATK in the /opt/gtk+-3.4.4 [COLOR=Red](mind that I have two folders in the /opt directory one of them is called[/COLOR] **gtk** [COLOR=Red]and the other[/COLOR] **gtk+-3.4.4**.).I untar them in /opt/gtk+-3.4.4,I went to the folder which was created after I untar each of these tars and I run ```
./configure --prefix=/opt/gtk 
``` and then ```
make
``` and then ```
make install
```.I did this procedure for each one of them separately with the following sequence: GLib,Pango,GDK-Pixbuf and ATK.The problem showed up when I tried to do the aforementioned procedure with GDK-Pixbuf.After I ran ```
./configure --prefix=/opt/gtk
``` in terminal there was was a message after the configure was failing telling me that GLib must be in 2.31.0 and above.I checked my GLib version and it was 2.34.2.So  after that I ran ldconfig and did the configure again of the GDK-Pixbuff,but still the same error message.I even ran sudo apt-get update,but nothing happened.So I decided to build and install the exact previous version of GLib.The 2.32.3.Which I did.After that I ran ```
./configure --prefix=/opt/gtk
``` for GDK-Pixbuff and it worked and then I ran ```
make
``` and ```
make install
``` and everything worked.I continued with ATK without any problems.In the end,I edited my .bashrc file by adding these lines:

```
CPPFLAGS="-I/opt/gtk/include" 
LDFLAGS="-L/opt/gtk/lib" 
PKG_CONFIG_PATH="/opt/gtk/lib/pkgconfig" 
export CPPFLAGS LDFLAGS PKG_CONFIG_PATH

LD_LIBRARY_PATH="/opt/gtk/lib" 
PATH="/opt/gtk/bin:$PATH" 
export LD_LIBRARY_PATH PATH
```I saved them and I decided to restart my system to make sure that every change will take effect.After the restart Nautilus was freaking dead.I tried to reinstall it,purge it and install it again,but without any success.So installed Nemo( you know the fork of Nautilus) and I have a file manager again.

Can somebody tell me if I have installed correctly GTK+,because I want to make a C program with graphical environment?And how on earth can I compile it with gcc or icc?

Thanks for your time and patience.I will post two screenshot of my gtk and gtk+- folder to show you what are the contained folders.

---

### Post by rai4shu2 on 2012-10-02
Why are you compiling gtk? You don't need to do that unless you want to work on changing gtk itself in some manner.

If you already had Gnome to begin with, the only thing you need to design a gtk gui is to install glade (available in Software Center).

---

### Post by underdog012 on 2012-10-02
Thank you for your valuable reply.I am about to kill myself right now because the only freaking thing that I had to do is to install gnome and I almost recreated the whole Ubuntu Distribution.:)

If you do not mind I would like to ask another question.

I wrote a very simple piece of C code to test GTK :
```

#include <stdio.h>    
#include <gtk/gtk.h>

int main (int argc ,char **argv)  {

    GtkWidget *window;

    gtk_init (&argc, &argv);

    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show (window);

    gtk_main ();

    return 0;

}
```How do I compile it and how can I use this source file with glade?Forgive my ignorance,I am trying to understand how someone can write a simple C source which uses GTK.That's all.

---

### Post by rai4shu2 on 2012-10-02
Well, from a command line, you'd do something like:

```
gcc `pkg-config --cflags gtk+-3.0` test.c `pkg-config --libs gtk+-3.0`
```

Where "test.c" is your above code. Of course, I'd use Geany to automate this sort of thing, but you can see how it works from the above.

---

### Post by underdog012 on 2012-10-02
> **rai4shu2 said:**
> Well, from a command line, you'd do something like:

```
gcc `pkg-config --cflags gtk+-3.0` test.c `pkg-config --libs gtk+-3.0`
```Where "test.c" is your above code. Of course, I'd use Geany to automate this sort of thing, but you can see how it works from the above.

Please note down on the 2nd of October 1:49:51 pm (GMT +2,daylight savings time activated)I compiled a C file using GTK+ libraries and it worked. :lolflag:

[SIZE=4]**[COLOR=Red](THANK YOU SO MUCH )x10^10000 rai4shu2![/COLOR]**[/SIZE]

I was trying for like 12 hours and I couldn't get it work.I will make a small research for glade tutorials.In case I have questions I will reply back here.

Once again thanks.

---

