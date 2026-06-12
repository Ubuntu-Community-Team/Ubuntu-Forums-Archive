---
title: "How to pass PATH to c program in Anjunta"
date: 2010-01-27
forum: Programming Talk
---

### Post by Milliways on 2010-01-27
I have written a program using gtk+ and glade. It is now time to install it.

How do I pass the path of the installed glade file /usr/local/share/... to gtk_builder_add_from_file()

Every example I have seen uses a local string like "test.glade", and even the Anjuta template uses hard coded paths.

It seems pointless using automake if this is necessary.

Is there a standard way of doing this?
Does Anjuta have a preprocessor variable?

Alternatively I could export a variable from the Makefile

---

### Post by zaniah on 2011-10-11
I was wondering about this too.

I think you need to add something like:

INCLUDES = \
    -DPACKAGE_DATA_DIR=\""$(datadir)"\" 

to your src directory Makefile.am

and 

#ifdef HAVE_CONFIG_H
#  include <config.h> 
in 'main.c'

then in your 'header.h' you can define the glade file as say:
#define XMLFILE "interface.glade"

in 'main.c':
GtkBuilder *builder;
builder = gtk_builder_new ();
gtk_builder_add_from_file(builder, PACKAGE_DATA_DIR "/" PACKAGE "/" XMLFILE, NULL);

The #define PACKAGE is generated automatically and found in config.h

...so you can now ./configure --prefix=/usr/local or /opt etc and after "sudo make install" the executable should be able to load the external glade file, no matter the path it was installed to.

Not fully tested and I am a beginner at this and I don't use Anjuta :(

---

