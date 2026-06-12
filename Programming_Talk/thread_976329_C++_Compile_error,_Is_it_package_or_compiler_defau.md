---
title: "C++ Compile error, Is it package or compiler default settings?  gtkmm.h"
date: 2008-11-09
forum: Programming Talk
---

### Post by Jonas thomas on 2008-11-09
Hi,
I know enough in C++ to be dangerous so I thought I ask for opinions here first before I really hose something..
I think I understand what is going on, but not why it's happening in the first place, nor the "correct" way to fix it.


I'm running "make" trying to compile this package and I'm getting this error:
```
jonas@Ubuntu4:~/gtkmmocascade$ make
make  all-recursive
make[1]: Entering directory `/home/jonas/gtkmmocascade'
Making all in src
make[2]: Entering directory `/home/jonas/gtkmmocascade/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.cpp; \
	then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
main.cpp:1:19: error: gtkmm.h: No such file or directory
In file included from main.cpp:2:
./gtkmmocascade.h:2:21: error: gtkglmm.h: No such file or directory
./gtkmmocascade.h:12:38: error: AIS_InteractiveContext.hxx: No such file or directory
......... and so on
 
```

The error is straight forward enough... sortof....
The issue is that I have gtkmm.h but the compiler doesn't know where it is.
```
jonas@Ubuntu4:~/gtkmmocascade/src$ locate gtkmm.h
/usr/include/gtkmm-2.4/gtkmm.h
```


Just for fun, I changed some code in main.cpp to see what would happen.
From:
```
#include <gtkmm.h>
To:
#include <gtkmm-2.4/gtkmm.h>
```

This got rid of the first error(like I expected) and generated the slew other errors.
So the compiler needs to look in the /usr/include/gtkmm-2.4/ directory but isn't being told to do that..
Is the fault in the compiler default settings (my money is on that one) or the configure.ac file?

---

### Post by dwhitney67 on 2008-11-09
IMHO, your second approach, using #include <gtkmm-2.4/gtkmm.h>, is the correct approach.

Alternatively, you could have specified the path /usr/include/gtkmm-2.4 using the -I option.

P.S.  You should check if there is a symbolic link to gtkmm-2.4 in the /usr/include directory (e.g. gtkmm/).

---

### Post by Jonas thomas on 2008-11-09
> **dwhitney67 said:**
> IMHO, your second approach, using #include <gtkmm-2.4/gtkmm.h>, is the correct approach.

Alternatively, you could have specified the path /usr/include/gtkmm-2.4 using the -I option.

P.S.  You should check if there is a symbolic link to gtkmm-2.4 in the /usr/include directory (e.g. gtkmm/).

I was leaning that way too, but now think that I something is screwed up in the package either in the configure.ac or src/makefile.am package

