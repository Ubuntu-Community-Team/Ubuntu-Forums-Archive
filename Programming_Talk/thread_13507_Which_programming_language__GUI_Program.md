---
title: "Which programming language / GUI Program?"
date: 2005-02-01
forum: Programming Talk
---

### Post by carlc on 2005-02-01
I have taken two classes in Visual Basic. I did not learn a lot and remember even less because it has been a few years since I have taken them.

Anyway, I would like to move on to a different programming language and would like to begin by using a program similar to Visual Studio in that you can use a GUI to create menus, text boxes, drop-down menus, etc and add code to them.

What would be a good language to learn and a good program to use?

---

### Post by Jad on 2005-02-01
so you are looking for a code genie, or wizard, I'm not sure about this dude. 
someone has to use his hands.

---

### Post by Juergen on 2005-02-01
I'm just starting to play with Python and Boa Constructor.
Looks good so far.

---

### Post by zabilcm on 2005-02-01
If you loved visual basic then you could probably try [Gambas](http://gambas.sourceforge.net/). It works much the same way as visual basic. It is Qt based does not exactly look like the other Ubuntu Gnome applications.

If you are willing to seperate out interface design and coding, you could try out [Glade](http://glade.gnome.org/). Here you design the interface and you can use a wide array of languages like c, c++, python etc to interact with the Glade generated interface.

---

### Post by carlc on 2005-02-01
Hey thanks for the info. I will check the programs out. Glade looked interesting because my ultimate goal is to learn C but I am also intresested in Python.

---

### Post by Daniel G. Taylor on 2005-02-02
[QUOTE=carlc]Hey thanks for the info. I will check the programs out. Glade looked interesting because my ultimate goal is to learn C but I am also intresested in Python.[/QUOTE]
 Glade works with C, C++, Python, and a handful of other languages to which bindings have been made. A GNOME developer once digitally slapped me for making a GTK+ GUI by hand and **not** using Glade. Now I use Glade XML GUIs and Python all the time :-) 

P.S. It was one of those crazy [Imendio](http://imendio.com) guys ;-) You know who you are!

---

### Post by miho on 2005-02-05
You should you Python and Boa Constructor, those are good. =D>

---

### Post by apoc on 2005-02-06
I've got Glade-2 (For GUI) and IDLE (For Python Coding), how do I get them to "work" togher, I've managed to make some simple stuff off a guide for python, and Glade seems on the surface easy enough to understand.. troube is I can't find any guides on how to make them work together. ?

---

### Post by rufius on 2005-02-06
[QUOTE=carlc]I have taken two classes in Visual Basic. I did not learn a lot and remember even less because it has been a few years since I have taken them.

Anyway, I would like to move on to a different programming language and would like to begin by using a program similar to Visual Studio in that you can use a GUI to create menus, text boxes, drop-down menus, etc and add code to them.

What would be a good language to learn and a good program to use?[/QUOTE]
 My approach would be a bit different compared to the Visual Basic method you're looking for but personally I've found that working with programs that don't require the GUI or don't teach the GUI initially helped me understand programming better. I personally wouldn't recommend starting out with the GUI builders, but would rather read some tutorials on say python, c, c++, or ruby.

---

### Post by carlc on 2005-02-06
I know what you mean. I am currently reading a book on c++. I guess once I get more into the book, I will figure out which route I want to go.

---

### Post by Klunk on 2005-02-07
Personally I would go with Java, but then again I really like java and have been using it commercially for the last 3 years, after going through Visual Basic and C++ over the preceeding 11 years.

I would go for Eclipse as an IDE and use the Visual Design plug-in. All you would want is available for free at [http://www.eclipse.org](http://www.eclipse.org). It has a whole host of plug-ins available for C++, php, Perl, Ruby etc so not just a Java IDE.

---

### Post by Daniel G. Taylor on 2005-02-07
[QUOTE=apoc]I've got Glade-2 (For GUI) and IDLE (For Python Coding), how do I get them to "work" togher, I've managed to make some simple stuff off a guide for python, and Glade seems on the surface easy enough to understand.. troube is I can't find any guides on how to make them work together. ?[/QUOTE]
 This is what I started with:

[http://www.linuxjournal.com/article/6586](http://www.linuxjournal.com/article/6586)

---

### Post by apoc on 2005-02-07
@Daniel

Sweet, thank you  :D

---

### Post by blixtra on 2005-02-10
[QUOTE=zabilcm]If you loved visual basic then you could probably try [Gambas](http://gambas.sourceforge.net/). It works much the same way as visual basic. It is Qt based does not exactly look like the other Ubuntu Gnome applications.[/QUOTE]

Just wanted to make clear that Gambas is not "Qt based".  Gambas is a language similar to Visual Basic but is in no way tied to the GUI.  For example, you can develop console programs with Gambas.  Currently, however, there is only a stable binding for Qt which is why the IDE is in Qt.  The development version also has a Gtk binding which last I checked is scheduled for release in summer some time.

Chris

---

### Post by defkewl on 2005-02-12
Have you tried Java yet? It's quite nice and IMHO it has a very massive user.

---

### Post by anthony_barker on 2005-02-12
If you plan to do development for an open platform (linux/gnome) I would stick to an open platform. For all of Sun's posturing around opening Java and Solaris both are still closed and owned by large multinationals who have a duty to make money for their shareholders.

So stick to c/c++/python/perl/ruby and widget sets wxWidgets (a wrapper), GTK, TK or QT.

I've found wxDesigner + Python fairly productive. 

If you want to parlay what you've learned to working for large company I might look at mono. Otherwise I'd avoid it.

---

### Post by dewfis on 2005-03-09
[QUOTE=][/QUOTE]
 I like Glade also, but I always have a problem with the way it structures its code.  At some point in my project, I always end up abandoning Glade and reorganizing the code.  Of course, from then on, I can't use Glade anymore.  But it's great for seeing which calls to use to do things in the interface.

There is also supposed to be a tool called Kexi, which is part of the KOffice suite.  It seems to be an MS Access clone.  I don't know if it's been released yet, or what shape it's in, but it might be a nice tool for someone coming from VB.

---

### Post by earobinson on 2005-03-11
Ok im trying to use glade but i dont seem to have glib how can i easly fix this

```
earobinson@earobinson:~/Desktop/GCList $ ./autogen.sh

**Error**: You must have `glib' installed.
You can get it from: [ftp://ftp.gtk.org/pub/gtk](ftp://ftp.gtk.org/pub/gtk)
```

---

### Post by earobinson on 2005-03-12
[QUOTE=carlc]I know what you mean. I am currently reading a book on c++. I guess once I get more into the book, I will figure out which route I want to go.[/QUOTE]
 Ok im trying to use glade but i dont seem to have glib how can i easly fix this

[CODE]earobinson@earobinson:~/Desktop/GCList $ ./autogen.sh

**Error**: You must have `glib' installed.
You can get it from: [ftp://ftp.gtk.org/pub/gtk](ftp://ftp.gtk.org/pub/gtk)[/CODE

---

### Post by Daniel G. Taylor on 2005-03-12
[QUOTE=dewfis]I like Glade also, but I always have a problem with the way it structures its code.  At some point in my project, I always end up abandoning Glade and reorganizing the code.  Of course, from then on, I can't use Glade anymore.  But it's great for seeing which calls to use to do things in the interface.[/QUOTE]
You should use libglade to load the XML Glade files instead of generating C or C++ code. Then you can edit the files and see the effects on the next program run and use signal autoconnecting. See: 
[http://developer.gnome.org/doc/API/2.0/libglade/libglade-notes.html](http://developer.gnome.org/doc/API/2.0/libglade/libglade-notes.html)
[http://developer.gnome.org/doc/API/2.0/libglade/GladeXML.html](http://developer.gnome.org/doc/API/2.0/libglade/GladeXML.html)
>  Ok im trying to use glade but i dont seem to have glib how can i easly fix this
```
earobinson@earobinson:~/Desktop/GCList $ ./autogen.sh

**Error**: You must have `glib' installed.
You can get it from: ftp://ftp.gtk.org/pub/gtk
```
Install libglade2-dev, which should get you the development files for glib, gtk, and glade. :wink:

---

### Post by earobinson on 2005-03-13
[QUOTE=Daniel G. Taylor]You should use libglade to load the XML Glade files instead of generating C or C++ code. Then you can edit the files and see the effects on the next program run and use signal autoconnecting. See: 
[http://developer.gnome.org/doc/API/2.0/libglade/libglade-notes.html](http://developer.gnome.org/doc/API/2.0/libglade/libglade-notes.html)
[http://developer.gnome.org/doc/API/2.0/libglade/GladeXML.html](http://developer.gnome.org/doc/API/2.0/libglade/GladeXML.html)

Install libglade2-dev, which should get you the development files for glib, gtk, and glade. :wink:[/QUOTE]


almost there i now get an error when i type make any ideas why? i havent typed any code just used glade so should it not be error free.

```
earobinson@earobinson:~/Desktop/GCList $ ./autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Making ./aclocal.m4 writable ...
Running aclocal  ...
Running autoheader...
Running automake --gnu  ...
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./missing'
automake: configure.in: installing `./config.guess'
automake: configure.in: installing `./config.sub'
automake: Makefile.am: installing `./INSTALL'
automake: Makefile.am: installing `./COPYING'
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... yes
checking PACKAGE_CFLAGS... -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking PACKAGE_LIBS... -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing default-1 commands
config.status: executing default-2 commands
Now type `make' to compile.
earobinson@earobinson:~/Desktop/GCList $ make
cd . && autoheader
make  all-recursive
make[1]: Entering directory `/home/earobinson/Desktop/GCList'
Making all in src
make[2]: Entering directory `/home/earobinson/Desktop/GCList/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c main.c
main.c: In function `main':
main.c:36: warning: assignment makes pointer from integer without a cast
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c support.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c interface.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c callbacks.c
gcc  -g -O2  -o gclist  main.o support.o interface.o callbacks.o -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
main.o(.text+0x63): In function `main':
/home/earobinson/Desktop/GCList/src/main.c:36: undefined reference to `create_window1'
collect2: ld returned 1 exit status
make[2]: *** [gclist] Error 1
make[2]: Leaving directory `/home/earobinson/Desktop/GCList/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/earobinson/Desktop/GCList'
make: *** [all-recursive-am] Error 2
```

---

### Post by earobinson on 2005-03-14
[QUOTE=carlc]I know what you mean. I am currently reading a book on c++. I guess once I get more into the book, I will figure out which route I want to go.[/QUOTE]
 [QUOTE=Daniel G. Taylor]You should use libglade to load the XML Glade files instead of generating C or C++ code. Then you can edit the files and see the effects on the next program run and use signal autoconnecting. See: 
[http://developer.gnome.org/doc/API/2.0/libglade/libglade-notes.html](http://developer.gnome.org/doc/API/2.0/libglade/libglade-notes.html)
[http://developer.gnome.org/doc/API/2.0/libglade/GladeXML.html](http://developer.gnome.org/doc/API/2.0/libglade/GladeXML.html)

Install libglade2-dev, which should get you the development files for glib, gtk, and glade. :wink:[/QUOTE]


almost there i now get an error when i type make any ideas why? i havent typed any code just used glade so should it not be error free.

```
earobinson@earobinson:~/Desktop/GCList $ ./autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Making ./aclocal.m4 writable ...
Running aclocal  ...
Running autoheader...
Running automake --gnu  ...
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./missing'
automake: configure.in: installing `./config.guess'
automake: configure.in: installing `./config.sub'
automake: Makefile.am: installing `./INSTALL'
automake: Makefile.am: installing `./COPYING'
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... yes
checking PACKAGE_CFLAGS... -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking PACKAGE_LIBS... -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing default-1 commands
config.status: executing default-2 commands
Now type `make' to compile.
earobinson@earobinson:~/Desktop/GCList $ make
cd . && autoheader
make  all-recursive
make[1]: Entering directory `/home/earobinson/Desktop/GCList'
Making all in src
make[2]: Entering directory `/home/earobinson/Desktop/GCList/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c main.c
main.c: In function `main':
main.c:36: warning: assignment makes pointer from integer without a cast
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c support.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c interface.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c callbacks.c
gcc  -g -O2  -o gclist  main.o support.o interface.o callbacks.o -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
main.o(.text+0x63): In function `main':
/home/earobinson/Desktop/GCList/src/main.c:36: undefined reference to `create_window1'
collect2: ld returned 1 exit status
make[2]: *** [gclist] Error 1
make[2]: Leaving directory `/home/earobinson/Desktop/GCList/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/earobinson/Desktop/GCList'
make: *** [all-recursive-am] Error 2
```

---

### Post by earobinson on 2005-03-15
[QUOTE=earobinson]almost there i now get an error when i type make any ideas why? i havent typed any code just used glade so should it not be error free.

```
earobinson@earobinson:~/Desktop/GCList $ ./autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Making ./aclocal.m4 writable ...
Running aclocal  ...
Running autoheader...
Running automake --gnu  ...
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./missing'
automake: configure.in: installing `./config.guess'
automake: configure.in: installing `./config.sub'
automake: Makefile.am: installing `./INSTALL'
automake: Makefile.am: installing `./COPYING'
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... yes
checking PACKAGE_CFLAGS... -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking PACKAGE_LIBS... -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing default-1 commands
config.status: executing default-2 commands
Now type `make' to compile.
earobinson@earobinson:~/Desktop/GCList $ make
cd . && autoheader
make  all-recursive
make[1]: Entering directory `/home/earobinson/Desktop/GCList'
Making all in src
make[2]: Entering directory `/home/earobinson/Desktop/GCList/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c main.c
main.c: In function `main':
main.c:36: warning: assignment makes pointer from integer without a cast
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c support.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c interface.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c callbacks.c
gcc  -g -O2  -o gclist  main.o support.o interface.o callbacks.o -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
main.o(.text+0x63): In function `main':
/home/earobinson/Desktop/GCList/src/main.c:36: undefined reference to `create_window1'
collect2: ld returned 1 exit status
make[2]: *** [gclist] Error 1
make[2]: Leaving directory `/home/earobinson/Desktop/GCList/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/earobinson/Desktop/GCList'
make: *** [all-recursive-am] Error 2
```[/QUOTE]
 no ideas?

---

### Post by earobinson on 2005-03-16
Almost there i now get an error when i type make any ideas why? i havent typed any code just used glade so should it not be error free.

```
earobinson@earobinson:~/Desktop/GCList $ ./autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Making ./aclocal.m4 writable ...
Running aclocal  ...
Running autoheader...
Running automake --gnu  ...
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./missing'
automake: configure.in: installing `./config.guess'
automake: configure.in: installing `./config.sub'
automake: Makefile.am: installing `./INSTALL'
automake: Makefile.am: installing `./COPYING'
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... yes
checking PACKAGE_CFLAGS... -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking PACKAGE_LIBS... -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing default-1 commands
config.status: executing default-2 commands
Now type `make' to compile.
earobinson@earobinson:~/Desktop/GCList $ make
cd . && autoheader
make  all-recursive
make[1]: Entering directory `/home/earobinson/Desktop/GCList'
Making all in src
make[2]: Entering directory `/home/earobinson/Desktop/GCList/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c main.c
main.c: In function `main':
main.c:36: warning: assignment makes pointer from integer without a cast
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c support.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c interface.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\"     -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"       -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c callbacks.c
gcc  -g -O2  -o gclist  main.o support.o interface.o callbacks.o -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
main.o(.text+0x63): In function `main':
/home/earobinson/Desktop/GCList/src/main.c:36: undefined reference to `create_window1'
collect2: ld returned 1 exit status
make[2]: *** [gclist] Error 1
make[2]: Leaving directory `/home/earobinson/Desktop/GCList/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/earobinson/Desktop/GCList'
make: *** [all-recursive-am] Error 2
```

---

### Post by JeffS on 2005-03-17
[QUOTE=Klunk]Personally I would go with Java, but then again I really like java and have been using it commercially for the last 3 years, after going through Visual Basic and C++ over the preceeding 11 years.

I would go for Eclipse as an IDE and use the Visual Design plug-in. All you would want is available for free at [http://www.eclipse.org](http://www.eclipse.org). It has a whole host of plug-ins available for C++, php, Perl, Ruby etc so not just a Java IDE.[/QUOTE]

Java is near ubiqutous in the enterprise, so learning it is always a good idea for those aspiring to earn a living programming.  However, to run Java + Eclipse one should have plenty of memory on the host system - at least 512meg.

That said, I love Glade + gEdit + Anjuta + C and/or C++ + Perl or Python for Gnome/GTK development, and QT Designer + Kate + Kdevelop + C++ for KDE development.

And I second the comment about learning to code first within and editor and command line first, then using the GUI designers.

In any case, happy progamming! 8)

---

### Post by defkewl on 2005-03-19
[QUOTE=anthony_barker]If you plan to do development for an open platform (linux/gnome) I would stick to an open platform. For all of Sun's posturing around opening Java and Solaris both are still closed and owned by large multinationals who have a duty to make money for their shareholders.[/QUOTE]
But at least it's standard unlike open platform language.  :-({|=

---

### Post by DJ_Max on 2005-03-19
[QUOTE=anthony_barker]If you plan to do development for an open platform (linux/gnome) I would stick to an open platform. For all of Sun's posturing around opening Java and Solaris both are still closed and owned by large multinationals who have a duty to make money for their shareholders.

So stick to c/c++/python/perl/ruby and widget sets wxWidgets (a wrapper), GTK, TK or QT.

I've found wxDesigner + Python fairly productive. 

If you want to parlay what you've learned to working for large company I might look at mono. Otherwise I'd avoid it.[/QUOTE]
Java being closed source has nothing to do with the power and genuis of it. Java is one of the most advanced cross-platform, OO languages out. Sun is a company made up of a bunch of smart programmers who created a great piece of software, why not use it? I hate when people down something cause it's owned by people trying to make a living. ](*,)

If you use Java you won't regret it.

---

### Post by Quest-Master on 2005-03-21
I must disagree.

I fully regretted even touching Java. It's just.. blah. It's more widely installed on systems, but that is probably the ONLY advantage it has over Python.

Python has a much cleaner syntax, down-to-earth and straightforward coding style, and has a wealth of libraries such as PyGTK, wxPython, Pygame, and many more.

---

### Post by DJ_Max on 2005-03-21
[QUOTE=Quest-Master]I must disagree.

I fully regretted even touching Java. It's just.. blah. It's more widely installed on systems, but that is probably the ONLY advantage it has over Python.
[/QUOTE]
Java has great web features(JSP, JDOM, Jimi, Jaxen, SAX2, JSTL etc.), over just about any language. Java is a universal language, and can be used for just about anything.

But Java isn't your common language, it's more of an art.

---

### Post by vague- on 2005-03-31
[QUOTE=Quest-Master]I fully regretted even touching Java. It's just.. blah. It's more widely installed on systems, but that is probably the ONLY advantage it has over Python.

Python has a much cleaner syntax, down-to-earth and straightforward coding style, and has a wealth of libraries such as PyGTK, wxPython, Pygame, and many more.[/QUOTE]

I like and use both Java and Python (and even Jython).  However, you cannot even compare the resources available to Python with the resources available to a Java programmer.

As for the only advantage being in it's wider installation base, I think that you must know that comment is not true.  I am not saying Python does not have advantages over Java (it does, and as I said, I like Python), but you must realise that Java has more to offer than a wider installation base.

---

### Post by Rottweiler on 2005-03-31
[QUOTE=DJ_Max]Java is one of the most advanced cross-platform, OO languages out.[/QUOTE]I don't consider Java to be a cross-platform language. It's more like a** no-platform** language.

Note that the topic of this thread is "GUI Program". The problem with Java is there seems to be no way to create true cross-platform GUI programs that behave like native apps and using the native widgets. Contrast with Python/wxPython.

Yes you can do "swing" and such but the apps are so ugly and non-functional as to be laughable. Ancient 1970s motif apps are pretty by comparison.

Now if there is some readily available (FLOSS) counterpart to wxPython for Java I'd like to be educated about it. I'd probably even use it. I wasn't able to find one. (There is wx4j.org but it appears to be a near dead project and nowhere near as usable as wxPython.)

That said, the person who mentioned Java could help you land a programming job in an "enterprise" shop is certainly correct. But I've done that sort of gig in a couple of places and I much prefer being independent. To each his own.

---

### Post by vague- on 2005-04-02
[QUOTE=Rottweiler]The problem with Java is there seems to be no way to create true cross-platform GUI programs that behave like native apps and using the native widgets.[/QUOTE]

[http://www.eclipse.org/swt/](http://www.eclipse.org/swt/)

Part of the Eclipse platform.  Offers native toolkits on Unix, Windows and Mac (possibly only OS X, I cannot recollect).  I have also found it less buggy than "wx".  Every large (to me, I just mean 25KLoC+) project that I have used "wx" in has shown at least one bug or problem with "wx".  That is why I do not use it anymore.

Examples of usage are the Eclipse IDE itself, Azureus (the bittorrent client) and RSSOwl (an RSS reader).  I am sure there are many more, but those are the few that I remember well.

---

### Post by Rottweiler on 2005-04-02
[QUOTE=vague-][http://www.eclipse.org/swt/]("http://www.eclipse.org/swt/")[/QUOTE]Thank you for that. Definitely worth a looksee.

---

### Post by lemone on 2005-04-20
[QUOTE=Quest-Master]I must disagree.

I fully regretted even touching Java. It's just.. blah. It's more widely installed on systems, but that is probably the ONLY advantage it has over Python.

Python has a much cleaner syntax, down-to-earth and straightforward coding style, and has a wealth of libraries such as PyGTK, wxPython, Pygame, and many more.[/QUOTE]

I have to agree with this one.  I try to avoid Java unless I'm being paid.  

Can anyone tell me how to get the pyUI module through apt?  Maybe I'm looking for the wrong package.  I've installed just about everything python2.4 in my repository list, but I still can't import pyui.   ](*,)   Thanks.

---

### Post by ZiZe on 2005-04-20
I've tried Borland CBuilderX, Kdevelop, anjuta and eclipse.
Right now im learning c++ myself, and i think eclipse is far better than any of the others.

---

### Post by hamiltjr on 2005-04-21
Currently I am a college student and recently took a course in Obect Oriented Design. For this course, our prof wanted to do his best as giving us an easy to use toolkit, but one which still required the programmer to "really" know what is going on. For this, he decided on **FLTK** ([www.fltk.org](http://www.fltk.org) ) which is a really easy to use toolkit that generally works on all *nix systems running an Xserver and, with some alternate configuration, can be configured to work on a Win32 system w/ Visual Studio (WHICH SHOULD BE AVOIDED!).

After meddling with FLTK for some time now, I do feel that I have a much better idea of OO programming and for a summer project, I am going to try working with GTK because of its popularity.

---

### Post by dataw0lf on 2005-04-21
May I suggest wxWidgets?  Great support in Ubuntu for it, and it's much more powerful, and easier, to use than GTK, IMHO.

---

### Post by MrBrownstone3g on 2005-04-21
You could try Lazarus a GPL Delphi clone, it is fairly complete but isn't not quite as mature as some of the development/gui enviroments out there.

You can find it [HERE](http://lazarus.freepascal.org)

---

### Post by nautilus on 2005-04-21
sorry, Java makes no sense.

I'd sooner write games in SNES .. language, because SNES ROM images run on more platforms than java does.

it's probably faster too, and takes far less ram.

java is the lazy language.  it's a neat idea for a language, but the problem with it is how it conflicts with fundamental principles of computation.

then again, i am a c programmer, and believe that memory management is about 95% of a program.  if your memory management sucks, your program sucks.

java doesn't do memory management.. ;/

whenever i write something in java, i feel like i'm making a "lego" program, because it's about as easy to make, and about as sturdy.

the other beef i have with it is, well, if the vm screws up and breaks your application, it's not your fault, but tough luck, it just won't work.

--

gambas is fun, yeah :D

i've made some cute little utilities with gambas.

---

### Post by Rodrigo on 2005-05-21
[QUOTE=nautilus]
then again, i am a c programmer, and believe that memory management is about 95% of a program.  if your memory management sucks, your program sucks.
[/QUOTE]

Thats all about programming for me, memory managment  :grin:

---

### Post by warfly on 2005-05-31
[QUOTE=nautilus]sorry, Java makes no sense.

I'd sooner write games in SNES .. language, because SNES ROM images run on more platforms than java does.

it's probably faster too, and takes far less ram.

java is the lazy language.  it's a neat idea for a language, but the problem with it is how it conflicts with fundamental principles of computation.

then again, i am a c programmer, and believe that memory management is about 95% of a program.  if your memory management sucks, your program sucks.

java doesn't do memory management.. ;/

whenever i write something in java, i feel like i'm making a "lego" program, because it's about as easy to make, and about as sturdy.

the other beef i have with it is, well, if the vm screws up and breaks your application, it's not your fault, but tough luck, it just won't work.

--

gambas is fun, yeah :D

i've made some cute little utilities with gambas.[/QUOTE]
I think it's all matter of taste :) However, automatic memory handling via VM is not inherently a bad concept, actually it was one of the reasons why Java was so successful on the server side. Problem is VM is far less efficient for small desktop applications than big and long running server side ones, but with modern JVM it's certainly viable to build fast end user applications in Java (see how popular Azureus is :)).

Certainly Java is more high level language than C/C++ but being high level just means that it's suitable for different kind of problems, not that it's easier to learn or program in. Building a Linux kernel module surely requires lot of skills, but it's by no means more difficult than building, say an crossplatform office suite even if the former is much more low level than the latter.

---

### Post by vague- on 2005-05-31
[QUOTE=nautilus]then again, i am a c programmer, and believe that memory management is about 95% of a program.  if your memory management sucks, your program sucks.[/QUOTE]

I am also a C programmer.  I write more lines of C than any other language I use.  I believe that if you think 95% of programming is the quality of your memory management that you are suffering from what the C2 Wiki calls PrematureOptimization - and there are some very good programmer who have written very good programs that seem to agree that this is not a good thing.  If a program I am writing is delivered on time with the desired feature set but uses 20% more memory than it should or I missed the fact that I could munmap(2) sooner (or even, maybe I missed an munmap(2) call out), then I am...well, happy is the wrong word, let's just say things could be worse.

When you are paid to program you will find that people are not immensely impressed by your home-brew memory manager (especially if you also guilty of writing specific managers for each program), as your output is not really all that useful to them.  Further, a lot of employment is in maintenance coding - you simply do not have the resources to change the memory management policy of some code bases you will have to maintain.  However, these programs do not "suck".  Far from it, that is why you are being paid to maintain it.  Could they manage memory better?  Probably, but their developers chose to deliver other features that mean users are not bothered by a few extra bytes (megabytes, even) of memory.

When programming in C or C++, I tend to use "safe" memory management practices over fast ones.  I would rather know that various memory management faults (especially exploitable faults like double frees) do not occur than gain a slight performance increase.  How robust and "secure" (I use the term loosely) your program is often at least as important as it's speed.  Even slow memory management is not likely to be the cause of a slow program - it is much more likely your program is slow due to an algorithm flaw or being bound to a input/output of a slow device.  In general, it is a case of optimising the wrong thing.

---

### Post by Gsibbery on 2005-06-01
[QUOTE=nautilus]sorry, Java makes no sense.

I'd sooner write games in SNES .. language, because SNES ROM images run on more platforms than java does.

it's probably faster too, and takes far less ram.

java is the lazy language.  it's a neat idea for a language, but the problem with it is how it conflicts with fundamental principles of computation.

then again, i am a c programmer, and believe that memory management is about 95% of a program.  if your memory management sucks, your program sucks.

java doesn't do memory management.. ;/

whenever i write something in java, i feel like i'm making a "lego" program, because it's about as easy to make, and about as sturdy.

the other beef i have with it is, well, if the vm screws up and breaks your application, it's not your fault, but tough luck, it just won't work.

--

gambas is fun, yeah :D

i've made some cute little utilities with gambas.[/QUOTE]


Maybe to you, Java makes no sense, but to many others it does. Java does do memory management by the way, it just hides that aspect of it from you, which can have advantages in some cases. I find GUI programming substantially less of a pain in Java than in C. I have fiund that Java programs are just as reliable and robust as C programs are . . . I admit that I am a recent convert, but if you think Java is the "lazy" language, maybe you should switch to assembler. :P That's what I use when I really need to optimize a program, although I wouldn't suggest it to a beginner.

---

### Post by DarkKnight on 2005-06-07
IMO, I like Java more then C/C++/Python/PHP because it is 'clean'. 

When I write Java code I like the nice clean behavior of it. Everything has it's place, everything has it's way, generally everything fits. 

I'm not saying C/C++ is awful, but seeing larger projects written in C/C++ makes me cringe... It's just so all over the place.
Python is also 'messy'... it reminds me too much of VB.
PHP is my second preference in languages, it's not as clean as Java, but it gives me the option of OO or structure, the option is nice. 

It's just my view on it...

---

### Post by .::welemski::. on 2005-09-10
If you like programming in VisualBasic try [REALBasic](http://www.realbasic.com) 
It works similar to Visual basic but you can compile your program to run into different types platforms, e.g Linux,Mac,Windows

---

### Post by BadAsh71 on 2005-09-10
There is always [Mono](http://www.mono-project.com).

You can design your user interface in Glade (Glade#) and then write your applications in any Mono supported .Net language (Visual Basic, C#, Python, Ruby, etc).

The Mono Project includes a Visual Studio *like* IDE called [MonoDevelop](http://www.monodevelop.com) but that is far from stable (but, has lots of promise and will undoubtedly be really good later).

Glade does not yet support Visual Basic (or VB.Net) but it does have support for "C, C++, Java, Perl, Python, C#, Pike, Ruby, Haskell, Objective Caml and Scheme".

I myself am an ex VB guy (11 years) and I have been programming in C# for about 5 years now.  I am waiting for the day when MonoDevelop is not only stable but fully incorporates a Glade GUI Designer within its IDE so I can start doing some true Cross-Platform Development using Mono.

Okay, could just end there but I'll add another insult to using Java.... its slow as hell on Windows but decent on Linux... so as long as "cross-platform" only means throughout Linux distros to you then fine, Java is great, otherwise... try C# via Mono  :)

---

### Post by Nasso on 2005-09-30
i think you should try delphi. you will have to be able to program but the guis are really simple and sweet to make, even fun :) (cant say its simple and slick to work with java.awt ;) )

edit: delphi is the name of both the programming enviroment and the programming language. But the enviroment for linux is called kylix. i think its free too :) 

edit2: kylix aint free :( delphi for windows got personal editions though. i think there was a personal version of kylix before but maybe they removed it :(

---

### Post by innovatel on 2005-10-27
At work I'm programming with C# - .NET ( windows platform ) but now I want to learn other languages in "Linux Planet". 

For example : java, python and other ... i'll see @ moment :cool: 

The gui program? To learn I think the gedit or nano is the best solution because you don't have "external-help" and you must to study the new language. After yuo can use other program. For example in Linux I use bluefish, eclipse or netbeans.

---

### Post by ofek on 2005-10-28
I mostly program with python(still in learning, basic programs) and c++.
i use gedit for python and c++ i like to do the work my self and not let the program do it for me.

---

### Post by fos on 2005-11-10
This is an interesting thread.

I first learned Fortran back in the days of punch cards. When personal computers came out in the seventies, I played with Basic. Since that time, I have taken a course in C and it has become my favorite.

Recently I have become involved with php and mysql due to web site development.

My question is:

What is a good language to use to create a graphical user interface for mysql? I would like to distribute it as an open source application.

Thanks, Jeff

---

### Post by forlog on 2005-11-12
I would also recommend wxWindows - you can use both python and c++ with it and it's really very intuitive and portable. (and remember, c++ rocks :) )

---

### Post by Quest-Master on 2005-11-12
It's called wxWidgets now though, due to patent issues with Microsoft.

Just a heads up for anyone who's interested in learning more about the library.

---

### Post by UbuWu on 2005-11-12
[QUOTE=fos]

What is a good language to use to create a graphical user interface for mysql? I would like to distribute it as an open source application.

[/QUOTE]

Python-mysqldb is in the repositories and could be useful.

---

### Post by xerman on 2005-11-17
Hi there,

If I'm used to PHP and XHTML/HTML and need to build a standalone app for linux (Ubuntulinux) what is the best partnership in Interface Design, Programming IDE and programming Language?

Should I use 
 - Glade+Anjuta+C++??
 - Glade+Anjuta+other language??
 - Eclipse+some language??
 - Mono???

Any suggestions welcome. I'm not the programming geek kind, I just need to write a program (an easy one) that works under Gnome/Ubuntu that has a good look and feel, and results are correct and well presented. This is for my job as a freelance.

My doubts grow if we talk about doing something like that instead of programming in C, C++... , using the Database Designer of OpenOffice, or using SQL+PHP+HTML(for interface design), regarding you need to install SQL and PHP on the machine you want to run it.

Another point is that I use two architectures, AMD64 and PowerPC, and would like the program/programs to run seamlesly on both.

Thanks a lot.
Best regards.
Xermán.

---

### Post by Metz on 2005-11-18
Excellent thread .... :)

I've been developing software commercially for over 20 years now...
(started young ;)). In the early days, it was basic, followed rapidly by
C. For business needs, Clipper was it in those days.

Later on....the evil empire got it's hands on me and I migrated to
Visual Basic 1.0....using, of all things, a Paradox database backend.
I've pretty much stuck with VB since then, in all it's varied guises
over the years....with some C++ where necessary.

The advent of web programming meant ASP, given the environment I was
working in. By now, I'd build up such a hatred of M$ products that I was
looking for a way out.

Having used Xenix in the early days (3GL stuff)...I started looking
around for open source products. I stumbled accross Ubuntu when it was
packaged on the front of a magazine. I'd recently trashed the XP
installation on my laptop, so I decided to jump in and installed Ubuntu,
with little or no problems really.

After spending some time getting used to the whole thing, I wanted to
begin programming, and set out to find some practical way of doing it.

My initial needs meant web programming. No contest...PHP. Peice of cake
to install....and even easier to program. Love it. Does everything I
need it to do, and PHP and MySQL make excellent bedfellows. After
getting my webserver, mailserver, etc all setup and running, I'd got my
first 'visible' results.

But then I was presented with a tougher choice. Which language/dev-env
for desktop stuff. I initally thought C/C++...but my first sample app
was a pain to get working....and the comiler fought me all the way. That
wasn't much fun.

Given the commercial environment I'm in, where MS is god (and, by no
coincidence, most of the money is ;)), I wanted to learn something
new...C#. But I wanted C# on Linux. Shopped around some more...and the
closest thing I could find was Mono.

Mono wasn't all that stable then....but I gave it a go and got pretty
much instant results. That's more like it :). So I've stuck with
it...and I'm now at the stage where I'm writing stuff at home (3D
modelling apps, to be specific) on Linux...which work great on Gnome
(GTK-Sharp-2.0) and taking the app into work and running it on XP, with
no problems :) Okay, the GTK stuff on Windows still looks mostly like
GTK....but I like, so no problem there :) Best of both worlds for me
:):)

I'm currently looking at adding Glade to the mix, but for the most part,
it's of little use given the nature of the application I'm writting.

I've become a huge supporter of Mono's efforts...and wish them all the
luck in the world.

---

### Post by Fermanagh on 2005-12-02
I have previously written programs in perl that use visual tcl for the GUI's. I am new to ubuntu and would like to install visual tcl, but so far I have been unable to have the Synaptic Packakge Manager point to the download site for visual tcl:

[http://vtcl.sourceforge.net/](http://vtcl.sourceforge.net/) 

I can download the debian package to my desktop, but not sure how to do the actual install of the package into my ubuntu environment. 

The visual tcl language is a great GUI maker and it works well with perl.

---

### Post by rooijan on 2005-12-06
If you want to prototype or just match some of the VB RAD concepts you have to try RealBasic.  When I last checked the Linux version was free.

---

### Post by JohnnyMast on 2005-12-06
Kde overall is coded in C++ where gnome and its GTK+ is more C. 

A funny not about GTK is there is a C++ development pack available called GTK-- :p
:)

---

### Post by cvmostert on 2005-12-09
I learned pascal in my studies, i am converting to C++ now, doing a course online... a free one ofcourse... quite fun going through all the stuff again...

reading a tutorial on c++ at cplusplus.com... or i think thats the site...
take care,
c

---

### Post by Salamander on 2005-12-10
[QUOTE=JohnnyMast]Kde overall is coded in C++ where gnome and its GTK+ is more C. 

A funny not about GTK is there is a C++ development pack available called GTK-- :p
:)[/QUOTE]
It's HP
[ gtkmm.org ]("http://gtkmm.org")
and very Important, the mail archive 
[http://mail.gnome.org/archives/gtkmm-list/]("http://mail.gnome.org/archives/gtkmm-list/")

greetz Maik

---

### Post by KEMitchell on 2005-12-23
[QUOTE=carlc]Glade looked interesting because my ultimate goal is to learn C but I am also intresested in Python.[/QUOTE]

If your goal is to learn C, learn C.

You probably won't want to program anything useful in it - designing GUIs without object-orientation (or worse, with fake/psudo OO manufactured by the programmers) is a serious exercise in unnecessary pain - but C remains the weapon of choice and linga franca of the computing world. Moving from C to a language like C++ (99% of commercial, boxed apps are written in some variant of C++) or Java (a great option for simple GUI projects - SWING is a godsend, also try SWT and MAKE SURE to try the free Eclipse IDE) is a big relief, and i think you'll find that once you UNDERSTAND object-oriented programming and KNOW C as a programming language things will pick up in pace. Essentially, learning C and moving forward in the timeline of computer languages is going to give you a really solid, strong base for working in any other language, rather than make you feature-and-quirk dependent.

C may not be that much fun, but it's the basis of all languages to follow in some manner or another. Things only get easier (unless you learn ASM) and you'll find it's time well spent crunching out seemingly worthless command-line novelties. That is, it will seem so when you get your 20/20 hindsight vision in a year or two.

For the basic question: good next language, good GUI-building support (intention to learn C notwithstanding): try Java 1.5, with the Eclipse IDE.

A little background information on myself, since all advice must be taken with a grain of salt (we call it background information):

[LIST=1]
[*]I began as a student in Visual Basic 6 (pre-OO VB, before .NET)
[*]Moved quickly into C++ for popular reasons
[*]Retreated quickly to C to make up for a lot of holes in my C++ education.
[*]Forced myself into some x86 ASM, to fill in holes in my C education.
[*]Moved on to Java, which is the closest thing the world has to a prgramming language which is actually enjoyable to work in (thanks also to the valiant work of the Eclipse project and IBM - what an IDE!)
[*]Tinkered in Jython for Java scripting, moved on to full-fledged Python
[*]Missed Java and wanted to go back, met halfway at Ruby
[*]Got a job, forced to write in Perl
[*]Went completely insane (i blame perl... and work), began typesetting in LaTeX
[*]Recovery: happily tinkering with the D programming language (Digital Mars)
[/LIST]

So basically:
If i want a throw-away shell script, it's in Perl. If i want a useful, small-scale GUI tool, it's in Java. If i'm being paid, chances are its in C++ or Ruby,Perl,JSP for web servers. If it's for me, chances are it's in whatever i felt like starting in at the time

---

### Post by HyperNewbie on 2005-12-25
[QUOTE=rufius]My approach would be a bit different compared to the Visual Basic method you're looking for but personally I've found that working with programs that don't require the GUI or don't teach the GUI initially helped me understand programming better. I personally wouldn't recommend starting out with the GUI builders, but would rather read some tutorials on say python, c, c++, or ruby.[/QUOTE]

same. i started qbasic. then vb but i didnt really like it. and now c++, is damn awesome because basically everything supports it! you got like 500000 libraries in front of you for you to learn and do crazy thigns with them

---

### Post by raha on 2006-01-03
Have a look at RealBasic as well, its Object Oriented and free for linux.
its easy to create GUI as well.

---

### Post by Howcomes on 2006-02-01
I'm actually taking a course in Visual Basic programming (which is like 2nd nature to me by now - which is why im taking the course :P I know it so well i might as well have a piece of paper stating so)

But i as well am looking to branch out into a more powerful programming language, I've dabbled in C, C++, Pascal, ASM, Perl. The only two i ever got anywhere with were Perl and Pascal. I havent read this entire thread yet, but from the sounds of it i might try Glade :P

I started off with QuickBasic back in my BBS days, learning that was a breeze and quickly moved to Pascal where i stayed only briefly and then I stumbled across Visual Basic 3.0, within 2 months i had my hands on a copy of Visual Studio 6.0 where i refined my Visual Basic programming skills and have since been coding in it. Coincidently at the same time i procured a copy of W32DASM and HIEW and learned some ASM from a reverse engineering standpoint and refined my skills in that somewhat, still need some work with real-time debugging thou.

Anyway....long story short I think i wanna learn C/C++ :P I'm pretty sure you have to be insane to at least some degree to program in ASM, having attempted it, its just....nuts.

---

### Post by ZylGadis on 2006-02-02
If you want to do Java, you could also consider NetBeans - all Java, true Java, far ahead of everyone in terms of no-code-writing GUI designers (a concept I despise but obviously you like). NB5.0 final is out today \\:D/ 

I don't understand all the hype around Eclipse and its twisted graphical libraries that break the Java spirit, but oh well. This is not the place for a flamewar.

---

### Post by Metz on 2006-02-02
<deleted post>

---

### Post by terje on 2006-02-07
If you want to learn how to program: GO WITH JAVA
It is easy, very widespread and has a LOT of good books, tutorials and so on. And if you get good at it you might be able to earn some money with it. It is also the preferred learning language for nearly all adademic institutions out there.

For an IDE I would recommend Netbeans, as I find it a lot easier to use than Eclipse.

If your goal is to develop native applications for Linux then you should probably go with something else like python or any of the other stuff discussed previously in this thread.

But don't forget: When you write a program in Java it will run on Linux.
And Windows
And Mac
And so on....

And you can create programs for your cellphone which is extremely fun to do. The satisfaction...

Just my two NOK.

---

### Post by bartbes on 2006-02-07
I love c++ but only terminal programs are cross-platform (doesn't matter for me I can't program GUI's :p )

---

### Post by theemahn on 2006-02-20
I know $ms Visual Basic .net on vb side actually have been programing since vb 3 days as far as windows before that qbasic as well as basic on a C64 wonder if they had a pc then?  probably did but i was not in the pc world, I would like to contribute but dont know where to start only been running ubuntu 2 weeks I have taken the time to learn c bought a book "learn c in 14 days" none the less in chapter 1 it said if you know basic pretty much hang it up, I do know PHP and I have heard PHP is very similar to c.  I also know some ASM due to C64 days what would u suggest i use as a development environment?

What I can see from a programmers eye if you want to think of it this way is gtk for example kinda like a dynamic link library to windows.  Main reason of concern is I do want to contribute to Xgl it shows promise and probably will require knowlege of c.  If there is one thing I do its learn fast perhaps I should have ignored if you know basic stop now chapter 1.  The reason they gave is I will take the time to think and compare it with VB or basic and to be honest I did when writing the common hello world program :)

any input is greatly appriciated thanx good or otherwise

---

### Post by Plank117 on 2006-02-21
Java. It's great because it's cross platform and you get to jump right into GUI if you know your fundamentals (flow control, etc). Also, I've found that GUI WYSIWYGs tend to be confusing and difficult to use if you don't understand what you're actually doing (in code), and they just get in the way if you want to do something simple. When my cellphone "breaks" I'm making sure my next one's a Java phone, because I've written all sorts of cool stuff for my buddy's phone, and no joke, I even met my girlfriend because he showed her a little app I wrote for his phone. (FYI, she's not just hanging around because I can make her life easier. We got into a conversation and discovered we both like to snowboard.) Java's a great language in all aspects. But most importantly, chicks dig Java!

---

### Post by MichaelZ on 2006-03-11
Hello,

Personally, I like C++. ISO C++ I mean :D. I do not want to begin a war between C++ and Java, but IMHO C++ is better programming language (I have developed in Java for some years). D seems promising.

Anyway, I think that what it is important is to be flexible :D and not to stick to a specific language, but to be open.

Best wishes,
Michael

---

### Post by Ozitraveller on 2006-03-11
[QUOTE=carlc]I have taken two classes in Visual Basic. I did not learn a lot and remember even less because it has been a few years since I have taken them.

Anyway, I would like to move on to a different programming language and would like to begin by using a program similar to Visual Studio in that you can use a GUI to create menus, text boxes, drop-down menus, etc and add code to them.

What would be a good language to learn and a good program to use?[/QUOTE]

I mainly use VB6 and C# (sorry I don't like VB.net, but that's another story!), plus a bunch of other languages to a lesser extent. 

Currectly I'm learning Python, IronPython is currently under development for VS at GotDotNet:
[http://www.gotdotnet.com/workspaces/workspace.aspx?id=ad7acff7-ab1e-4bcb-99c0-57ac5a3a9742](http://www.gotdotnet.com/workspaces/workspace.aspx?id=ad7acff7-ab1e-4bcb-99c0-57ac5a3a9742).
So it should have all the bits that come with .Net as well as Python 2.4.

I'm waiting for Mono implement Winforms : [http://www.mono-project.com/WinForms](http://www.mono-project.com/WinForms).

You might find this useful too:
Using Visual Studio to develop with Mono
[http://tirania.org/blog/archive/2006/Feb-25.html](http://tirania.org/blog/archive/2006/Feb-25.html)

FAQ: Winforms:
[http://www.mono-project.com/FAQ:_Winforms](http://www.mono-project.com/FAQ:_Winforms)

This is from the FAQ
> 
Do you have an estimate for when Windows.Forms will be released?
The plan currently is aimed at Q2/2006.


Gui Toolkits:
[http://www.mono-project.com/Gui_Toolkits](http://www.mono-project.com/Gui_Toolkits)

Hope this helps

---

### Post by sharperguy on 2006-03-13
Ok, i have decided (not from reading this topic though) to try and use glade+gtkmm+c++.

However i would like a/some tutorial(s) on how to do this.

I know a bit about using c++ and can write console apps and i can use glade its just knowing how to make it c++ and what to put in to made it  edit the GTK GUI i dont know about.

Thanks


PS: I love the fact that no-ones even commented on the realBASIC idea :)

---

### Post by rplantz on 2006-03-14
I have seen many comments about the best language to start with when learning how to program. In my experience, you need to learn several languages before you can start seeing the general concepts.

I taught computer science at a university for 21 years. When I first started (1983), we taught in Pascal. After several years we switched to C. I was the first one to teach our introduction to programming class in C. It was a 4-unit class.

At the same time, I offered a 2-unit class in C for those students who had already taken the intro class in Pascal.

The classes were fairly small. As I recall, about 40 in the intro class and 20 in the language-only one. Both had a lab component, which I also taught. There were no teaching assistants.

I used the same book for both classes, thinking that the second group of students could skim quickly over the first few chapters and we could concentrate on the more advanced material in the second half of the book. Wrong! It was like a totally new experience to these students. I was amazed at how few of the concepts carried across the two languages for them.

Basically, I ended up doing the same thing in both classes. The 2-unit class did not need to relearn things like how to use an editor, how to compile, etc., so they did move quite a bit faster than the 4-unit class.

Caveat: The numbers are very small, so this has not statistical significance. But all of my colleagues have remarked about how difficult it is for students to learn a second language. And I also admit that I'm not the person to judge how much this may have been due to my teaching capabilities.

---

### Post by TitusDalwards on 2006-03-31
GTK+ is more interesting for me  sometimes i use it but generally i write codes in Glade

---

### Post by jimbo2150 on 2006-04-04
Anyone know of any good Coldfusion (CFML) apps.

I have used Dreamweaver a lot, but (if possible) am looking to switch my machine at work from WinXP to Ubuntu. :)

I am primarily a PHP programmer, but have to use CFML at work. Are there any web development programs that support Coldfusion 5+?

It would have to have FTP support too.

Ran a few searches and came up empty handed.
Thanks for any programs.

---

### Post by SreckoMicic on 2006-04-15
I know that eclipse has plugin for coldfusion. But I'm not sure about ftp access. Never used it.

---

### Post by unbuntu on 2006-04-15
I like python, but haven't gone into GUI programming in python yet.  For GUI I usually use Java Swing or even .NET Windows Forms

---

### Post by bhar on 2006-04-18
Hi,

I always prefer the VB/VB.net as frond end, easy to learn. I developed the full accounting module of ERP domain using one VB.Net book titled: "Database programming using vb.net and sql server (C/s version)". it works fine for me.

This book is very useful for people who want to develop database app. It teaches the domain knowledge of Accounting.

Regards
bhar

---

### Post by microsurfer on 2006-04-18
Hey buddy dont put yourself in hardwork, If you are reluctant to program in visual basic. y not change the track. I advise you to join internet programming, learn HTML, VBScript, ASP, PHP, very easy learn and quite effective to use and program in. I develop a site [www.microglobe.co.uk](www.microglobe.co.uk) using php, HTML, MySQL ,,,, its an oscommerce templete, good luck](*,)

---

### Post by javarunner on 2006-08-10
Java is a great language for just about anything, and the GUI/IDE I use, and it most everyone else uses in the Java community, is Eclipse.:D

---

