---
title: "Unresolved References with GTKMM Helloworld"
date: 2015-01-14
forum: Programming Talk
---

### Post by crcarson on 2015-01-14
Sure I missing some package(s) but can't figure out which one.  Getting this error linking the Helloworld code from the gtkmm website.

```
cliff@cliffps:~/Projects/Test$ make -f newgtk.mak
g++ -c -g newgtk.cc -pthread -I/usr/include/gtkmm-3.0 -I/usr/lib/x86_64-linux-gnu/gtkmm-3.0/include -I/usr/include/atkmm-1.6 -I/usr/include/gtk-3.0/unix-print -I/usr/include/gdkmm-3.0 -I/usr/lib/x86_64-linux-gnu/gdkmm-3.0/include -I/usr/include/giomm-2.4 -I/usr/lib/x86_64-linux-gnu/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/x86_64-linux-gnu/pangomm-1.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/gtk-3.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/mirclient -I/usr/include/mircommon -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/cairomm-1.0 -I/usr/lib/x86_64-linux-gnu/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/sigc++-2.0 -I/usr/lib/x86_64-linux-gnu/sigc++-2.0/include -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include 
g++ -o newgtk newgtk.o -lgtkmm-3.0 -latkmm-1.6 -lgdkmm-3.0 -lgiomm-2.4 -lpangomm-1.4 -lglibmm-2.4 -lgtk-3 -lgdk-3 -lpangocairo-1.0 -lpango-1.0 -latk-1.0 -lcairo-gobject -lgio-2.0 -lcairomm-1.0 -lcairo -lsigc-2.0 -lgdk_pixbuf-2.0 -lgobject-2.0 -lglib-2.0  
newgtk.o: In function `HelloWorld::HelloWorld()':
/home/cliff/Projects/Test/helloworld.cc:13: undefined reference to `HelloWorld::on_button_clicked()'
newgtk.o: In function `HelloWorld::HelloWorld()':
/home/cliff/Projects/Test/helloworld.cc:13: undefined reference to `HelloWorld::on_button_clicked()'
collect2: error: ld returned 1 exit status
newgtk.mak:13: recipe for target 'newgtk' failed
make: *** [newgtk] Error 1
```

I think that I need the package that contains signal_clicked() but not sure at this point.

Update: shoudl have added running on 14.10 and installed libgtkmm-3.0 and all suggested packages.

---

### Post by spjackson on 2015-01-14
That error message is nothing to do with packages or libraries. It means that you have written in your own code something like
```

class HelloWorld {
// some stuff here

    void on_button_clicked();

// some more stuff
};

```
but nowhere in your code do you have
```

void HelloWorld::on_buttton_clicked()
{
// TODO fill in the details
}

```

---

### Post by QIII on 2015-01-14
Or you have

```
 void on_button_clicked ()
```

Without scope resolution thus:

```
 void HelloWorld::on_button_clicked ()
```

---

### Post by crcarson on 2015-01-14
Thanks, you are quite right, my cut and paste from the gtkmm web page failed.  On to the examples which I thought had a similar failure.

---

