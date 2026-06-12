---
title: "Glade not generating..."
date: 2006-12-26
forum: Programming Talk
---

### Post by Elrohir on 2006-12-26
I just installed Glade and after building source code, I go for the ./autogen.sh and I get an error about not having installed glib comes up...

anyone had this error? anyway to fix it?

---

### Post by Elrohir on 2006-12-26
nobody?

---

### Post by Elrohir on 2006-12-26
nobody? talk to me people, at least say that you're searching or something...

---

### Post by lnostdal on 2006-12-26
> **Elrohir said:**
> I just installed Glade and after building source code, I go for the ./autogen.sh and I get an error about not having installed glib comes up...

anyone had this error? anyway to fix it?

i must admit i'm  tired of answering this ... :}

* do not generate code using glade; generate XML (data) and load it using libglade @ runtime of your application

there is a pattern here: "lib***-dev" .. so we search:

```
aptitude search libgtk
```

..then

```
aptitude install libgtk2.0-dev libglib2.0-dev
```

(i believe libgtk2.0-dev pulls libglib2.0-dev and others too though) ..  also consider getting libgtk2.0-doc .. etc.

also see: [http://developer.gnome.org/doc/API/2.0/libglade/](http://developer.gnome.org/doc/API/2.0/libglade/)

---

### Post by Elrohir on 2006-12-27
> **lnostdal said:**
> 
* do not generate code using glade; generate XML (data) and load it using libglade @ runtime of your application


and how do I do this?

---

### Post by Elrohir on 2007-02-12
lnostad, new problem with Glade... I'm trying to build the source code on C++, and when I go for the ./autogen.sh step I get this error:
```

configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
/usr/bin/make  all-recursive
make[1]: Entering directory `/home/legithrand/Projects/cppcompiler'
Making all in po
make[2]: Entering directory `/home/legithrand/Projects/cppcompiler/po'
make[2]: *** No rule to make target `/config.status', needed by `Makefile'.  Stop.
make[2]: Leaving directory `/home/legithrand/Projects/cppcompiler/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/legithrand/Projects/cppcompiler'
make: *** [all] Error 2

```

---

### Post by psychicdragon on 2007-02-12
Source code generation is depreciated, use libglade to create the gui from the glade project file (something.glade).

Here are two links you should have a look at:
[Libglade]("http://www.jamesh.id.au/software/libglade/")
[Libglade Reference Manual]("http://developer.gnome.org/doc/API/2.0/libglade/")

---

### Post by Elrohir on 2007-02-12
> **psychicdragon said:**
> Source code generation is depreciated, use libglade to create the gui from the glade project file (something.glade).

Here are two links you should have a look at:
[Libglade]("http://www.jamesh.id.au/software/libglade/")
[Libglade Reference Manual]("http://developer.gnome.org/doc/API/2.0/libglade/")
It says that libglade works with C, I'm working with C++... and frankly, I see the reference manual and still have no idea how to use libglade... some crash course you can facilitate?

---

### Post by psychicdragon on 2007-02-12
There are of course C++ bindings for libglade. 

Here's the requisite page from the gtkmm tutorial: [Chapter 23. Glade and libglademm]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch23.html").

---

### Post by Elrohir on 2007-02-12
OK, I must admit now that I'm a complete ignorant... My best guess is that I must place this: ```
Glib::RefPtr<Gnome::Glade::Xml> refXml = Gnome::Glade::Xml::create("xxxxx.glade");
``` either on Terminal or on some file... close?

---

### Post by Elrohir on 2007-02-12
setting aside libglade (which I still have no idea how it works), is there a way to fix the problem last mentioned?

---

### Post by lnostdal on 2007-02-12
start glade, design something, save it (don't "Build") as `hello-glade' .. 

then type in the following code:

```

/*
  gcc -std=c99 -Wall -g `pkg-config --libs --cflags gtk+-2.0` `pkg-config --libs --cflags libglade-2.0` hello-glade.c -o hello-glade
*/
  
#include <gtk/gtk.h>
#include <glade/glade.h>

int main(int argc, char *argv[])
{
  GladeXML *xml;
  gtk_init(&argc, &argv);
  xml = glade_xml_new("hello-glade.glade", NULL, NULL);
  gtk_main();
  return 0;
}

```

save it as hello-glade.c, then compile it as shown in the comment at the top, run it and up pops what you just designed..   this should work; see the reference manual of libglade for info on how to get "hold of" the widgets .. or just ask here and i'll help :)

(if you want specific help with the mess-that-is c++/gtkmm someone else will have to volunteer for that .. (or you could pay me a truckload of money .. lol))

---

