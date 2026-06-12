---
title: "What file do I stick this in?  PKG_CHECK_MODULES([MYAPP], [gtkmm-2.4 &gt;= 2.8.0])"
date: 2007-07-29
forum: Programming Talk
---

### Post by xl_cheese on 2007-07-29
I'm trying to set up an automake/autoconf.

I compiled this sample helloworld ok:
[http://www.openismus.com/documents/linux/automake/automake.shtml](http://www.openismus.com/documents/linux/automake/automake.shtml)

However, when I add include gtkmm.h in the helloworld program I get errors about finding gtkmm.h

I added 

```
PKG_CHECK_MODULES([MYAPP], [gtkmm-2.4 >= 2.8.0])
```

to the configure.ac file, but it does not seem to work.  

Is this the right line to include and am I sticking in the right place?

fyi- I have already sucessfully compiled a simple hello program using:

```
g++ simple.cc -o simple `pkg-config gtkmm-2.4 --cflags --libs`
```

thanks.

---

### Post by xl_cheese on 2007-07-29
After searching high and low I found the answer.

In the src/makefile.am I needed these two lines.

LIBS = $(DEPS_LIBS)
INCLUDES = $(DEPS_CFLAGS)

In the configure.ac I needed this line.
PKG_CHECK_MODULES(DEPS, gtkmm-2.4 >= 1.0.0 )

---

### Post by mrbrklyn on 2008-10-02
there is a better method to this.  You should be using the CXXFLAG for C++

Here is a cut and paste on this solution 

Hello

I'm really a novice at autoconf and automake and trying to learn some
gtkmm but I'm running into a problem that I just don't have the
familiarity to solve and I'd like to request some help

I've done a google search for a solution and came up blank so I hope
someone can help me here.

I'm working from documentation here
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-headers-and-linking.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-headers-and-linking.html)
[http://www.openismus.com/documents/linux/automake/automake.shtml#ExampleFiles](http://www.openismus.com/documents/linux/automake/automake.shtml#ExampleFiles)
[http://www.elitecoders.de/mags/cscene/CS2/CS2-10.html](http://www.elitecoders.de/mags/cscene/CS2/CS2-10.html)
[http://www.openismus.com/documents/linux/automake/automake.shtml](http://www.openismus.com/documents/linux/automake/automake.shtml)
and of course the GNU manual and [http://sources.redhat.com/autobook/](http://sources.redhat.com/autobook/)

I need to include the include and library flags into autoconf and
automake and it seems to fail to pickup the gtkmm and gtk library

I'm using this autogen.sh script
---------------------------------------------
#! /bin/sh

# $Id: autogen.sh,v 1.4 2002/12/02 01:39:49 murrayc Exp $
#
# Copyright (c) 2002 Daniel Elstner
#
# This program is free software; you can redistribute it and/or modify
dir=`echo "$0" | sed 's,[^/]*$,,'`
echo $dir
test "x${dir}" = "x" && dir='.'

if test "x`cd "${dir}" 2>/dev/null && pwd`" != "x`pwd`"
then
echo "This script must be executed directly from the source
directory."
exit 1
fi

rm -f config.cache acconfig.h

echo "- libtoolize." && \
libtoolize --force && \
echo "- aclocal." && \
aclocal && \
echo "- autoconf." && \
autoconf && \
echo "- autoheader." && \
autoheader && \
echo "- automake." && \
automake --add-missing --gnu && \
echo && \
./configure "$-at-" && exit 0

exit 1
--------------------------------------------



This is my top level configure.ac
____________________________________________
AC_INIT(src/one_window.cc)

AM_INIT_AUTOMAKE(one_window,0.1)
AM_CONFIG_HEADER(config.h)

AC_PROG_CC
AC_PROG_CXX

AC_PROG_INSTALL
AC_PROG_LIBTOOL

PKG_CHECK_MODULES([MYAPP], [gtkmm-2.4 >= 2.4.0])
AC_OUTPUT(Makefile src/Makefile)
----------------------------------------------




This is my toplevel Makefile.am
------------------------------------------------

SUBDIRS = src
EXTRA_DIST=autogen.sh
________________________________________________




This is my src directory Makefile.am
_______________________________________________

bin_PROGRAMS = onewindow
onewindow_SOURCES = one_window.cc

______________________________________________


and the C++ code is very simple
one_window.cc
_____________________________________________
#include

int main(int argc, char *argv[])
{
Gtk::Main kit(argc, argv);

Gtk::Window window;

Gtk::Main::run(window);

return 0;
}
_____________________________________



Everything seems to work except for the make command

ruben-at-www2:~/cplus/pharm/gmm> make
make all-recursive
make[1]: Entering directory `/home/ruben/cplus/pharm/gmm'
Making all in src
make[2]: Entering directory `/home/ruben/cplus/pharm/gmm/src'
cd .. && /bin/sh /home/ruben/cplus/pharm/gmm/missing --run automake-1.9
--gnu
src/Makefile
cd .. && /bin/sh ./config.status src/Makefile depfiles
config.status: creating src/Makefile
config.status: executing depfiles commands
make[2]: Leaving directory `/home/ruben/cplus/pharm/gmm/src'
make[2]: Entering directory `/home/ruben/cplus/pharm/gmm/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -g -O2 -MT one_window.o -MD -MP
-MF ".de
ps/one_window.Tpo" -c -o one_window.o one_window.cc; \
then mv -f ".deps/one_window.Tpo" ".deps/one_window.Po"; else rm -f
".deps/one_w
indow.Tpo"; exit 1; fi
one_window.cc:1:19: gtkmm.h: No such file or directory
one_window.cc: In function `int main(int, char**)':
one_window.cc:5: error: `Gtk' undeclared (first use this function)
one_window.cc:5: error: (Each undeclared identifier is reported only
once for
each function it appears in.)
one_window.cc:5: error: syntax error before `::' token
make[2]: *** [one_window.o] Error 1
make[2]: Leaving directory `/home/ruben/cplus/pharm/gmm/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ruben/cplus/pharm/gmm'
make: *** [all] Error 2


The resulting Makefile.in has

MYAPP_CFLAGS = -at-MYAPP_CFLAGS-at-
MYAPP_LIBS = -at-MYAPP_LIBS-at-


and the src level Makefile has

MYAPP_CFLAGS = -DXTHREADS -D_REENTRANT -DXUSE_MTSAFE_API
-I/opt/gnome/include/gtkmm-2.4 -I/opt/gnome/lib/gtkmm-2.4/include
-I/opt/gnome/include/glibmm-2.4 -I/opt/gnome/lib/glibmm-2.4/include
-I/opt/gnome/include/gdkmm-2.4 -I/opt/gnome/lib/gdkmm-2.4/include
-I/opt/gnome/include/pangomm-1.4 -I/opt/gnome/include/atkmm-1.6
-I/opt/gnome/include/gtk-2.0 -I/opt/gnome/include/sigc++-2.0
-I/opt/gnome/lib/sigc++-2.0/include -I/opt/gnome/include/glib-2.0
-I/opt/gnome/lib/glib-2.0/include -I/opt/gnome/lib/gtk-2.0/include
-I/usr/X11R6/include -I/opt/gnome/include/pango-1.0
-I/usr/include/freetype2 -I/usr/include/freetype2/config
-I/opt/gnome/include/atk-1.0
MYAPP_LIBS = -L/opt/gnome/lib -lgtkmm-2.4 -lgdkmm-2.4 -latkmm-1.6
-lgtk-x11-2.0 -lpangomm-1.4 -lglibmm-2.4 -lsigc-2.0 -lgdk-x11-2.0
-latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0
-lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0


So I'm just lost here. What am I doing wrong?


Ruben

On Thu, 02 Oct 2008 15:21:25 -0400, Alfred M. Szmidt wrote:

> I'm using this autogen.sh script
>
> Use autoreconf.
>
>
> This is my top level configure.ac
>
> Looks fine.
>
> This is my toplevel Makefile.am
>
> Looks fine.
>
> This is my src directory Makefile.am
>
> Looks fine.
>
> one_window.cc:1:19: gtkmm.h: No such file or directory
>
> You did not specify where the compiler should look for headers (and
> libraries).
>
> The resulting Makefile.in has
>
> MYAPP_CFLAGS = -at-MYAPP_CFLAGS-at-
> MYAPP_LIBS = -at-MYAPP_LIBS-at-
>
> CFLAGS is used for C, not C++. CXXFLAGS is what you wish to look at,
> and set.
>
> PKG_CHECK_MODULES I have never used that variable, maybe it is buggy
> and does not set CXXFLAGS accordingly, check the documentation for it.
> And maybe check with the people who maintain that macro (it isn't part
> of autoconf or automake).

OK Alfred, you were right on the MONEY

So just to make this complete so that someone else can find this in the
future I want to cut and paste this conversation on irc
----------------------------------------------------------------------
* Now talking on #gtk+
* Topic for #gtk+ is: Welcome to #gtk+:
[http://library.gnome.org/devel/gtk/stable/](http://library.gnome.org/devel/gtk/stable/) | GtkTreeView tutorial:
[http://scentric.net/tutorial/](http://scentric.net/tutorial/) | Do use Glade! But, don't use Glade to
generate source code!-
[http://developer.gnome.org/doc/API/2.0/libglade/index.html](http://developer.gnome.org/doc/API/2.0/libglade/index.html) | Do not ask to
ask! * Topic for #gtk+ set by __tim at Tue Jul 15 09:57:10 2008 mrbrklyn
He;;p
mrbrklyn hello
mrbrklyn anyone have expereince with autoconf mrbrklyn and automake
descender that's off-topic, but yeah I have mrbrklyn well I'm trying to
use it with gtkmm according to the docs on that sight
mrbrklyn and I can't get it to work, to find the gtk library
mrbrklyn I'm missing something obvious and I don't know what it is
mrbrklyn [http://www.nylxs.com/messages.html?id=538339&archive=2008-10-01](http://www.nylxs.com/messages.html?id=538339&archive=2008-10-01)
descender mrbrklyn, trying running pkg-config --modversion gtkmm-2.4 to
see if you have trouble with pkgconfig
descender oh n/m, you've gone past that stage
mrbrklyn pkg-config --modversion gtkmm-2.4 mrbrklyn 2.4.11
descender mrbrklyn, try adding two Automake targets:
descender onewindow_CXXFLAGS = $(MYAPP_CFLAGS)
descender onewindow_LDADD = $(MYAPP_LIBS) descender then rerun autotools
descender .. variables I mean
mrbrklyn add it to configure.ac?
mrbrklyn or Makefile.am
mrbrklyn ?
descender mrbrklyn, the Makefile.am that resides alongside your C++ source
files
descender that one with bin_PROGRAMS = onewindow
mrbrklyn Ok - BRB
mrbrklyn descender - that did it.
descender ok
mrbrklyn Now my question is why?
descender AFAICT, it has to do with your autoconf language settings
mrbrklyn I'm going to need to do that for every external lib?
descender PKG_CHECK_MODULES added the flags to CFLAGS but not CXXFLAGS
descender CFLAGS isn't used to compile C++ programs=
descender so the compiler flags were missing descender
mrbrklyn, I add each lib manually
mrbrklyn what does that mean?
descender which?
mrbrklyn to do it manually
descender like this:
descender onewindow_CXXFLAGS = $(LIB1_CFLAGS) $(LIB2_CFLAGS)
$(LIB3_CFLAGS) ..
descender onewindow_LDADD = $(LIB1_LIBS) $(LIB2_LIBS) $(LIB3_LIBS) ..
descender I think it's possible to get PKG_CHECK_MODULES to add the
detected flags to CXXFLAGS by setting the language to C++ with
AC_LANG([CXX])
mrbrklyn thanks
descender I'm wrong, PKG_CHECK_MODULES never modifies CFLAGS or CXXFLAGS,
so you always have to add the variables manually as in the example I gave
you
descender I gotta go to bed


_______________________________________

The finished example for the autotool files look like this

configure.ac on the top level

AC_INIT(src/onewindow.cc)

AM_INIT_AUTOMAKE(onewindow_cc,0.1)
AM_CONFIG_HEADER(config.h)

AC_PROG_CC
AC_PROG_CXX

AC_PROG_INSTALL
AC_PROG_LIBTOOL

PKG_CHECK_MODULES([GTKMM], [gtkmm-2.4 >= 2.4.0])
AC_OUTPUT(Makefile src/Makefile)


_________________________________________________

Top Level Makefile.am

SUBDIRS = src
EXTRA_DIST=autogen.sh

______________________________________

/src level Makefile.am


AC_INIT(src/onewindow.cc)

AM_INIT_AUTOMAKE(onewindow_cc,0.1)
AM_CONFIG_HEADER(config.h)

AC_PROG_CC
AC_PROG_CXX

AC_PROG_INSTALL
AC_PROG_LIBTOOL

PKG_CHECK_MODULES([GTKMM], [gtkmm-2.4 >= 2.4.0])
AC_OUTPUT(Makefile src/Makefile)

________________________________________________

all this is in reference to corrections needed for the gtkmm tutorial
located at

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-headers-and-linking.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-headers-and-linking.html)
and

[http://www.openismus.com/documents/linux/automake/automake.shtml#ExampleFiles](http://www.openismus.com/documents/linux/automake/automake.shtml#ExampleFiles)

Thanks for everyones help!

Ruben Safir


-- 
[http://www.mrbrklyn.com](http://www.mrbrklyn.com) - Interesting Stuff
[http://www.nylxs.com](http://www.nylxs.com) - Leadership Development in Free Software

So many immigrant groups have swept through our town that Brooklyn, like Atlantis, reaches mythological proportions in the mind of the world - RI Safir 1998

[http://fairuse.nylxs.com](http://fairuse.nylxs.com) DRM is THEFT - We are the STAKEHOLDERS - RI Safir 2002

"Yeah - I write Free Software...so SUE ME"

"The tremendous problem we face is that we are becoming sharecroppers to our own cultural heritage -- we need the ability to participate in our own society."

"> I'm an engineer. I choose the best tool for the job, politics be damned.<
You must be a stupid engineer then, because politcs and technology have been attached at the hip since the 1st dynasty in Ancient Egypt. I guess you missed that one."

Â© Copyright for the Digital Millennium

---

### Post by mrbrklyn on 2008-10-02
ah one corrections the 
src level Makefile.ac is

bin_PROGRAMS = onewindow
onewindow_SOURCES = onewindow.cc
onewindow_CXXFLAGS = $(GTKMM_CFLAGS)
onewindow_LDADD = $(GTKMM_LIBS)

which is the whol point :)

---

