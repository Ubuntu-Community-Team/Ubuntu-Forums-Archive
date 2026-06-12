---
title: "My newbish c++ makefile questions"
date: 2006-11-13
forum: Programming Talk
---

### Post by gareththegeek on 2006-11-13
Hello,

How do I go about compiling a libglademm program using c++ in kdevelop.  If I start a new project there is only the one gtk option which seems to be for building apps using glade in source code mode. I am trying to use xml (libglade) instead since everyone said that was the way to go.

Here is my source code (adapted from a tutorial [http://people.debian.org/~rleigh/gtk/ogcalc/ogcalc.pdf):](http://people.debian.org/~rleigh/gtk/ogcalc/ogcalc.pdf):)

------ gnomeman.h ------

#ifndef GNOMEMAN_H
#define GNOMEMAN_H

#include <gtkmm.h>
#include <libglademm.h>

class FrmGnomeman : public Gtk::Window
{
   public:
      FrmGnomeman();
      virtual ~FrmGnomeman();

   protected:
      // Signal handlers

   protected:
      // Member widgets

      // Glade interface description
   Glib::RefPtr<Gnome::Glade::Xml> mo_xml_interface;
};

#endif

------ gnomeman.cc ------

# include <iomanip>
# include <sstream>
# include <sigc++/retype_return.h>

#include "gnomeman.h"

FrmGnomeman::FrmGnomeman()
{
   set_title("gnomeman");

   mo_xml_interface = Gnome::Glade::Xml::create("gnomeman.glade", "frmGnomeman_mainBox");

   Gtk::Table *o_main_box;
   mo_xml_interface->get_widget("frmGnomeman_mainBox", o_main_box);
   add(*o_main_box);
}

FrmGnomeman::~FrmGnomeman(){}

------ main.cc ------

#include <gtk/gtk.h>
#include <glade/glade.h>

#include "gnomeman.h"

int main(int argc, char* argv[])
{
   Gtk::Main kit(argc, argv);

   FrmGnomeman frmGnomeman;
   kit.run(frmGnomeman);

   return 0;
}

So I try to build all and get:

...
/home/gareth/Programming/gnomeman/src/main.cc:3:25: error: glade/glade.h: No such file or directory
In file included from /home/gareth/Programming/gnomeman/src/main.cc:5:
/home/gareth/Programming/gnomeman/src/gnomeman.h:5:24: error: libglademm.h: No such file or directory
...

So I look and find out that where libglademm.h and glade/glade.h are and I tried adding them:
Project > Project Options > Configure Options > CPPFlags: -I/usr/include/libglademm-2.4 -I/usr/include/glade-2.0

Configure & Build it all again and I get:

Making all in src
cd .. && CONFIG_FILES=src/Makefile CONFIG_HEADERS= /bin/sh ./config.status
config.status: creating src/Makefile
g++ -DHAVE_CONFIG_H -I. -I/home/gareth/Programming/gnomeman/src -I.. -I/usr/include/libglademm-2.4 -I/usr/include/glade-2.0 -O0 -g3 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/atk-1.0 -O0 -g3 -c /home/gareth/Programming/gnomeman/src/gnomeman.cc
g++ -DHAVE_CONFIG_H -I. -I/home/gareth/Programming/gnomeman/src -I.. -I/usr/include/libglademm-2.4 -I/usr/include/glade-2.0 -O0 -g3 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/atk-1.0 -O0 -g3 -c /home/gareth/Programming/gnomeman/src/main.cc
/home/gareth/Programming/gnomeman/src/main.cc:3:25: error: glade/glade.h: No such file or directory
make[2]: *** [main.o] Error 1
make[2]: Target `all' not remade because of errors.
make[1]: *** [all-recursive] Error 1
make: *** [all-recursive-am] Error 2
make: Target `all' not remade because of errors.
*** Exited with status: 2 ***

I'm probably just being dense but how do I compile this?

I have got it to compile using gedit and a shell script:

#!/bin/bash

c++ $(pkg-config --cflags libglademm-2.4) -c gnomeman.cc
c++ $(pkg-config --cflags libglademm-2.4) -c main.cc
c++ $(pkg-config --libs libglademm-2.4) -o gnomeman gnomeman.o main.o

But I wanna use an IDE :D

Thanks,

G!

---

### Post by llonesmiz on 2006-11-13
If you want to add them manually you need to put "-I/usr/include/libglade-2.0" at least. That should take care of the problem with glade/glade.h maybe later another problem will arise.

---

### Post by gareththegeek on 2006-11-15
Thanks for the suggestion, I changed the include path as suggested but still the same problems:

cd '/home/gareth/Programming/gnomeman/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
/bin/sh ./config.status --recheck
running /bin/sh /home/gareth/Programming/gnomeman/configure --enable-debug=full CFLAGS=-O0 -g3 CPPFLAGS=-I/usr/include/libglademm-2.4 -I/usr/include/libglade-2.0 CXXFLAGS=-O0 -g3 --no-create --no-recursion
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTKMM... yes
configure: creating ./config.status
cd . && CONFIG_FILES=Makefile CONFIG_HEADERS= /bin/sh ./config.status
config.status: creating Makefile
cd /home/gareth/Programming/gnomeman && autoheader
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING: AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader: [Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
cd . && CONFIG_FILES= CONFIG_HEADERS=config.h /bin/sh ./config.status
config.status: creating config.h
config.status: config.h is unchanged
make all-recursive
Making all in src
cd .. && CONFIG_FILES=src/Makefile CONFIG_HEADERS= /bin/sh ./config.status
config.status: creating src/Makefile
g++ -DHAVE_CONFIG_H -I. -I/home/gareth/Programming/gnomeman/src -I.. -I/usr/include/libglademm-2.4 -I/usr/include/libglade-2.0 -O0 -g3 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/atk-1.0 -O0 -g3 -c /home/gareth/Programming/gnomeman/src/main.cc
/bin/sh ../libtool --mode=link g++ -O0 -g3 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/atk-1.0 -O0 -g3 -o gnomeman gnomeman.o main.o -lgtkmm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lgtk-x11-2.0 -lpangomm-1.4 -lglibmm-2.4 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 
mkdir .libs
g++ -O0 -g3 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/atk-1.0 -O0 -g3 -o gnomeman gnomeman.o main.o /usr/lib/libgtkmm-2.4.so /usr/lib/libgdkmm-2.4.so /usr/lib/libatkmm-1.6.so /usr/lib/libgtk-x11-2.0.so /usr/lib/libpangomm-1.4.so /usr/lib/libglibmm-2.4.so /usr/lib/libsigc-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes /usr/lib/libpango-1.0.so /usr/lib/libcairo.so -lX11 /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so
gnomeman.o: In function `FrmGnomeman':/home/gareth/Programming/gnomeman/src/gnomeman.cc:11: undefined reference to `Gnome::Glade::Xml::create(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, Glib::ustring const&, Glib::ustring const&)'
:/home/gareth/Programming/gnomeman/src/gnomeman.cc:11: undefined reference to `Gnome::Glade::Xml::create(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, Glib::ustring const&, Glib::ustring const&)'
gnomeman.o: In function `Gtk::Table* Gnome::Glade::Xml::get_widget<Gtk::Table>(Glib::ustring const&, Gtk::Table*&)':/usr/include/libglademm-2.4/libglademm/xml.h:204: undefined reference to `Gnome::Glade::Xml::get_widget_checked(Glib::ustring const&, unsigned long)'
collect2: ld returned 1 exit status
make[2]: *** [gnomeman] Error 1
make[2]: Target `all' not remade because of errors.
make[1]: *** [all-recursive] Error 1
make: *** [all-recursive-am] Error 2
make: Target `all' not remade because of errors.
*** Exited with status: 2 ***

Anyone?

---

### Post by llonesmiz on 2006-11-15
Can you put the complete source directory as an attachment so I can test it? I really don't want to install kdevelop to try it. (You should probably do "make clean" before creating the archive to upload, in case you finally do it).

---

### Post by po0f on 2006-11-15
gareththegeek,

Why don't you just add your pkg-config declarations to CPPFLAGS?  And if you add a directory via -I (uppercase i) to include header files, you're more than likely going to have to link to that library with -l (ell).

I didn't notice anything similar to -lglade in the output.  The undefined reference error means you aren't linking with all the required libraries.

---

### Post by gareththegeek on 2006-11-15
Hi,

Like the title says I'm a newbie with makefiles and pkg-config (whatever that is) etc...

So

1. What is pkg-config and how do I add these include files to the CPPFLAGS?  I went to project>Project Options>Configure Options and added the include paths to the C/C++ preprocessor fields (CPPFLAGS) is there a better way to do this?

2. Adding the libs, how do I do this and how do I know what their names are?

3. What does "make clean" mean?

All my c++ experience is in Windows with Borland C++ Builder or Visual Studio and I am finding it tough doing anything in Linux, I just don't seem to know anything!? ](*,) 

Thanks
G!

---

### Post by llonesmiz on 2006-11-16
I'm not sure if this would work but maybe you could put `pkg-config --cflags libglademm-2.4` (the backticks are very important) in CPPFLAGS and `pkg-config --libs libglademm-2.4` in LDFLAGS in project>project options>configure options. If that doesn't work... a very ugly alternative would be using 

pkg-config --cflags --libs libglademm-2.4

from the terminal and then one by one copying from what it returns everything that starts with -I/usr...(capital i) to CPPFLAGS and everything that starts with -l...(non-capital L) to LDFLAGS.

make clean deletes every executable and object file leaving only the source code I thought it would be useful if you wanted to upload it. Probably there is an option from kdevelop to "clean" or "clean project". If there isn't one you should, using the terminal, go to the root directory of your project and enter "make clean" (although if we are lucky and what I wrote above works this won't be necessary).

Good luck.

---

### Post by gareththegeek on 2006-11-16
Thanks again!

So pkg-config is some program that returns compiler flags? The backticks mean to evaluate what's between them and use that in the command right?

Anyway, I'll give this a go tonight.

Works like a charm!  Thanks, man, you're a life saver! :D

Thanks,
G!

---

