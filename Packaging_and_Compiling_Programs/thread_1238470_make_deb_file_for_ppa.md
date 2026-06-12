---
title: "make deb file for ppa"
date: 2009-08-12
forum: Packaging and Compiling Programs
---

### Post by rubenverweij on 2009-08-12
Hi all,

I have created a small program I want to put in a ppa in launchpad.
I've read the Ubuntu Packaging Guide and the GNU Make documentation and I'm confused well and proper. :(
To compile the source, I use: 
```
g++ -o executable source.cpp `pkg-config --cflags gtk+-2.0 --libs libxml-2.0`
```
Which files should I make before I can continue to the Ubuntu Packaging Guide? I find the GNU documentation very confusing to read, but there was something about autoconf, automake and autoheader. Should I use these?
Sorry for my ignorance, but I've looked all over the internet and all guides I follow result in errors (probably due to the fact it is written in C++ and it uses gtk+ and libxml).

Could anyone give me directions on how to continue?

Thanks in advance,

Ruben

---

### Post by _sluimers_ on 2009-09-01
Have you figured it out already?

If not, as far as I know they don't want a deb file, but a sources.change file, a .tar.gz and a dsc file.

I use:
dh_make -s -n -e <my e-mail adress>
debuild -S -k<my-key>
and dput <ppa name> <app name>_<app version>_source.changes

I'm still learning myself as I haven't figured out why my executable isn't going into my package, but I've managed to get an empty package in the PPA.

---

### Post by rubenverweij on 2009-09-01
Thanks for your reply.
No, I haven't, but I'll try your solution. Maybe that'll work, I namely did succeed in uploading package, but Launchpad couldn't compile it. Maybe it will with these commands.

---

### Post by Brandon Williams on 2009-09-01
See [here](http://ubuntuforums.org/showpost.php?p=7881137&postcount=4) for my response to another similar thread.

---

### Post by rubenverweij on 2009-09-06
Thanks for your answer Brandon.
I have followed your guide and got the package uploaded to my ppa. One slight problem though: it fails to build.
Could you please tell me where I need to specify the dependencies and how?
Thanks in advance!
This is the relevant part of the build log:
```
g++ -Wall -c -o MainWindow.o MainWindow.cpp `pkg-config gtkmm-2.4 libxml++-2.6 --cflags --libs` -lboost_regex-mt
/bin/sh: pkg-config: not found
In file included from MainWindow.cpp:23:
studentsPlanner.h:26:23: error: gtkmm/box.h: No such file or directory
studentsPlanner.h:27:27: error: gtkmm/toolbar.h: No such file or directory
studentsPlanner.h:28:30: error: gtkmm/toolbutton.h: No such file or directory
studentsPlanner.h:29:37: error: gtkmm/separatortoolitem.h: No such file or directory
studentsPlanner.h:30:25: error: gtkmm/table.h: No such file or directory
studentsPlanner.h:31:26: error: gtkmm/window.h: No such file or directory
studentsPlanner.h:32:25: error: gtkmm/stock.h: No such file or directory
studentsPlanner.h:33:28: error: gtkmm/notebook.h: No such file or directory
studentsPlanner.h:34:37: error: gtkmm/filechooserdialog.h: No such file or directory
studentsPlanner.h:35:30: error: gtkmm/filefilter.h: No such file or directory
studentsPlanner.h:36:25: error: gtkmm/label.h: No such file or directory
studentsPlanner.h:37:28: error: gtkmm/eventbox.h: No such file or directory
studentsPlanner.h:38:29: error: gtkmm/treemodel.h: No such file or directory
studentsPlanner.h:39:28: error: gtkmm/treeview.h: No such file or directory
studentsPlanner.h:40:29: error: gtkmm/liststore.h: No such file or directory
studentsPlanner.h:41:34: error: gtkmm/scrolledwindow.h: No such file or directory
studentsPlanner.h:42:33: error: gtkmm/messagedialog.h: No such file or directory
studentsPlanner.h:46:27: error: boost/regex.hpp: No such file or directory
studentsPlanner.h:48:31: error: libxml++/libxml++.h: No such file or directory
In file included from MainWindow.cpp:23:
studentsPlanner.h:55: error: 'xmlpp' has not been declared
studentsPlanner.h:55: error: expected '{' before 'DomParser'
studentsPlanner.h:56: error: invalid type in declaration before '{' token
studentsPlanner.h:56: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x
studentsPlanner.h:57: error: expected primary-expression before 'public'
studentsPlanner.h:57: error: expected '}' before 'public'
studentsPlanner.h:57: error: expected ',' or ';' before 'public'
studentsPlanner.h:59: error: declaration of '~XmlParser' as non-member
studentsPlanner.h:67: error: expected unqualified-id before 'protected'
studentsPlanner.h:69: error: ISO C++ forbids declaration of 'xmlpp' with no type
studentsPlanner.h:69: error: expected ',' or '...' before '::' token
studentsPlanner.h:70: error: expected declaration before '}' token
make[1]: *** [MainWindow.o] Error 1
make[1]: Leaving directory `/build/buildd/students-planner-0.1alpha2'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```

---

### Post by _sluimers_ on 2009-09-06
In the conrtol file:

Here's an example:
```

Source: ika
Section: misc
Priority: extra
Maintainer: Rogier M. Sluimers <r.m.sluimers@gmail.com>
Build-Depends: debhelper (>= 7), corona, libaudiere-dev, libaudiere-1.9.4, libwxgtk2.8-0, libwxgtk2.8-dev, libsdl1.2-dev, libwxgtk2.6-0, libwxgtk2.6-dev, zlib1g-dev, python-wxgtk2.6, python-wxgtk2.8, python2.6-dev
Standards-Version: 3.8.0

Package: ika
Architecture: any
Depends: 
Description: ika is a Python based Multi-Platform 2D (RPG) GameMaker. 
 This is the core engine of ika.
 Visit ika's homepage at http://ika.sf.net

```

---

### Post by rubenverweij on 2009-09-06
Okay, thanks, that solved part of my problem!
The only thing is, it still doesn't build. It has no authorization to install it into /usr/bin, should I install it to $(DESTDIR) instead? I'm almost there I think.... :D
Thanks in advance!
Here is the log:
```
make[1]: Entering directory `/build/buildd/students-planner-0.1alpha2'
g++ -Wall -c -o MainWindow.o MainWindow.cpp `pkg-config gtkmm-2.4 libxml++-2.6 --cflags --libs` -lboost_regex-mt
g++ -Wall -c -o Marks.o Marks.cpp `pkg-config gtkmm-2.4 libxml++-2.6 --cflags --libs` -lboost_regex-mt
g++ -Wall -c -o studentsPlanner.o studentsPlanner.cpp `pkg-config gtkmm-2.4 libxml++-2.6 --cflags --libs` -lboost_regex-mt
g++ -Wall -c -o XmlParser.o XmlParser.cpp `pkg-config gtkmm-2.4 libxml++-2.6 --cflags --libs` -lboost_regex-mt
g++ -o /usr/bin/students-planner MainWindow.o Marks.o studentsPlanner.o XmlParser.o `pkg-config gtkmm-2.4 libxml++-2.6 --cflags --libs` -lboost_regex-mt
/usr/bin/ld: cannot open output file /usr/bin/students-planner: Permission denied
collect2: ld returned 1 exit status
make[1]: *** [students-planner] Error 1
make[1]: Leaving directory `/build/buildd/students-planner-0.1alpha2'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```

---

### Post by Brandon Williams on 2009-09-06
Your build target is using /usr/bin/students-planner is that target for gcc. The build target for your program should be putting the binary in the build directory, not in /usr/bin/. You should add an install target to your Makefile that will install the binary into $(DESTDIR)/usr/bin. See the other thread I referred to in my previous post for an example of what this would look like.

---

### Post by _sluimers_ on 2009-09-06
So part of your Makefile should look similar to this:

```

DESTDIR = debian/hello-world

hello-world: hello-world.o

install: hello-world
	install hello-world $(DESTDIR)/usr/bin

clean:
	rm -f hello-world hello-world.o

```

---

### Post by rubenverweij on 2009-09-06
Thanks a lot Brandon, it successfully builds now! :popcorn:

---

### Post by Brandon Williams on 2009-09-06
> **_sluimers_ said:**
> So part of your Makefile should look similar to this:

```

DESTDIR = debian/hello-world

hello-world: hello-world.o

install: hello-world
	install hello-world $(DESTDIR)/usr/bin

clean:
	rm -f hello-world hello-world.o

```

Just a clarification ...

Your Makefile will typically not specify DESTDIR directly. Instead, with a straight Makefile and no configure script, you will usually allow the Makefile to default to DESTDIR being empty. This allows debuild to set DESTDIR when it's building the package, while also allowing the Makefile to work correctly when run on its own.

---

### Post by rubenverweij on 2009-09-07
Yes, I figured that out too... :)
Thanks, though, for your help, it works perfectly now.

---