I need work through this thread here: [http://ubuntuforums.org/showthread.php?p=5895821]("http://ubuntuforums.org/showthread.php?p=5895821") and see if it helps.... Back in a few minutes

---

### Post by samjh on 2008-11-09
Have you got the right compiler flags?  (Assuming that the make file is yours.)

What does this command show?
```
pkg-config --cflags --libs gtkmm-2.4
```Because those are the flags you need to compile gtkmm programs.

As for your include headers, #include <gtkmm.h> is the correct one if you're using the right compiler flags.  It looks like you mightn't have read the documentation [here](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-basics.html). ;)

---

### Post by Jonas thomas on 2008-11-09
> **Jonas thomas said:**
> I was leaning that way too, but now think that I something is screwed up in the package either in the configure.ac or src/makefile.am package

I need work through this thread here: [http://ubuntuforums.org/showthread.php?p=5895821]("http://ubuntuforums.org/showthread.php?p=5895821") and see if it helps.... Back in a few minutes

So...
I added a 
PKG_CHECK_MODULES([GTKMM], [gtkmm-2.4 >= 2.4.0])
to configure.ac as was suggested

In addition, went to src/Makefile.am
and made a couple of additions
```
bin_PROGRAMS = gtkmmocascade
gtkmmocascade_SOURCES = gtmmocascade.h main.cpp gtmmocascade.cpp MakeBottle.cpp 
[B][I]gtkmmocascade_CXXFLAGS = $(GTKMM_CFLAGS)
gtkmmocascade_LDADD = $(GTKMM_LIBS)[/I][/B]

```

I ran 
```
jonas@Ubuntu4:~/gtkmmocascade$ autoreconf --install
jonas@Ubuntu4:~/gtkmmocascade$ ./configure

```
before running the make... and it seems to have had a positive effect.

Now the next error is:
```
jonas@Ubuntu4:~/gtkmmocascade$ make
make  all-recursive
make[1]: Entering directory `/home/jonas/gtkmmocascade'
Making all in src
make[2]: Entering directory `/home/jonas/gtkmmocascade/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/atk-1.0   -g -O2 -MT gtkmmocascade-main.o -MD -MP -MF ".deps/gtkmmocascade-main.Tpo" -c -o gtkmmocascade-main.o `test -f 'main.cpp' || echo './'`main.cpp; \
	then mv -f ".deps/gtkmmocascade-main.Tpo" ".deps/gtkmmocascade-main.Po"; else rm -f ".deps/gtkmmocascade-main.Tpo"; exit 1; fi
In file included from main.cpp:2:
./gtkmmocascade.h:2:21: error: gtkglmm.h: No such file or directory
./gtkmmocascade.h:12:38: error: AIS_InteractiveContext.hxx: No such file or dire
```

Need to research this one a little more.... Back in a while....

---

### Post by Jonas thomas on 2008-11-09
> **samjh said:**
> Have you got the right compiler flags?  (Assuming that the make file is yours.)

What does this command show?
```
pkg-config --cflags --libs gtkmm-2.4
```Because those are the flags you need to compile gtkmm programs.

As for your include headers, #include <gtkmm.h> is the correct one if you're using the right compiler flags.  It looks like you mightn't have read the documentation [here](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-basics.html). ;)

Actually, the package is not mine.. I think the guy who made this package was a newbie like me.  I've read so much documentation over the past few weeks it's making my head ache.. Like I said, I'm just starting think to know what I'm doing, so this make me really dangerous.

Your right that I don't have the correct compiler flags...
I fixed the problem and I'm moving on to the next...
I'm having a similar issue with gtkglmm.h 
The thing that's different is I need add multiple sources to the CXXFLAGS in the src/Makefile.am file. I found some [info]("http://www.gnu.org/software/automake/manual/html_node/Flag-Variables-Ordering.html") on how to do that.  
Actually, I think I just had a lightbulb go on has far as far whats going on with PKG_CHECK_MODULES in the configure.ac file.
```
jonas@Ubuntu4:~/gtkmmocascade$ locate gtkglmm.h
/usr/include/gtkglextmm-1.2/gtkglmm.h
```

revised configure.ac
```
AC_INIT([gtkmmopencascade],[1.0],[blah@blahblah.com])
AM_INIT_AUTOMAKE([-Wall -Werror foreign])
AC_PROG_CXX
AC_CONFIG_HEADERS([config.h])
PKG_CHECK_MODULES([GTKMM], [gtkmm-2.4 >= 2.4.0])
PKG_CHECK_MODULES([JTTESTTHEORY], [gtkglextmm-1.2 >= 1.2.0])
AC_CONFIG_FILES([
Makefile 
src/Makefile
])
AC_OUTPUT

```

revised src/Makefile.am
```
bin_PROGRAMS = gtkmmocascade
gtkmmocascade_SOURCES = gtmmocascade.h main.cpp gtmmocascade.cpp MakeBottle.cpp 
gtkmmocascade_CXXFLAGS = $(GTKMM_CFLAGS) $(JTTESTTHEORY_CFLAGS)
gtkmmocascade_LDADD = $(GTKMM_LIBS)  $(JTTESTTHEORY_LIBS)
```

I think what I did worked(I think?) but I'm still getting errors....
I need to digest the latest (unless someone sees something obvious)

```
jonas@Ubuntu4:~/gtkmmocascade$ make
make  all-recursive
make[1]: Entering directory `/home/jonas/gtkmmocascade'
Making all in src
make[2]: Entering directory `/home/jonas/gtkmmocascade/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/atk-1.0   -I/usr/include/gtkglextmm-1.2 -I/usr/lib/gtkglextmm-1.2/include -I/usr/include/gtkglext-1.0 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/lib/gtkglext-1.0/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/cairomm-1.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/atk-1.0 -I/usr/include/atkmm-1.6   -g -O2 -MT gtkmmocascade-main.o -MD -MP -MF ".deps/gtkmmocascade-main.Tpo" -c -o gtkmmocascade-main.o `test -f 'main.cpp' || echo './'`main.cpp; \
	then mv -f ".deps/gtkmmocascade-main.Tpo" ".deps/gtkmmocascade-main.Po"; else rm -f ".deps/gtkmmocascade-main.Tpo"; exit 1; fi
In file included from main.cpp:2:
./gtkmmocascade.h:12:38: error: AIS_InteractiveContext.hxx: No such file or directory
./gtkmmocascade.h:14:24: error: V3d_View.hxx: No such file or directory
./gtkmmocascade.h:15:26: error: V3d_Viewer.hxx: No such file or directory
./gtkmmocascade.h:17:35: error: Geom_BSplineSurface.hxx: No such file or directory
./gtkmmocascade.h:19:37: error: AIS_InteractiveObject.hxx: No such file or directory
./gtkmmocascade.h:20:40: error: Graphic3d_NameOfMaterial.hxx: No such file or directory
./gtkmmocascade.h:22:28: error: TopoDS_Shape.hxx: No such file or directory
./gtkmmocascade.h:23:25: error: AIS_Shape.hxx: No such file or directory
./gtkmmocascade.h:25:43: error: Handle_V3d_OrthographicView.hxx: No such file or directory

```

Actually same kind of problem
```
jonas@Ubuntu4:~/gtkmmocascade$ locate AIS_InteractiveContext.hxx
/usr/include/opencascade/AIS_InteractiveContext.hxx
```
[Similar but different]. I can't use PKG_CHECK_MODULES for opencascade since there is no ".pc" file for this package(as far as I'm aware).....

---

