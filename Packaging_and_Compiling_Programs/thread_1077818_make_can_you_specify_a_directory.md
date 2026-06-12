---
title: "make: can you specify a directory?"
date: 2009-02-22
forum: Packaging and Compiling Programs
---

### Post by dodle on 2009-02-22
When using "make" to create executables, is there a way to specify a directory so that the executables don't end up in the source's directory?

I've tried "make --help" to try and figure it out, but I can't.

**Edit:** Whoops!  I didn't realize there was a specific forum for this issue.  Sorry.

---

### Post by monkeyking on 2009-02-22
I don't know,
but I don't think theres a build in argument for this.

But you can easily do it your self,
this Makefile should give you an idea.

args like 'libs' 'COMPILE'
can be changedat make  time simply by
make LIBS=-lm

good luck
```

LIBS = -lpthread
COMPILE = gcc
OPTFLAGS = -Wall -O2
LDFLAGS = -L/usr/lib -lform -lmenu -lpanel -lncurses -lm
MKDIR = /bin/mkdir -p
INSTALL = /bin/cp
SETRX = /bin/chmod 755
SETR = /bin/chmod 644
DESTROOT = /
BINDIR = $(DESTROOT)/usr/bin/
SBINDIR = $(DESTROOT)/usr/sbin/
MAN1DIR = $(DESTROOT)/usr/man/man1/
MAN8DIR = $(DESTROOT)/usr/man/man8/

all: tmon tmond

tmon: tmon.c
        $(COMPILE) $(OPTFLAGS) -o tmon tmon.c $(LDFLAGS)

tmond: tmond.c
        $(COMPILE) $(OPTFLAGS) -o tmond tmond.c $(LIBS)

install: install-bin install-man install-man install-client install-server

install-bin: tmon tmond
	$(MKDIR) $(BINDIR)
	$(INSTALL) tmon $(BINDIR)
	$(SETRX) $(BINDIR)/tmon
	$(MKDIR) $(SBINDIR)
	$(INSTALL) tmond $(SBINDIR)
	$(SETRX) $(SBINDIR)/tmond


install-man:
	$(MKDIR) $(MAN1DIR)
        $(INSTALL) tmon.1 $(MAN1DIR)
	$(SETR) $(MAN1DIR)/tmon.1
        $(MKDIR) $(MAN8DIR)
        $(INSTALL) tmond.8 $(MAN8DIR)
	$(SETR) $(MAN8DIR)/tmond.8

install-client: tmon
	$(MKDIR) $(BINDIR)
        $(INSTALL) tmon $(BINDIR)
	$(SETRX) $(BINDIR)/tmon
        $(MKDIR) $(MAN1DIR)
	$(INSTALL) tmon.1 $(MAN1DIR)
	$(SETR) $(MAN1DIR)/tmon.1

install-server: tmond
	$(MKDIR) $(SBINDIR)
	$(INSTALL) tmond $(SBINDIR)
	$(SETRX) $(SBINDIR)/tmond
        $(MKDIR) $(MAN8DIR)
	$(INSTALL) tmond.8 $(MAN8DIR)
	$(SETR) $(MAN8DIR)/tmond.8

clean:
	rm -f tmon tmond



```

---

### Post by Ptero-4 on 2009-02-22
There's a way to make a target "install"(IANAP) which puts all the binary stuff (executables, libraries, shared parts of the software, documentation, etc) in their respective places in the filesystem outside of the source directory.

---

### Post by Simian Man on 2009-02-22
make just does exactly what the makefile tells it to do, there's nothing about make that's even specific to compiling programs.  Are you using a pre-written makefile to install software from source?  Or are you having trouble writing your own makefiles?

---

### Post by dodle on 2009-02-22
I'm using a pre-written makefile.  I don't have any experience with them.  I'll guess I'll have to study up.

---

### Post by bsharp on 2009-02-22
If it uses autoconf, there should be an argument called "prefix" that allows you to set a directory. E.G:

```
./configure --prefix=/usr/bin
make
make install
```

---

### Post by monkeyking on 2009-02-22
> **Ptero-4 said:**
> There's a way to make a target "install"(IANAP) which puts all the binary stuff (executables, libraries, shared parts of the software, documentation, etc) in their respective places in the filesystem outside of the source directory.

You might be thinking about the Makefiles generated with autoconf and friends.

If the original poster is using a autoconf and automake Makfile,
the default is --prefix.
But he should use it with ./configure and not ./Makefile

---

### Post by dwhitney67 on 2009-02-22
> **monkeyking said:**
> I don't know,
but I don't think theres a build in argument for this.

But you can easily do it your self,
this Makefile should give you an idea.

args like 'libs' 'COMPILE'
can be changedat make  time simply by
make LIBS=-lm

good luck
```

LIBS = -lpthread
COMPILE = gcc
OPTFLAGS = -Wall -O2
LDFLAGS = -L/usr/lib -lform -lmenu -lpanel -lncurses -lm
MKDIR = /bin/mkdir -p
INSTALL = /bin/cp
SETRX = /bin/chmod 755
SETR = /bin/chmod 644
DESTROOT = /
BINDIR = $(DESTROOT)/usr/bin/
SBINDIR = $(DESTROOT)/usr/sbin/
MAN1DIR = $(DESTROOT)/usr/man/man1/
MAN8DIR = $(DESTROOT)/usr/man/man8/

all: tmon tmond

tmon: tmon.c
        $(COMPILE) $(OPTFLAGS) -o tmon tmon.c $(LDFLAGS)

tmond: tmond.c
        $(COMPILE) $(OPTFLAGS) -o tmond tmond.c $(LIBS)

install: install-bin install-man install-man install-client install-server

install-bin: tmon tmond
	$(MKDIR) $(BINDIR)
	$(INSTALL) tmon $(BINDIR)
	$(SETRX) $(BINDIR)/tmon
	$(MKDIR) $(SBINDIR)
	$(INSTALL) tmond $(SBINDIR)
	$(SETRX) $(SBINDIR)/tmond


install-man:
	$(MKDIR) $(MAN1DIR)
        $(INSTALL) tmon.1 $(MAN1DIR)
	$(SETR) $(MAN1DIR)/tmon.1
        $(MKDIR) $(MAN8DIR)
        $(INSTALL) tmond.8 $(MAN8DIR)
	$(SETR) $(MAN8DIR)/tmond.8

install-client: tmon
	$(MKDIR) $(BINDIR)
        $(INSTALL) tmon $(BINDIR)
	$(SETRX) $(BINDIR)/tmon
        $(MKDIR) $(MAN1DIR)
	$(INSTALL) tmon.1 $(MAN1DIR)
	$(SETR) $(MAN1DIR)/tmon.1

install-server: tmond
	$(MKDIR) $(SBINDIR)
	$(INSTALL) tmond $(SBINDIR)
	$(SETRX) $(SBINDIR)/tmond
        $(MKDIR) $(MAN8DIR)
	$(INSTALL) tmond.8 $(MAN8DIR)
	$(SETR) $(MAN8DIR)/tmond.8

clean:
	rm -f tmon tmond



```

The Makefile above could be made a little better.

First, if the user specifies a path for DESTDIR that does not exist, then the Makefile ought to create it.  Thus the MKDIR statements should include the -p option.

Second, do not use the 'cp' command, followed by the 'chmod' to install a file.  Just use the 'install' command instead, and specify the appropriate file permissions.

Lastly, $(COMPILE) can be replaced with $(CC); the 'rm -f' can be replaced with a $(RM); and wherever possible, use the built-in symbols for referencing sources and targets rather than spelling them out.

Here's a Makefile that I occasionally use as a template:
```

EXE       = testing

CPP_SRCS  = Foo.cpp Poly.cpp Testing.cpp
C_SRCS    = Function.c

CPP_OBJS  = $(CPP_SRCS:.cpp=.o)
C_OBJS    = $(C_SRCS:.c=.o)

CXXFLAGS  = -Wall -ansi -pedantic
CFLAGS    = -Wall -ansi -pedantic -D_GNU_SOURCE -std=gnu99

# Define header file paths
INCPATH   = -I./

# Define the -L library path(s)
LDFLAGS   =

# Define the -l library name(s)
LIBS      =

#
# Below this line, generally not much needs to be changed.
#

DEP_FILE  = .depend


.PHONY = all clean distclean


# Main entry point
#
all: depend $(EXE)


# For linking object file(s) to produce the executable
#
$(EXE): $(C_OBJS) $(CPP_OBJS)
	@echo Linking $@
	@$(CXX) $^ $(LDFLAGS) $(LIBS) -o $@


# For compiling source file(s)
#
.cpp.o:
	@echo Compiling $<
	@$(CXX) -c $(CXXFLAGS) $(INCPATH) $<

.c.o:
	@echo Compiling $<
	@$(CC) -c $(CFLAGS) $(INCPATH) $<


# For cleaning up the project
#
clean:
	$(RM) $(CPP_OBJS) $(C_OBJS)

distclean: clean
	$(RM) $(EXE)
	$(RM) $(DEP_FILE)


# For determining source file dependencies
#
depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Generating dependencies in $@
	@-$(CXX) -E -MM $(CXXFLAGS) $(INCPATH) $(CPP_SRCS) >> $(DEP_FILE)
	@-$(CC) -E -MM $(CFLAGS) $(INCPATH) $(C_SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```

---

### Post by dodle on 2009-02-22
Could someone help me with this makefile?  I am trying to cross-compile gnome-games for Windows.  The one that I am most concerned about is mahjongg.  I can successfully make the executables/binaries (which is more appropriate?) with mingw32, but mahjongg cannot find the pixmaps at execution time.  Here is the error:> **Could not load tile set**

Unable to render file:
'Failed to open file '/usr/local/share/pixmaps/mahjongg/postmodern.svg': No such file or directory'

Please check that Mahjongg is installed correctly.

I'd like the pixmaps to be located in:  (mahjongg's directory)/tilesets

Here is gnome-games makefile:```
# Makefile.in generated by automake 1.10.1 from Makefile.am.
# Makefile.  Generated from Makefile.in by configure.

# Copyright (C) 1994, 1995, 1996, 1997, 1998, 1999, 2000, 2001, 2002,
# 2003, 2004, 2005, 2006, 2007, 2008  Free Software Foundation, Inc.
# This Makefile.in is free software; the Free Software Foundation
# gives unlimited permission to copy and/or distribute it,
# with or without modifications, as long as this notice is preserved.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY, to the extent permitted by law; without
# even the implied warranty of MERCHANTABILITY or FITNESS FOR A
# PARTICULAR PURPOSE.



pkgdatadir = $(datadir)/gnome-games
pkglibdir = $(libdir)/gnome-games
pkgincludedir = $(includedir)/gnome-games
am__cd = CDPATH="$${ZSH_VERSION+.}$(PATH_SEPARATOR)" && cd
install_sh_DATA = $(install_sh) -c -m 644
install_sh_PROGRAM = $(install_sh) -c
install_sh_SCRIPT = $(install_sh) -c
INSTALL_HEADER = $(INSTALL_DATA)
transform = $(program_transform_name)
NORMAL_INSTALL = :
PRE_INSTALL = :
POST_INSTALL = :
NORMAL_UNINSTALL = :
PRE_UNINSTALL = :
POST_UNINSTALL = :
build_triplet = i686-pc-linux-gnu
host_triplet = i686-pc-linux-gnu
#am__append_1 = sounds
subdir = .
DIST_COMMON = README $(am__configure_deps) $(srcdir)/Makefile.am \
	$(srcdir)/Makefile.in $(srcdir)/config.h.in \
	$(srcdir)/gnome-games.spec.in $(top_srcdir)/configure AUTHORS \
	COPYING ChangeLog NEWS TODO compile config.guess config.sub \
	depcomp install-sh ltmain.sh missing mkinstalldirs py-compile
ACLOCAL_M4 = $(top_srcdir)/aclocal.m4
am__aclocal_m4_deps = $(top_srcdir)/m4/c99.m4 $(top_srcdir)/m4/ggz.m4 \
	$(top_srcdir)/m4/gnome-doc-utils.m4 \
	$(top_srcdir)/m4/intltool.m4 $(top_srcdir)/m4/platform.m4 \
	$(top_srcdir)/m4/sdl.m4 $(top_srcdir)/m4/sound.m4 \
	$(top_srcdir)/m4/system.m4 $(top_srcdir)/m4/tls.m4 \
	$(top_srcdir)/configure.in
am__configure_deps = $(am__aclocal_m4_deps) $(CONFIGURE_DEPENDENCIES) \
	$(ACLOCAL_M4)
am__CONFIG_DISTCLEAN_FILES = config.status config.cache config.log \
 configure.lineno config.status.lineno
mkinstalldirs = $(SHELL) $(top_srcdir)/mkinstalldirs
CONFIG_HEADER = config.h
CONFIG_CLEAN_FILES = gnome-games.spec
SOURCES =
DIST_SOURCES =
RECURSIVE_TARGETS = all-recursive check-recursive dvi-recursive \
	html-recursive info-recursive install-data-recursive \
	install-dvi-recursive install-exec-recursive \
	install-html-recursive install-info-recursive \
	install-pdf-recursive install-ps-recursive install-recursive \
	installcheck-recursive installdirs-recursive pdf-recursive \
	ps-recursive uninstall-recursive
RECURSIVE_CLEAN_TARGETS = mostlyclean-recursive clean-recursive	\
  distclean-recursive maintainer-clean-recursive
ETAGS = etags
CTAGS = ctags
DISTFILES = $(DIST_COMMON) $(DIST_SOURCES) $(TEXINFOS) $(EXTRA_DIST)
distdir = $(PACKAGE)-$(VERSION)
top_distdir = $(distdir)
am__remove_distdir = \
  { test ! -d $(distdir) \
    || { find $(distdir) -type d ! -perm -200 -exec chmod u+w {} ';' \
         && rm -fr $(distdir); }; }
GZIP_ENV = --best
DIST_ARCHIVES = $(distdir).tar.bz2
distcleancheck_listfiles = find . -type f -print
ACLOCAL = ${SHELL} /home/jordan/Downloads/gnome-games-2.22.3/missing --run aclocal-1.10
ACLOCAL_AMFLAGS = -I m4
ALL_LINGUAS = 
AMTAR = ${SHELL} /home/jordan/Downloads/gnome-games-2.22.3/missing --run tar
AR = ar
AS = as
AUTOCONF = ${SHELL} /home/jordan/Downloads/gnome-games-2.22.3/missing --run autoconf
AUTOHEADER = ${SHELL} /home/jordan/Downloads/gnome-games-2.22.3/missing --run autoheader
AUTOMAKE = ${SHELL} /home/jordan/Downloads/gnome-games-2.22.3/missing --run automake-1.10
AWK = gawk
CATALOGS = 
CATOBJEXT = .gmo
CC = gcc
CCDEPMODE = depmode=gcc3
CFLAGS = -g -O2 -D_REENTRANT
CHECK_CFLAGS = 
CHECK_LIBS = 
CPP = gcc -E
CPPFLAGS =  -I /usr/local/include -I /usr/local/include
CXX = g++
CXXCPP = g++ -E
CXXDEPMODE = depmode=gcc3
CXXFLAGS = -g -O2
CYGPATH_W = echo
DATADIRNAME = share
DEFS = -DHAVE_CONFIG_H
DEPDIR = .deps
DISTCHECK_CONFIGURE_FLAGS = \
	--with-platform=gnome \
	--disable-schemas-install \
	--disable-scrollkeeper

DLLTOOL = dlltool
DOC_USER_FORMATS = 
DSYMUTIL = 
ECHO = echo
ECHO_C = 
ECHO_N = -n
ECHO_T = 
EGREP = /bin/grep -E
EXEEXT = 
F77 = 
FFLAGS = 
GCONFTOOL = /usr/bin/gconftool-2
GCONF_CFLAGS = -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
GCONF_LIBS = -lgconf-2 -lglib-2.0  
GCONF_SCHEMA_CONFIG_SOURCE = xml:merged:/etc/gconf/gconf.xml.defaults
GCONF_SCHEMA_FILE_DIR = $(sysconfdir)/gconf/schemas
GETTEXT_PACKAGE = gnome-games
GGZDMOD_INCLUDES = 
GGZDMOD_LDFLAGS = 
GGZMOD_INCLUDES = -I /usr/include
GGZMOD_LDFLAGS = -L/usr/lib
GGZTLS_INCLUDES = 
GGZTLS_LDFLAGS = 
GGZ_CONFIG = true
GGZ_GTK_INCLUDES = -I$(top_srcdir)/dependencies/ggz-gtk
GGZ_GTK_LDFLAGS = 
GLIB_GENMARSHAL = /usr/bin/glib-genmarshal
GLIB_GENMARSHAL_INTERNAL = --internal
GMOFILES = 
GMSGFMT = /usr/bin/msgfmt
GNOME_CFLAGS = -DORBIT2=1 -pthread -I/usr/include/libxml2 -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1  
GNOME_GAMES_CFLAGS =  -std=gnu89 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/libxml2 -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1   -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/librsvg-2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1     -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -I$(top_srcdir)/libgames-support -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare 
GNOME_GAMES_CXXFLAGS = -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/libxml2 -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1   -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/librsvg-2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1     -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -I$(top_srcdir)/libgames-support -g -O2 -Wall -Wno-unused -Wshadow -Woverloaded-virtual 
GNOME_GAMES_GGZ_DSC_RULE = %.dsc:   %.dsc.in   ; $(SED) -e "s|@VERSION@|$(VERSION)|g" -e "s|@libexecdir@|$(libexecdir)|g" -e "s|@bindir@|$(bindir)|g" -e "s|@ggzexecmoddir@|$(ggzexecmoddir)|g"< $< > $@
GNOME_GAMES_GGZ_INTLTOOL_ROOM_RULE = %.room:   %.room.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
GNOME_GAMES_LIBS = -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lgconf-2 -lglib-2.0   -pthread -lxml2 -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lORBit-2 -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgconf-2 -lgthread-2.0 -lrt -lgmodule-2.0 -ldl -lgobject-2.0 -lglib-2.0   -lffi -lgobject-2.0 -lglib-2.0   -lrsvg-2 -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lcairo     -L/usr/lib -lSDL -lSDL_mixer
GNOME_LIBS = -pthread -lxml2 -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lORBit-2 -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgconf-2 -lgthread-2.0 -lrt -lgmodule-2.0 -ldl -lgobject-2.0 -lglib-2.0  
GREP = /bin/grep
GSTREAMER_CFLAGS = 
GSTREAMER_LIBS = 
GTHREAD_CFLAGS = -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
GTHREAD_LIBS = -pthread -lgthread-2.0 -lrt -lglib-2.0  
GTK_CFLAGS = -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  
GTK_LIBS = -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
GUILE = /usr/bin/guile
GUILE_CFLAGS = 
GUILE_CONFIG = /usr/bin/guile-config
GUILE_LIBS = -lguile -lguile-ltdl -lqthreads -lpthread -lcrypt -lm
HELP_DIR = ${datadir}/gnome/help
HILDON_CFLAGS = 
HILDON_LIBS = 
INSTALL = /usr/bin/install -c
INSTALL_DATA = ${INSTALL} -m 644
INSTALL_PROGRAM = ${INSTALL}
INSTALL_SCRIPT = ${INSTALL}
INSTALL_STRIP_PROGRAM = $(install_sh) -c -s
INSTOBJEXT = .mo
INTLLIBS = 
INTLTOOL_CAVES_RULE = %.caves:     %.caves.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_DESKTOP_RULE = %.desktop:   %.desktop.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_DIRECTORY_RULE = %.directory: %.directory.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_EXTRACT = /usr/bin/intltool-extract
INTLTOOL_KBD_RULE = %.kbd:       %.kbd.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -m -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_KEYS_RULE = %.keys:      %.keys.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -k -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_MERGE = /usr/bin/intltool-merge
INTLTOOL_OAF_RULE = %.oaf:       %.oaf.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -o -p $(top_srcdir)/po $< $@
INTLTOOL_PERL = /usr/bin/perl
INTLTOOL_POLICY_RULE = %.policy:    %.policy.in    $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_PONG_RULE = %.pong:      %.pong.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_PROP_RULE = %.prop:      %.prop.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_SCHEMAS_RULE = %.schemas:   %.schemas.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -s -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_SERVER_RULE = %.server:    %.server.in    $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -o -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_SERVICE_RULE = %.service: %.service.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_SHEET_RULE = %.sheet:     %.sheet.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_SOUNDLIST_RULE = %.soundlist: %.soundlist.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_THEME_RULE = %.theme:     %.theme.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_UI_RULE = %.ui:        %.ui.in        $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_UPDATE = /usr/bin/intltool-update
INTLTOOL_XAM_RULE = %.xam:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_XML_NOMERGE_RULE = %.xml:       %.xml.in       $(INTLTOOL_MERGE) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u /tmp $< $@
INTLTOOL_XML_RULE = %.xml:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
LDADD =  -lnsl -lpthread
LDFLAGS =  -L/usr/local/lib -L/usr/local/lib
LIBGGZ_INCLUDES = -I /usr/include
LIBGGZ_LDFLAGS = -L/usr/lib
LIBOBJS = 
LIBS = 
LIBTOOL = $(SHELL) $(top_builddir)/libtool
LIB_ASYNC = 
LIB_GCRYPT = -lgcrypt
LIB_GGZ = -lggz
LIB_GGZDMOD = 
LIB_GGZMOD = -lggzmod
LIB_GGZTLS = 
LIB_GGZ_GTK = $(top_builddir)/dependencies/ggz-gtk/libggz-gtk.la
LN_S = ln -s
LTLIBOBJS = 
MAKEINFO = ${SHELL} /home/jordan/Downloads/gnome-games-2.22.3/missing --run makeinfo
MKDIR_P = /bin/mkdir -p
MKINSTALLDIRS = ./mkinstalldirs
MSGFMT = /usr/bin/msgfmt
MSGFMT_OPTS = -c
MSGMERGE = /usr/bin/msgmerge
NMEDIT = 
OBJDUMP = objdump
OBJEXT = o
OMF_DIR = ${datadir}/omf
PACKAGE = gnome-games
PACKAGE_BUGREPORT = http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games
PACKAGE_NAME = GNOME Games
PACKAGE_STRING = GNOME Games 2.22.3
PACKAGE_TARNAME = gnome-games
PACKAGE_VERSION = 2.22.3
PATH_SEPARATOR = :
PKG_CONFIG = /usr/bin/pkg-config
POFILES = 
POSUB = po
PO_IN_DATADIR_FALSE = 
PO_IN_DATADIR_TRUE = 
PYGTK_CFLAGS = -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
PYGTK_LIBS = -lffi -lgobject-2.0 -lglib-2.0  
PYTHON = /usr/bin/python
PYTHON_EXEC_PREFIX = ${exec_prefix}
PYTHON_PLATFORM = linux2
PYTHON_PREFIX = ${prefix}
PYTHON_VERSION = 2.5
RANLIB = ranlib
RSVG_CFLAGS = -I/usr/include/librsvg-2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  
RSVG_LIBS = -lrsvg-2 -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lcairo  
SDL_CFLAGS = -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT
SDL_CONFIG = /usr/bin/sdl-config
SDL_LIBS = -L/usr/lib -lSDL
SDL_MIXER_CFLAGS =  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT
SDL_MIXER_LIBS =  -L/usr/lib -lSDL -lSDL_mixer
SED = /bin/sed
SET_MAKE = 
SHELL = /bin/bash
STRIP = strip
USE_NLS = yes
VERSION = 2.22.3
WARN_CFLAGS = -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare 
WARN_CXXFLAGS = -g -O2 -Wall -Wno-unused -Wshadow -Woverloaded-virtual 
XGETTEXT = /usr/bin/xgettext
abs_builddir = /home/jordan/Downloads/gnome-games-2.22.3
abs_srcdir = /home/jordan/Downloads/gnome-games-2.22.3
abs_top_builddir = /home/jordan/Downloads/gnome-games-2.22.3
abs_top_srcdir = /home/jordan/Downloads/gnome-games-2.22.3
ac_ct_CC = gcc
ac_ct_CXX = g++
ac_ct_F77 = 
allgames = aisleriot blackjack gnometris gnect gnomine same-gnome mahjongg gtali gnotravex gnotski glines iagno glchess gnobots2 gnibbles gnome-sudoku
am__include = include
am__leading_dot = .
am__quote = 
am__tar = ${AMTAR} chof - "$$tardir"
am__untar = ${AMTAR} xf -
bindir = ${exec_prefix}/bin
build = i686-pc-linux-gnu
build_alias = 
build_cpu = i686
build_os = linux-gnu
build_vendor = pc
builddir = .
datadir = ${datarootdir}
datarootdir = ${prefix}/share
docdir = ${datarootdir}/doc/${PACKAGE_TARNAME}
dvidir = ${docdir}
exec_prefix = ${prefix}
gamelist = aisleriot blackjack gnometris gnect gnomine same-gnome mahjongg gtali gnotravex gnotski glines iagno glchess gnobots2 gnibbles gnome-sudoku
ggz_config = 
ggzdatadir = ${datadir}/ggz
ggzdconfdir = 
ggzddatadir = 
ggzdexecmoddir = 
ggzdexecmodpath = 
ggzdmod_includes = 
ggzdmod_libraries = 
ggzexecmoddir = ${libdir}/ggz
ggzmod_includes = /usr/include
ggzmod_libraries = /usr/lib
ggzmoduleconfdir = 
host = i686-pc-linux-gnu
host_alias = 
host_cpu = i686
host_os = linux-gnu
host_vendor = pc
htmldir = ${docdir}
includedir = ${prefix}/include
infodir = ${datarootdir}/info
install_sh = $(SHELL) /home/jordan/Downloads/gnome-games-2.22.3/install-sh
libdir = ${exec_prefix}/lib
libexecdir = ${exec_prefix}/libexec
libggz_includes = /usr/include
libggz_libraries = /usr/lib
localedir = ${datarootdir}/locale
localstatedir = ${prefix}/var
mandir = ${datarootdir}/man
mkdir_p = /bin/mkdir -p
oldincludedir = /usr/include
packagesrcdir = 
pdfdir = ${docdir}
pkgpyexecdir = ${pyexecdir}/gnome-games
pkgpythondir = ${pythondir}/gnome-games
prefix = /usr/local
program_transform_name = s,x,x,
psdir = ${docdir}
pyexecdir = ${exec_prefix}/lib/python2.5/site-packages
pythondir = ${prefix}/lib/python2.5/site-packages
sbindir = ${exec_prefix}/sbin
scoredir = ${localstatedir}/games
scores_group = games
scores_user = games
setgid = true
sharedstatedir = ${prefix}/com
srcdir = .
sysconfdir = ${prefix}/etc
target_alias = 
top_builddir = .
top_srcdir = .
SUBDIRS = po dependencies icons libgames-support tests $(gamelist) \
	$(am__append_1)
DIST_SUBDIRS = po dependencies icons sounds libgames-support tests $(allgames)
EXTRA_DIST = \
	autogen.sh \
	gnome-games.spec.in \
	gnome-games.spec \
	COPYING-DOCS \
	xmldocs.make \
	omf.make \
	MAINTAINERS	\
	HACKING		 \
	gnome-doc-utils.make

DISTCLEANFILES = \
	intltool-extract \
	intltool-merge \
	intltool-update \
	gnome-doc-utils.make


# Ignore score files, these *should* be left behind.
distuninstallcheck_listfiles = find . -type f -print | grep -v '.scores' | grep-v scrollkeeper
all: config.h
	$(MAKE) $(AM_MAKEFLAGS) all-recursive

.SUFFIXES:
am--refresh:
	@:
$(srcdir)/Makefile.in:  $(srcdir)/Makefile.am  $(am__configure_deps)
	@for dep in $?; do \
	  case '$(am__configure_deps)' in \
	    *$$dep*) \
	      echo ' cd $(srcdir) && $(AUTOMAKE) --foreign '; \
	      cd $(srcdir) && $(AUTOMAKE) --foreign  \
		&& exit 0; \
	      exit 1;; \
	  esac; \
	done; \
	echo ' cd $(top_srcdir) && $(AUTOMAKE) --foreign  Makefile'; \
	cd $(top_srcdir) && \
	  $(AUTOMAKE) --foreign  Makefile
.PRECIOUS: Makefile
Makefile: $(srcdir)/Makefile.in $(top_builddir)/config.status
	@case '$?' in \
	  *config.status*) \
	    echo ' $(SHELL) ./config.status'; \
	    $(SHELL) ./config.status;; \
	  *) \
	    echo ' cd $(top_builddir) && $(SHELL) ./config.status $@ $(am__depfiles_maybe)'; \
	    cd $(top_builddir) && $(SHELL) ./config.status $@ $(am__depfiles_maybe);; \
	esac;

$(top_builddir)/config.status: $(top_srcdir)/configure $(CONFIG_STATUS_DEPENDENCIES)
	$(SHELL) ./config.status --recheck

$(top_srcdir)/configure:  $(am__configure_deps)
	cd $(srcdir) && $(AUTOCONF)
$(ACLOCAL_M4):  $(am__aclocal_m4_deps)
	cd $(srcdir) && $(ACLOCAL) $(ACLOCAL_AMFLAGS)

config.h: stamp-h1
	@if test ! -f $@; then \
	  rm -f stamp-h1; \
	  $(MAKE) $(AM_MAKEFLAGS) stamp-h1; \
	else :; fi

stamp-h1: $(srcdir)/config.h.in $(top_builddir)/config.status
	@rm -f stamp-h1
	cd $(top_builddir) && $(SHELL) ./config.status config.h
$(srcdir)/config.h.in:  $(am__configure_deps) 
	cd $(top_srcdir) && $(AUTOHEADER)
	rm -f stamp-h1
	touch $@

distclean-hdr:
	-rm -f config.h stamp-h1
gnome-games.spec: $(top_builddir)/config.status $(srcdir)/gnome-games.spec.in
	cd $(top_builddir) && $(SHELL) ./config.status $@

mostlyclean-libtool:
	-rm -f *.lo

clean-libtool:
	-rm -rf .libs _libs

distclean-libtool:
	-rm -f libtool

# This directory's subdirectories are mostly independent; you can cd
# into them and run `make' without going through this Makefile.
# To change the values of `make' variables: instead of editing Makefiles,
# (1) if the variable is set in `config.status', edit `config.status'
#     (which will cause the Makefiles to be regenerated when you run `make');
# (2) otherwise, pass the desired values on the `make' command line.
$(RECURSIVE_TARGETS):
	@failcom='exit 1'; \
	for f in x $$MAKEFLAGS; do \
	  case $$f in \
	    *=* | --[!k]*);; \
	    *k*) failcom='fail=yes';; \
	  esac; \
	done; \
	dot_seen=no; \
	target=`echo $@ | sed s/-recursive//`; \
	list='$(SUBDIRS)'; for subdir in $$list; do \
	  echo "Making $$target in $$subdir"; \
	  if test "$$subdir" = "."; then \
	    dot_seen=yes; \
	    local_target="$$target-am"; \
	  else \
	    local_target="$$target"; \
	  fi; \
	  (cd $$subdir && $(MAKE) $(AM_MAKEFLAGS) $$local_target) \
	  || eval $$failcom; \
	done; \
	if test "$$dot_seen" = "no"; then \
	  $(MAKE) $(AM_MAKEFLAGS) "$$target-am" || exit 1; \
	fi; test -z "$$fail"

$(RECURSIVE_CLEAN_TARGETS):
	@failcom='exit 1'; \
	for f in x $$MAKEFLAGS; do \
	  case $$f in \
	    *=* | --[!k]*);; \
	    *k*) failcom='fail=yes';; \
	  esac; \
	done; \
	dot_seen=no; \
	case "$@" in \
	  distclean-* | maintainer-clean-*) list='$(DIST_SUBDIRS)' ;; \
	  *) list='$(SUBDIRS)' ;; \
	esac; \
	rev=''; for subdir in $$list; do \
	  if test "$$subdir" = "."; then :; else \
	    rev="$$subdir $$rev"; \
	  fi; \
	done; \
	rev="$$rev ."; \
	target=`echo $@ | sed s/-recursive//`; \
	for subdir in $$rev; do \
	  echo "Making $$target in $$subdir"; \
	  if test "$$subdir" = "."; then \
	    local_target="$$target-am"; \
	  else \
	    local_target="$$target"; \
	  fi; \
	  (cd $$subdir && $(MAKE) $(AM_MAKEFLAGS) $$local_target) \
	  || eval $$failcom; \
	done && test -z "$$fail"
tags-recursive:
	list='$(SUBDIRS)'; for subdir in $$list; do \
	  test "$$subdir" = . || (cd $$subdir && $(MAKE) $(AM_MAKEFLAGS) tags); \
	done
ctags-recursive:
	list='$(SUBDIRS)'; for subdir in $$list; do \
	  test "$$subdir" = . || (cd $$subdir && $(MAKE) $(AM_MAKEFLAGS) ctags); \
	done

ID: $(HEADERS) $(SOURCES) $(LISP) $(TAGS_FILES)
	list='$(SOURCES) $(HEADERS) $(LISP) $(TAGS_FILES)'; \
	unique=`for i in $$list; do \
	    if test -f "$$i"; then echo $$i; else echo $(srcdir)/$$i; fi; \
	  done | \
	  $(AWK) '{ files[$$0] = 1; nonemtpy = 1; } \
	      END { if (nonempty) { for (i in files) print i; }; }'`; \
	mkid -fID $$unique
tags: TAGS

TAGS: tags-recursive $(HEADERS) $(SOURCES) config.h.in $(TAGS_DEPENDENCIES) \
		$(TAGS_FILES) $(LISP)
	tags=; \
	here=`pwd`; \
	if ($(ETAGS) --etags-include --version) >/dev/null 2>&1; then \
	  include_option=--etags-include; \
	  empty_fix=.; \
	else \
	  include_option=--include; \
	  empty_fix=; \
	fi; \
	list='$(SUBDIRS)'; for subdir in $$list; do \
	  if test "$$subdir" = .; then :; else \
	    test ! -f $$subdir/TAGS || \
	      tags="$$tags $$include_option=$$here/$$subdir/TAGS"; \
	  fi; \
	done; \
	list='$(SOURCES) $(HEADERS) config.h.in $(LISP) $(TAGS_FILES)'; \
	unique=`for i in $$list; do \
	    if test -f "$$i"; then echo $$i; else echo $(srcdir)/$$i; fi; \
	  done | \
	  $(AWK) '{ files[$$0] = 1; nonempty = 1; } \
	      END { if (nonempty) { for (i in files) print i; }; }'`; \
	if test -z "$(ETAGS_ARGS)$$tags$$unique"; then :; else \
	  test -n "$$unique" || unique=$$empty_fix; \
	  $(ETAGS) $(ETAGSFLAGS) $(AM_ETAGSFLAGS) $(ETAGS_ARGS) \
	    $$tags $$unique; \
	fi
ctags: CTAGS
CTAGS: ctags-recursive $(HEADERS) $(SOURCES) config.h.in $(TAGS_DEPENDENCIES) \
		$(TAGS_FILES) $(LISP)
	tags=; \
	list='$(SOURCES) $(HEADERS) config.h.in $(LISP) $(TAGS_FILES)'; \
	unique=`for i in $$list; do \
	    if test -f "$$i"; then echo $$i; else echo $(srcdir)/$$i; fi; \
	  done | \
	  $(AWK) '{ files[$$0] = 1; nonempty = 1; } \
	      END { if (nonempty) { for (i in files) print i; }; }'`; \
	test -z "$(CTAGS_ARGS)$$tags$$unique" \
	  || $(CTAGS) $(CTAGSFLAGS) $(AM_CTAGSFLAGS) $(CTAGS_ARGS) \
	     $$tags $$unique

GTAGS:
	here=`$(am__cd) $(top_builddir) && pwd` \
	  && cd $(top_srcdir) \
	  && gtags -i $(GTAGS_ARGS) $$here

distclean-tags:
	-rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags

distdir: $(DISTFILES)
	$(am__remove_distdir)
	test -d $(distdir) || mkdir $(distdir)
	@srcdirstrip=`echo "$(srcdir)" | sed 's/[].[^$$\\*]/\\\\&/g'`; \
	topsrcdirstrip=`echo "$(top_srcdir)" | sed 's/[].[^$$\\*]/\\\\&/g'`; \
	list='$(DISTFILES)'; \
	  dist_files=`for file in $$list; do echo $$file; done | \
	  sed -e "s|^$$srcdirstrip/||;t" \
	      -e "s|^$$topsrcdirstrip/|$(top_builddir)/|;t"`; \
	case $$dist_files in \
	  */*) $(MKDIR_P) `echo "$$dist_files" | \
			   sed '/\//!d;s|^|$(distdir)/|;s,/[^/]*$$,,' | \
			   sort -u` ;; \
	esac; \
	for file in $$dist_files; do \
	  if test -f $$file || test -d $$file; then d=.; else d=$(srcdir); fi; \
	  if test -d $$d/$$file; then \
	    dir=`echo "/$$file" | sed -e 's,/[^/]*$$,,'`; \
	    if test -d $(srcdir)/$$file && test $$d != $(srcdir); then \
	      cp -pR $(srcdir)/$$file $(distdir)$$dir || exit 1; \
	    fi; \
	    cp -pR $$d/$$file $(distdir)$$dir || exit 1; \
	  else \
	    test -f $(distdir)/$$file \
	    || cp -p $$d/$$file $(distdir)/$$file \
	    || exit 1; \
	  fi; \
	done
	list='$(DIST_SUBDIRS)'; for subdir in $$list; do \
	  if test "$$subdir" = .; then :; else \
	    test -d "$(distdir)/$$subdir" \
	    || $(MKDIR_P) "$(distdir)/$$subdir" \
	    || exit 1; \
	    distdir=`$(am__cd) $(distdir) && pwd`; \
	    top_distdir=`$(am__cd) $(top_distdir) && pwd`; \
	    (cd $$subdir && \
	      $(MAKE) $(AM_MAKEFLAGS) \
	        top_distdir="$$top_distdir" \
	        distdir="$$distdir/$$subdir" \
		am__remove_distdir=: \
		am__skip_length_check=: \
	        distdir) \
	      || exit 1; \
	  fi; \
	done
	-find $(distdir) -type d ! -perm -777 -exec chmod a+rwx {} \; -o \
	  ! -type d ! -perm -444 -links 1 -exec chmod a+r {} \; -o \
	  ! -type d ! -perm -400 -exec chmod a+r {} \; -o \
	  ! -type d ! -perm -444 -exec $(install_sh) -c -m a+r {} {} \; \
	|| chmod -R a+r $(distdir)
dist-gzip: distdir
	tardir=$(distdir) && $(am__tar) | GZIP=$(GZIP_ENV) gzip -c >$(distdir).tar.gz
	$(am__remove_distdir)
dist-bzip2: distdir
	tardir=$(distdir) && $(am__tar) | bzip2 -9 -c >$(distdir).tar.bz2
	$(am__remove_distdir)

dist-lzma: distdir
	tardir=$(distdir) && $(am__tar) | lzma -9 -c >$(distdir).tar.lzma
	$(am__remove_distdir)

dist-tarZ: distdir
	tardir=$(distdir) && $(am__tar) | compress -c >$(distdir).tar.Z
	$(am__remove_distdir)

dist-shar: distdir
	shar $(distdir) | GZIP=$(GZIP_ENV) gzip -c >$(distdir).shar.gz
	$(am__remove_distdir)

dist-zip: distdir
	-rm -f $(distdir).zip
	zip -rq $(distdir).zip $(distdir)
	$(am__remove_distdir)

dist dist-all: distdir
	tardir=$(distdir) && $(am__tar) | bzip2 -9 -c >$(distdir).tar.bz2
	$(am__remove_distdir)

# This target untars the dist file and tries a VPATH configuration.  Then
# it guarantees that the distribution is self-contained by making another
# tarfile.
distcheck: dist
	case '$(DIST_ARCHIVES)' in \
	*.tar.gz*) \
	  GZIP=$(GZIP_ENV) gunzip -c $(distdir).tar.gz | $(am__untar) ;;\
	*.tar.bz2*) \
	  bunzip2 -c $(distdir).tar.bz2 | $(am__untar) ;;\
	*.tar.lzma*) \
	  unlzma -c $(distdir).tar.lzma | $(am__untar) ;;\
	*.tar.Z*) \
	  uncompress -c $(distdir).tar.Z | $(am__untar) ;;\
	*.shar.gz*) \
	  GZIP=$(GZIP_ENV) gunzip -c $(distdir).shar.gz | unshar ;;\
	*.zip*) \
	  unzip $(distdir).zip ;;\
	esac
	chmod -R a-w $(distdir); chmod a+w $(distdir)
	mkdir $(distdir)/_build
	mkdir $(distdir)/_inst
	chmod a-w $(distdir)
	dc_install_base=`$(am__cd) $(distdir)/_inst && pwd | sed -e 's,^[^:\\/]:[\\/],/,'` \
	  && dc_destdir="$${TMPDIR-/tmp}/am-dc-$$$$/" \
	  && cd $(distdir)/_build \
	  && ../configure --srcdir=.. --prefix="$$dc_install_base" \
	    $(DISTCHECK_CONFIGURE_FLAGS) \
	  && $(MAKE) $(AM_MAKEFLAGS) \
	  && $(MAKE) $(AM_MAKEFLAGS) dvi \
	  && $(MAKE) $(AM_MAKEFLAGS) check \
	  && $(MAKE) $(AM_MAKEFLAGS) install \
	  && $(MAKE) $(AM_MAKEFLAGS) installcheck \
	  && $(MAKE) $(AM_MAKEFLAGS) uninstall \
	  && $(MAKE) $(AM_MAKEFLAGS) distuninstallcheck_dir="$$dc_install_base" \
	        distuninstallcheck \
	  && chmod -R a-w "$$dc_install_base" \
	  && ({ \
	       (cd ../.. && umask 077 && mkdir "$$dc_destdir") \
	       && $(MAKE) $(AM_MAKEFLAGS) DESTDIR="$$dc_destdir" install \
	       && $(MAKE) $(AM_MAKEFLAGS) DESTDIR="$$dc_destdir" uninstall \
	       && $(MAKE) $(AM_MAKEFLAGS) DESTDIR="$$dc_destdir" \
	            distuninstallcheck_dir="$$dc_destdir" distuninstallcheck; \
	      } || { rm -rf "$$dc_destdir"; exit 1; }) \
	  && rm -rf "$$dc_destdir" \
	  && $(MAKE) $(AM_MAKEFLAGS) dist \
	  && rm -rf $(DIST_ARCHIVES) \
	  && $(MAKE) $(AM_MAKEFLAGS) distcleancheck
	$(am__remove_distdir)
	@(echo "$(distdir) archives ready for distribution: "; \
	  list='$(DIST_ARCHIVES)'; for i in $$list; do echo $$i; done) | \
	  sed -e 1h -e 1s/./=/g -e 1p -e 1x -e '$$p' -e '$$x'
distuninstallcheck:
	@cd $(distuninstallcheck_dir) \
	&& test `$(distuninstallcheck_listfiles) | wc -l` -le 1 \
	   || { echo "ERROR: files left after uninstall:" ; \
	        if test -n "$(DESTDIR)"; then \
	          echo "  (check DESTDIR support)"; \
	        fi ; \
	        $(distuninstallcheck_listfiles) ; \
	        exit 1; } >&2
distcleancheck: distclean
	@if test '$(srcdir)' = . ; then \
	  echo "ERROR: distcleancheck can only run from a VPATH build" ; \
	  exit 1 ; \
	fi
	@test `$(distcleancheck_listfiles) | wc -l` -eq 0 \
	  || { echo "ERROR: files left in build directory after distclean:" ; \
	       $(distcleancheck_listfiles) ; \
	       exit 1; } >&2
check-am: all-am
check: check-recursive
all-am: Makefile config.h
installdirs: installdirs-recursive
installdirs-am:
install: install-recursive
install-exec: install-exec-recursive
install-data: install-data-recursive
uninstall: uninstall-recursive

install-am: all-am
	@$(MAKE) $(AM_MAKEFLAGS) install-exec-am install-data-am

installcheck: installcheck-recursive
install-strip:
	$(MAKE) $(AM_MAKEFLAGS) INSTALL_PROGRAM="$(INSTALL_STRIP_PROGRAM)" \
	  install_sh_PROGRAM="$(INSTALL_STRIP_PROGRAM)" INSTALL_STRIP_FLAG=-s \
	  `test -z '$(STRIP)' || \
	    echo "INSTALL_PROGRAM_ENV=STRIPPROG='$(STRIP)'"` install
mostlyclean-generic:

clean-generic:

distclean-generic:
	-test -z "$(CONFIG_CLEAN_FILES)" || rm -f $(CONFIG_CLEAN_FILES)
	-test -z "$(DISTCLEANFILES)" || rm -f $(DISTCLEANFILES)

maintainer-clean-generic:
	@echo "This command is intended for maintainers to use"
	@echo "it deletes files that may require special tools to rebuild."
clean: clean-recursive

clean-am: clean-generic clean-libtool mostlyclean-am

distclean: distclean-recursive
	-rm -f $(am__CONFIG_DISTCLEAN_FILES)
	-rm -f Makefile
distclean-am: clean-am distclean-generic distclean-hdr \
	distclean-libtool distclean-tags

dvi: dvi-recursive

dvi-am:

html: html-recursive

info: info-recursive

info-am:

install-data-am:

install-dvi: install-dvi-recursive

install-exec-am:

install-html: install-html-recursive

install-info: install-info-recursive

install-man:

install-pdf: install-pdf-recursive

install-ps: install-ps-recursive

installcheck-am:

maintainer-clean: maintainer-clean-recursive
	-rm -f $(am__CONFIG_DISTCLEAN_FILES)
	-rm -rf $(top_srcdir)/autom4te.cache
	-rm -f Makefile
maintainer-clean-am: distclean-am maintainer-clean-generic

mostlyclean: mostlyclean-recursive

mostlyclean-am: mostlyclean-generic mostlyclean-libtool

pdf: pdf-recursive

pdf-am:

ps: ps-recursive

ps-am:

uninstall-am:

.MAKE: $(RECURSIVE_CLEAN_TARGETS) $(RECURSIVE_TARGETS) install-am \
	install-strip

.PHONY: $(RECURSIVE_CLEAN_TARGETS) $(RECURSIVE_TARGETS) CTAGS GTAGS \
	all all-am am--refresh check check-am clean clean-generic \
	clean-libtool ctags ctags-recursive dist dist-all dist-bzip2 \
	dist-gzip dist-lzma dist-shar dist-tarZ dist-zip distcheck \
	distclean distclean-generic distclean-hdr distclean-libtool \
	distclean-tags distcleancheck distdir distuninstallcheck dvi \
	dvi-am html html-am info info-am install install-am \
	install-data install-data-am install-dvi install-dvi-am \
	install-exec install-exec-am install-html install-html-am \
	install-info install-info-am install-man install-pdf \
	install-pdf-am install-ps install-ps-am install-strip \
	installcheck installcheck-am installdirs installdirs-am \
	maintainer-clean maintainer-clean-generic mostlyclean \
	mostlyclean-generic mostlyclean-libtool pdf pdf-am ps ps-am \
	tags tags-recursive uninstall uninstall-am

# Tell versions [3.59,3.63) of GNU make to not export all variables.
# Otherwise a system limit (for SysV at least) may be exceeded.
.NOEXPORT:
```And here is the mahjongg makefile:```
# Makefile.in generated by automake 1.10.1 from Makefile.am.
# mahjongg/Makefile.  Generated from Makefile.in by configure.

# Copyright (C) 1994, 1995, 1996, 1997, 1998, 1999, 2000, 2001, 2002,
# 2003, 2004, 2005, 2006, 2007, 2008  Free Software Foundation, Inc.
# This Makefile.in is free software; the Free Software Foundation
# gives unlimited permission to copy and/or distribute it,
# with or without modifications, as long as this notice is preserved.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY, to the extent permitted by law; without
# even the implied warranty of MERCHANTABILITY or FITNESS FOR A
# PARTICULAR PURPOSE.





pkgdatadir = $(datadir)/gnome-games
pkglibdir = $(libdir)/gnome-games
pkgincludedir = $(includedir)/gnome-games
am__cd = CDPATH="$${ZSH_VERSION+.}$(PATH_SEPARATOR)" && cd
install_sh_DATA = $(install_sh) -c -m 644
install_sh_PROGRAM = $(install_sh) -c
install_sh_SCRIPT = $(install_sh) -c
INSTALL_HEADER = $(INSTALL_DATA)
transform = $(program_transform_name)
NORMAL_INSTALL = :
PRE_INSTALL = :
POST_INSTALL = :
NORMAL_UNINSTALL = :
PRE_UNINSTALL = :
POST_UNINSTALL = :
build_triplet = i686-pc-linux-gnu
host_triplet = i686-pc-linux-gnu
bin_PROGRAMS = mahjongg$(EXEEXT)
am__append_1 = $(GNOME_CFLAGS)
am__append_2 = $(GNOME_LIBS)
am__append_3 = $(RSVG_CFLAGS)
am__append_4 = $(RSVG_LIBS)
am__append_5 = $(GHTREAD_CFLAGS)
am__append_6 = $(GTHREAD_LIBS)
subdir = mahjongg
DIST_COMMON = $(srcdir)/Makefile.am $(srcdir)/Makefile.in \
	$(srcdir)/mahjongg.desktop.in.in ChangeLog
ACLOCAL_M4 = $(top_srcdir)/aclocal.m4
am__aclocal_m4_deps = $(top_srcdir)/m4/c99.m4 $(top_srcdir)/m4/ggz.m4 \
	$(top_srcdir)/m4/gnome-doc-utils.m4 \
	$(top_srcdir)/m4/intltool.m4 $(top_srcdir)/m4/platform.m4 \
	$(top_srcdir)/m4/sdl.m4 $(top_srcdir)/m4/sound.m4 \
	$(top_srcdir)/m4/system.m4 $(top_srcdir)/m4/tls.m4 \
	$(top_srcdir)/configure.in
am__configure_deps = $(am__aclocal_m4_deps) $(CONFIGURE_DEPENDENCIES) \
	$(ACLOCAL_M4)
mkinstalldirs = $(SHELL) $(top_srcdir)/mkinstalldirs
CONFIG_HEADER = $(top_builddir)/config.h
CONFIG_CLEAN_FILES = mahjongg.desktop.in
am__installdirs = "$(DESTDIR)$(bindir)" "$(DESTDIR)$(desktopdir)" \
	"$(DESTDIR)$(mapdir)" "$(DESTDIR)$(pixmapdir)" \
	"$(DESTDIR)$(schemadir)"
binPROGRAMS_INSTALL = $(INSTALL_PROGRAM)
PROGRAMS = $(bin_PROGRAMS)
am__objects_1 =
am_mahjongg_OBJECTS = mahjongg-drawing.$(OBJEXT) \
	mahjongg-mahjongg.$(OBJEXT) mahjongg-maps.$(OBJEXT) \
	mahjongg-solubility.$(OBJEXT) $(am__objects_1)
mahjongg_OBJECTS = $(am_mahjongg_OBJECTS)
am__DEPENDENCIES_1 =
am__DEPENDENCIES_2 = $(am__DEPENDENCIES_1)
am__DEPENDENCIES_3 = $(am__DEPENDENCIES_1)
am__DEPENDENCIES_4 = $(am__DEPENDENCIES_1)
mahjongg_DEPENDENCIES =  \
	$(top_builddir)/libgames-support/libgames-support.la \
	$(am__DEPENDENCIES_1) $(am__DEPENDENCIES_1) \
	$(am__DEPENDENCIES_1) $(am__DEPENDENCIES_2) \
	$(am__DEPENDENCIES_3) $(am__DEPENDENCIES_4)
mahjongg_LINK = $(LIBTOOL) --tag=CC $(AM_LIBTOOLFLAGS) $(LIBTOOLFLAGS) \
	--mode=link $(CCLD) $(mahjongg_CFLAGS) $(CFLAGS) $(AM_LDFLAGS) \
	$(LDFLAGS) -o $@
DEFAULT_INCLUDES = -I. -I$(top_builddir)
depcomp = $(SHELL) $(top_srcdir)/depcomp
am__depfiles_maybe = depfiles
COMPILE = $(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(AM_CPPFLAGS) \
	$(CPPFLAGS) $(AM_CFLAGS) $(CFLAGS)
LTCOMPILE = $(LIBTOOL) --tag=CC $(AM_LIBTOOLFLAGS) $(LIBTOOLFLAGS) \
	--mode=compile $(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) \
	$(AM_CPPFLAGS) $(CPPFLAGS) $(AM_CFLAGS) $(CFLAGS)
CCLD = $(CC)
LINK = $(LIBTOOL) --tag=CC $(AM_LIBTOOLFLAGS) $(LIBTOOLFLAGS) \
	--mode=link $(CCLD) $(AM_CFLAGS) $(CFLAGS) $(AM_LDFLAGS) \
	$(LDFLAGS) -o $@
SOURCES = $(mahjongg_SOURCES)
DIST_SOURCES = $(mahjongg_SOURCES)
RECURSIVE_TARGETS = all-recursive check-recursive dvi-recursive \
	html-recursive info-recursive install-data-recursive \
	install-dvi-recursive install-exec-recursive \
	install-html-recursive install-info-recursive \
	install-pdf-recursive install-ps-recursive install-recursive \
	installcheck-recursive installdirs-recursive pdf-recursive \
	ps-recursive uninstall-recursive
am__vpath_adj_setup = srcdirstrip=`echo "$(srcdir)" | sed 's|.|.|g'`;
am__vpath_adj = case $$p in \
    $(srcdir)/*) f=`echo "$$p" | sed "s|^$$srcdirstrip/||"`;; \
    *) f=$$p;; \
  esac;
am__strip_dir = `echo $$p | sed -e 's|^.*/||'`;
desktopDATA_INSTALL = $(INSTALL_DATA)
mapDATA_INSTALL = $(INSTALL_DATA)
pixmapDATA_INSTALL = $(INSTALL_DATA)
schemaDATA_INSTALL = $(INSTALL_DATA)
DATA = $(desktop_DATA) $(map_DATA) $(pixmap_DATA) $(schema_DATA)
RECURSIVE_CLEAN_TARGETS = mostlyclean-recursive clean-recursive	\
  distclean-recursive maintainer-clean-recursive
ETAGS = etags
CTAGS = ctags
DIST_SUBDIRS = $(SUBDIRS)
DISTFILES = $(DIST_COMMON) $(DIST_SOURCES) $(TEXINFOS) $(EXTRA_DIST)
ACLOCAL = ${SHELL} /home/jordan/Downloads/gnome-games-2.22.3/missing --run aclocal-1.10
ACLOCAL_AMFLAGS = ${ACLOCAL_FLAGS}
ALL_LINGUAS = 
AMTAR = ${SHELL} /home/jordan/Downloads/gnome-games-2.22.3/missing --run tar
AR = ar
AS = as
AUTOCONF = ${SHELL} /home/jordan/Downloads/gnome-games-2.22.3/missing --run autoconf
AUTOHEADER = ${SHELL} /home/jordan/Downloads/gnome-games-2.22.3/missing --run autoheader
AUTOMAKE = ${SHELL} /home/jordan/Downloads/gnome-games-2.22.3/missing --run automake-1.10
AWK = gawk
CATALOGS = 
CATOBJEXT = .gmo
CC = gcc
CCDEPMODE = depmode=gcc3
CFLAGS = -g -O2 -D_REENTRANT
CHECK_CFLAGS = 
CHECK_LIBS = 
CPP = gcc -E
CPPFLAGS =  -I /usr/local/include -I /usr/local/include
CXX = g++
CXXCPP = g++ -E
CXXDEPMODE = depmode=gcc3
CXXFLAGS = -g -O2
CYGPATH_W = echo
DATADIRNAME = share
DEFS = -DHAVE_CONFIG_H
DEPDIR = .deps
DISTCHECK_CONFIGURE_FLAGS = --disable-scrollkeeper 
DLLTOOL = dlltool
DOC_USER_FORMATS = 
DSYMUTIL = 
ECHO = echo
ECHO_C = 
ECHO_N = -n
ECHO_T = 
EGREP = /bin/grep -E
EXEEXT = 
F77 = 
FFLAGS = 
GCONFTOOL = /usr/bin/gconftool-2
GCONF_CFLAGS = -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
GCONF_LIBS = -lgconf-2 -lglib-2.0  
GCONF_SCHEMA_CONFIG_SOURCE = xml:merged:/etc/gconf/gconf.xml.defaults
GCONF_SCHEMA_FILE_DIR = $(sysconfdir)/gconf/schemas
GETTEXT_PACKAGE = gnome-games
GGZDMOD_INCLUDES = 
GGZDMOD_LDFLAGS = 
GGZMOD_INCLUDES = -I /usr/include
GGZMOD_LDFLAGS = -L/usr/lib
GGZTLS_INCLUDES = 
GGZTLS_LDFLAGS = 
GGZ_CONFIG = true
GGZ_GTK_INCLUDES = -I$(top_srcdir)/dependencies/ggz-gtk
GGZ_GTK_LDFLAGS = 
GLIB_GENMARSHAL = /usr/bin/glib-genmarshal
GLIB_GENMARSHAL_INTERNAL = --internal
GMOFILES = 
GMSGFMT = /usr/bin/msgfmt
GNOME_CFLAGS = -DORBIT2=1 -pthread -I/usr/include/libxml2 -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1  
GNOME_GAMES_CFLAGS =  -std=gnu89 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/libxml2 -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1   -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/librsvg-2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1     -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -I$(top_srcdir)/libgames-support -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare 
GNOME_GAMES_CXXFLAGS = -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/libxml2 -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1   -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/librsvg-2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1     -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -I$(top_srcdir)/libgames-support -g -O2 -Wall -Wno-unused -Wshadow -Woverloaded-virtual 
GNOME_GAMES_GGZ_DSC_RULE = %.dsc:   %.dsc.in   ; $(SED) -e "s|@VERSION@|$(VERSION)|g" -e "s|@libexecdir@|$(libexecdir)|g" -e "s|@bindir@|$(bindir)|g" -e "s|@ggzexecmoddir@|$(ggzexecmoddir)|g"< $< > $@
GNOME_GAMES_GGZ_INTLTOOL_ROOM_RULE = %.room:   %.room.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
GNOME_GAMES_LIBS = -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lgconf-2 -lglib-2.0   -pthread -lxml2 -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lORBit-2 -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgconf-2 -lgthread-2.0 -lrt -lgmodule-2.0 -ldl -lgobject-2.0 -lglib-2.0   -lffi -lgobject-2.0 -lglib-2.0   -lrsvg-2 -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lcairo     -L/usr/lib -lSDL -lSDL_mixer
GNOME_LIBS = -pthread -lxml2 -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lORBit-2 -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgconf-2 -lgthread-2.0 -lrt -lgmodule-2.0 -ldl -lgobject-2.0 -lglib-2.0  
GREP = /bin/grep
GSTREAMER_CFLAGS = 
GSTREAMER_LIBS = 
GTHREAD_CFLAGS = -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
GTHREAD_LIBS = -pthread -lgthread-2.0 -lrt -lglib-2.0  
GTK_CFLAGS = -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  
GTK_LIBS = -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
GUILE = /usr/bin/guile
GUILE_CFLAGS = 
GUILE_CONFIG = /usr/bin/guile-config
GUILE_LIBS = -lguile -lguile-ltdl -lqthreads -lpthread -lcrypt -lm
HELP_DIR = ${datadir}/gnome/help
HILDON_CFLAGS = 
HILDON_LIBS = 
INSTALL = /usr/bin/install -c
INSTALL_DATA = ${INSTALL} -m 644
INSTALL_PROGRAM = ${INSTALL}
INSTALL_SCRIPT = ${INSTALL}
INSTALL_STRIP_PROGRAM = $(install_sh) -c -s
INSTOBJEXT = .mo
INTLLIBS = 
INTLTOOL_CAVES_RULE = %.caves:     %.caves.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_DESKTOP_RULE = %.desktop:   %.desktop.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_DIRECTORY_RULE = %.directory: %.directory.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_EXTRACT = /usr/bin/intltool-extract
INTLTOOL_KBD_RULE = %.kbd:       %.kbd.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -m -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_KEYS_RULE = %.keys:      %.keys.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -k -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_MERGE = /usr/bin/intltool-merge
INTLTOOL_OAF_RULE = %.oaf:       %.oaf.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -o -p $(top_srcdir)/po $< $@
INTLTOOL_PERL = /usr/bin/perl
INTLTOOL_POLICY_RULE = %.policy:    %.policy.in    $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_PONG_RULE = %.pong:      %.pong.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_PROP_RULE = %.prop:      %.prop.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_SCHEMAS_RULE = %.schemas:   %.schemas.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -s -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_SERVER_RULE = %.server:    %.server.in    $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -o -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_SERVICE_RULE = %.service: %.service.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_SHEET_RULE = %.sheet:     %.sheet.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_SOUNDLIST_RULE = %.soundlist: %.soundlist.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_THEME_RULE = %.theme:     %.theme.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_UI_RULE = %.ui:        %.ui.in        $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_UPDATE = /usr/bin/intltool-update
INTLTOOL_XAM_RULE = %.xam:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
INTLTOOL_XML_NOMERGE_RULE = %.xml:       %.xml.in       $(INTLTOOL_MERGE) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u /tmp $< $@
INTLTOOL_XML_RULE = %.xml:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
LDADD =  -lnsl -lpthread
LDFLAGS =  -L/usr/local/lib -L/usr/local/lib
LIBGGZ_INCLUDES = -I /usr/include
LIBGGZ_LDFLAGS = -L/usr/lib
LIBOBJS = 
LIBS = 
LIBTOOL = $(SHELL) $(top_builddir)/libtool
LIB_ASYNC = 
LIB_GCRYPT = -lgcrypt
LIB_GGZ = -lggz
LIB_GGZDMOD = 
LIB_GGZMOD = -lggzmod
LIB_GGZTLS = 
LIB_GGZ_GTK = $(top_builddir)/dependencies/ggz-gtk/libggz-gtk.la
LN_S = ln -s
LTLIBOBJS = 
MAKEINFO = ${SHELL} /home/jordan/Downloads/gnome-games-2.22.3/missing --run makeinfo
MKDIR_P = /bin/mkdir -p
MKINSTALLDIRS = ./mkinstalldirs
MSGFMT = /usr/bin/msgfmt
MSGFMT_OPTS = -c
MSGMERGE = /usr/bin/msgmerge
NMEDIT = 
OBJDUMP = objdump
OBJEXT = o
OMF_DIR = ${datadir}/omf
PACKAGE = gnome-games
PACKAGE_BUGREPORT = http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games
PACKAGE_NAME = GNOME Games
PACKAGE_STRING = GNOME Games 2.22.3
PACKAGE_TARNAME = gnome-games
PACKAGE_VERSION = 2.22.3
PATH_SEPARATOR = :
PKG_CONFIG = /usr/bin/pkg-config
POFILES = 
POSUB = po
PO_IN_DATADIR_FALSE = 
PO_IN_DATADIR_TRUE = 
PYGTK_CFLAGS = -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
PYGTK_LIBS = -lffi -lgobject-2.0 -lglib-2.0  
PYTHON = /usr/bin/python
PYTHON_EXEC_PREFIX = ${exec_prefix}
PYTHON_PLATFORM = linux2
PYTHON_PREFIX = ${prefix}
PYTHON_VERSION = 2.5
RANLIB = ranlib
RSVG_CFLAGS = -I/usr/include/librsvg-2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  
RSVG_LIBS = -lrsvg-2 -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lcairo  
SDL_CFLAGS = -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT
SDL_CONFIG = /usr/bin/sdl-config
SDL_LIBS = -L/usr/lib -lSDL
SDL_MIXER_CFLAGS =  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT
SDL_MIXER_LIBS =  -L/usr/lib -lSDL -lSDL_mixer
SED = /bin/sed
SET_MAKE = 
SHELL = /bin/bash
STRIP = strip
USE_NLS = yes
VERSION = 2.22.3
WARN_CFLAGS = -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare 
WARN_CXXFLAGS = -g -O2 -Wall -Wno-unused -Wshadow -Woverloaded-virtual 
XGETTEXT = /usr/bin/xgettext
abs_builddir = /home/jordan/Downloads/gnome-games-2.22.3/mahjongg
abs_srcdir = /home/jordan/Downloads/gnome-games-2.22.3/mahjongg
abs_top_builddir = /home/jordan/Downloads/gnome-games-2.22.3
abs_top_srcdir = /home/jordan/Downloads/gnome-games-2.22.3
ac_ct_CC = gcc
ac_ct_CXX = g++
ac_ct_F77 = 
allgames = aisleriot blackjack gnometris gnect gnomine same-gnome mahjongg gtali gnotravex gnotski glines iagno glchess gnobots2 gnibbles gnome-sudoku
am__include = include
am__leading_dot = .
am__quote = 
am__tar = ${AMTAR} chof - "$$tardir"
am__untar = ${AMTAR} xf -
bindir = ${exec_prefix}/bin
build = i686-pc-linux-gnu
build_alias = 
build_cpu = i686
build_os = linux-gnu
build_vendor = pc
builddir = .
datadir = ${datarootdir}
datarootdir = ${prefix}/share
docdir = ${datarootdir}/doc/${PACKAGE_TARNAME}
dvidir = ${docdir}
exec_prefix = ${prefix}
gamelist = aisleriot blackjack gnometris gnect gnomine same-gnome mahjongg gtali gnotravex gnotski glines iagno glchess gnobots2 gnibbles gnome-sudoku
ggz_config = 
ggzdatadir = ${datadir}/ggz
ggzdconfdir = 
ggzddatadir = 
ggzdexecmoddir = 
ggzdexecmodpath = 
ggzdmod_includes = 
ggzdmod_libraries = 
ggzexecmoddir = ${libdir}/ggz
ggzmod_includes = /usr/include
ggzmod_libraries = /usr/lib
ggzmoduleconfdir = 
host = i686-pc-linux-gnu
host_alias = 
host_cpu = i686
host_os = linux-gnu
host_vendor = pc
htmldir = ${docdir}
includedir = ${prefix}/include
infodir = ${datarootdir}/info
install_sh = $(SHELL) /home/jordan/Downloads/gnome-games-2.22.3/install-sh
libdir = ${exec_prefix}/lib
libexecdir = ${exec_prefix}/libexec
libggz_includes = /usr/include
libggz_libraries = /usr/lib
localedir = ${datarootdir}/locale
localstatedir = ${prefix}/var
mandir = ${datarootdir}/man
mkdir_p = /bin/mkdir -p
oldincludedir = /usr/include
packagesrcdir = 
pdfdir = ${docdir}
pkgpyexecdir = ${pyexecdir}/gnome-games
pkgpythondir = ${pythondir}/gnome-games
prefix = /usr/local
program_transform_name = s,x,x,
psdir = ${docdir}
pyexecdir = ${exec_prefix}/lib/python2.5/site-packages
pythondir = ${prefix}/lib/python2.5/site-packages
sbindir = ${exec_prefix}/sbin
scoredir = ${localstatedir}/games
scores_group = games
scores_user = games
setgid = true
sharedstatedir = ${prefix}/com
srcdir = .
sysconfdir = ${prefix}/etc
target_alias = 
top_builddir = ..
top_srcdir = ..
SUBDIRS = help
NULL = 
mapdir = $(pkgdatadir)/mahjongg/maps
map_DATA = \
	mahjongg.map	\
	$(NULL)

pixmapdir = $(datadir)/pixmaps/mahjongg
pixmap_DATA = \
	smooth.png	\
	postmodern.svg	\
	$(NULL)

mahjongg_SOURCES = \
	drawing.c	\
	drawing.h	\
	mahjongg.c	\
	mahjongg.h	\
	maps.c		\
	maps.h		\
	solubility.c	\
	solubility.h	\
	translatable_game_names.h	\
	$(NULL)

mahjongg_CPPFLAGS = \
	-I$(top_srcdir)					\
	-DGNOMELOCALEDIR=\""$(datadir)/locale"\"	\
	-DDATADIR="\"$(datadir)\""			\
	-DPIXMAPDIR="\"$(pixmapdir)\""			\
	-DMAPDIR="\"$(mapdir)\""			\
	$(AM_CPPFLAGS)

mahjongg_CFLAGS = $(GTK_CFLAGS) $(AM_CFLAGS) $(am__append_1) \
	$(am__append_3) $(am__append_5)
mahjongg_LDADD = $(top_builddir)/libgames-support/libgames-support.la \
	$(GTK_LIBS) $(INTLLIBS) $(NULL) $(am__append_2) \
	$(am__append_4) $(am__append_6)
schema_in_files = mahjongg.schemas.in
schemadir = $(GCONF_SCHEMA_FILE_DIR)
schema_DATA = $(schema_in_files:.schemas.in=.schemas)
desktop_in_files = mahjongg.desktop.in.in
desktopdir = $(datadir)/applications
desktop_DATA = $(desktop_in_files:.desktop.in.in=.desktop)
EXTRA_DIST = \
	$(pixmap_DATA)		\
	$(schema_in_files)	\
	$(map_DATA)		\
	$(NULL)

CLEANFILES = $(desktop_DATA) $(schema_DATA)
DISTCLEANFILES = $(desktop_DATA) $(schema_DATA)
all: all-recursive

.SUFFIXES:
.SUFFIXES: .c .lo .o .obj
$(srcdir)/Makefile.in:  $(srcdir)/Makefile.am  $(am__configure_deps)
	@for dep in $?; do \
	  case '$(am__configure_deps)' in \
	    *$$dep*) \
	      cd $(top_builddir) && $(MAKE) $(AM_MAKEFLAGS) am--refresh \
		&& exit 0; \
	      exit 1;; \
	  esac; \
	done; \
	echo ' cd $(top_srcdir) && $(AUTOMAKE) --foreign  mahjongg/Makefile'; \
	cd $(top_srcdir) && \
	  $(AUTOMAKE) --foreign  mahjongg/Makefile
.PRECIOUS: Makefile
Makefile: $(srcdir)/Makefile.in $(top_builddir)/config.status
	@case '$?' in \
	  *config.status*) \
	    cd $(top_builddir) && $(MAKE) $(AM_MAKEFLAGS) am--refresh;; \
	  *) \
	    echo ' cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@ $(am__depfiles_maybe)'; \
	    cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@ $(am__depfiles_maybe);; \
	esac;

$(top_builddir)/config.status: $(top_srcdir)/configure $(CONFIG_STATUS_DEPENDENCIES)
	cd $(top_builddir) && $(MAKE) $(AM_MAKEFLAGS) am--refresh

$(top_srcdir)/configure:  $(am__configure_deps)
	cd $(top_builddir) && $(MAKE) $(AM_MAKEFLAGS) am--refresh
$(ACLOCAL_M4):  $(am__aclocal_m4_deps)
	cd $(top_builddir) && $(MAKE) $(AM_MAKEFLAGS) am--refresh
mahjongg.desktop.in: $(top_builddir)/config.status $(srcdir)/mahjongg.desktop.in.in
	cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@
install-binPROGRAMS: $(bin_PROGRAMS)
	@$(NORMAL_INSTALL)
	test -z "$(bindir)" || $(MKDIR_P) "$(DESTDIR)$(bindir)"
	@list='$(bin_PROGRAMS)'; for p in $$list; do \
	  p1=`echo $$p|sed 's/$(EXEEXT)$$//'`; \
	  if test -f $$p \
	     || test -f $$p1 \
	  ; then \
	    f=`echo "$$p1" | sed 's,^.*/,,;$(transform);s/$$/$(EXEEXT)/'`; \
	   echo " $(INSTALL_PROGRAM_ENV) $(LIBTOOL) $(AM_LIBTOOLFLAGS) $(LIBTOOLFLAGS) --mode=install $(binPROGRAMS_INSTALL) '$$p' '$(DESTDIR)$(bindir)/$$f'"; \
	   $(INSTALL_PROGRAM_ENV) $(LIBTOOL) $(AM_LIBTOOLFLAGS) $(LIBTOOLFLAGS) --mode=install $(binPROGRAMS_INSTALL) "$$p" "$(DESTDIR)$(bindir)/$$f" || exit 1; \
	  else :; fi; \
	done

uninstall-binPROGRAMS:
	@$(NORMAL_UNINSTALL)
	@list='$(bin_PROGRAMS)'; for p in $$list; do \
	  f=`echo "$$p" | sed 's,^.*/,,;s/$(EXEEXT)$$//;$(transform);s/$$/$(EXEEXT)/'`; \
	  echo " rm -f '$(DESTDIR)$(bindir)/$$f'"; \
	  rm -f "$(DESTDIR)$(bindir)/$$f"; \
	done

clean-binPROGRAMS:
	@list='$(bin_PROGRAMS)'; for p in $$list; do \
	  f=`echo $$p|sed 's/$(EXEEXT)$$//'`; \
	  echo " rm -f $$p $$f"; \
	  rm -f $$p $$f ; \
	done
mahjongg$(EXEEXT): $(mahjongg_OBJECTS) $(mahjongg_DEPENDENCIES) 
	@rm -f mahjongg$(EXEEXT)
	$(mahjongg_LINK) $(mahjongg_OBJECTS) $(mahjongg_LDADD) $(LIBS)

mostlyclean-compile:
	-rm -f *.$(OBJEXT)

distclean-compile:
	-rm -f *.tab.c

include ./$(DEPDIR)/mahjongg-drawing.Po
include ./$(DEPDIR)/mahjongg-mahjongg.Po
include ./$(DEPDIR)/mahjongg-maps.Po
include ./$(DEPDIR)/mahjongg-solubility.Po

.c.o:
	$(COMPILE) -MT $@ -MD -MP -MF $(DEPDIR)/$*.Tpo -c -o $@ $<
	mv -f $(DEPDIR)/$*.Tpo $(DEPDIR)/$*.Po
#	source='$<' object='$@' libtool=no \
#	DEPDIR=$(DEPDIR) $(CCDEPMODE) $(depcomp) \
#	$(COMPILE) -c $<

.c.obj:
	$(COMPILE) -MT $@ -MD -MP -MF $(DEPDIR)/$*.Tpo -c -o $@ `$(CYGPATH_W) '$<'`
	mv -f $(DEPDIR)/$*.Tpo $(DEPDIR)/$*.Po
#	source='$<' object='$@' libtool=no \
#	DEPDIR=$(DEPDIR) $(CCDEPMODE) $(depcomp) \
#	$(COMPILE) -c `$(CYGPATH_W) '$<'`

.c.lo:
	$(LTCOMPILE) -MT $@ -MD -MP -MF $(DEPDIR)/$*.Tpo -c -o $@ $<
	mv -f $(DEPDIR)/$*.Tpo $(DEPDIR)/$*.Plo
#	source='$<' object='$@' libtool=yes \
#	DEPDIR=$(DEPDIR) $(CCDEPMODE) $(depcomp) \
#	$(LTCOMPILE) -c -o $@ $<

mahjongg-drawing.o: drawing.c
	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -MT mahjongg-drawing.o -MD -MP -MF $(DEPDIR)/mahjongg-drawing.Tpo -c -o mahjongg-drawing.o `test -f 'drawing.c' || echo '$(srcdir)/'`drawing.c
	mv -f $(DEPDIR)/mahjongg-drawing.Tpo $(DEPDIR)/mahjongg-drawing.Po
#	source='drawing.c' object='mahjongg-drawing.o' libtool=no \
#	DEPDIR=$(DEPDIR) $(CCDEPMODE) $(depcomp) \
#	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -c -o mahjongg-drawing.o `test -f 'drawing.c' || echo '$(srcdir)/'`drawing.c

mahjongg-drawing.obj: drawing.c
	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -MT mahjongg-drawing.obj -MD -MP -MF $(DEPDIR)/mahjongg-drawing.Tpo -c -o mahjongg-drawing.obj `if test -f 'drawing.c'; then $(CYGPATH_W) 'drawing.c'; else $(CYGPATH_W) '$(srcdir)/drawing.c'; fi`
	mv -f $(DEPDIR)/mahjongg-drawing.Tpo $(DEPDIR)/mahjongg-drawing.Po
#	source='drawing.c' object='mahjongg-drawing.obj' libtool=no \
#	DEPDIR=$(DEPDIR) $(CCDEPMODE) $(depcomp) \
#	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -c -o mahjongg-drawing.obj `if test -f 'drawing.c'; then $(CYGPATH_W) 'drawing.c'; else $(CYGPATH_W) '$(srcdir)/drawing.c'; fi`

mahjongg-mahjongg.o: mahjongg.c
	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -MT mahjongg-mahjongg.o -MD -MP -MF $(DEPDIR)/mahjongg-mahjongg.Tpo -c -o mahjongg-mahjongg.o `test -f 'mahjongg.c' || echo '$(srcdir)/'`mahjongg.c
	mv -f $(DEPDIR)/mahjongg-mahjongg.Tpo $(DEPDIR)/mahjongg-mahjongg.Po
#	source='mahjongg.c' object='mahjongg-mahjongg.o' libtool=no \
#	DEPDIR=$(DEPDIR) $(CCDEPMODE) $(depcomp) \
#	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -c -o mahjongg-mahjongg.o `test -f 'mahjongg.c' || echo '$(srcdir)/'`mahjongg.c

mahjongg-mahjongg.obj: mahjongg.c
	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -MT mahjongg-mahjongg.obj -MD -MP -MF $(DEPDIR)/mahjongg-mahjongg.Tpo -c -o mahjongg-mahjongg.obj `if test -f 'mahjongg.c'; then $(CYGPATH_W) 'mahjongg.c'; else $(CYGPATH_W) '$(srcdir)/mahjongg.c'; fi`
	mv -f $(DEPDIR)/mahjongg-mahjongg.Tpo $(DEPDIR)/mahjongg-mahjongg.Po
#	source='mahjongg.c' object='mahjongg-mahjongg.obj' libtool=no \
#	DEPDIR=$(DEPDIR) $(CCDEPMODE) $(depcomp) \
#	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -c -o mahjongg-mahjongg.obj `if test -f 'mahjongg.c'; then $(CYGPATH_W) 'mahjongg.c'; else $(CYGPATH_W) '$(srcdir)/mahjongg.c'; fi`

mahjongg-maps.o: maps.c
	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -MT mahjongg-maps.o -MD -MP -MF $(DEPDIR)/mahjongg-maps.Tpo -c -o mahjongg-maps.o `test -f 'maps.c' || echo '$(srcdir)/'`maps.c
	mv -f $(DEPDIR)/mahjongg-maps.Tpo $(DEPDIR)/mahjongg-maps.Po
#	source='maps.c' object='mahjongg-maps.o' libtool=no \
#	DEPDIR=$(DEPDIR) $(CCDEPMODE) $(depcomp) \
#	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -c -o mahjongg-maps.o `test -f 'maps.c' || echo '$(srcdir)/'`maps.c

mahjongg-maps.obj: maps.c
	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -MT mahjongg-maps.obj -MD -MP -MF $(DEPDIR)/mahjongg-maps.Tpo -c -o mahjongg-maps.obj `if test -f 'maps.c'; then $(CYGPATH_W) 'maps.c'; else $(CYGPATH_W) '$(srcdir)/maps.c'; fi`
	mv -f $(DEPDIR)/mahjongg-maps.Tpo $(DEPDIR)/mahjongg-maps.Po
#	source='maps.c' object='mahjongg-maps.obj' libtool=no \
#	DEPDIR=$(DEPDIR) $(CCDEPMODE) $(depcomp) \
#	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -c -o mahjongg-maps.obj `if test -f 'maps.c'; then $(CYGPATH_W) 'maps.c'; else $(CYGPATH_W) '$(srcdir)/maps.c'; fi`

mahjongg-solubility.o: solubility.c
	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -MT mahjongg-solubility.o -MD -MP -MF $(DEPDIR)/mahjongg-solubility.Tpo -c -o mahjongg-solubility.o `test -f 'solubility.c' || echo '$(srcdir)/'`solubility.c
	mv -f $(DEPDIR)/mahjongg-solubility.Tpo $(DEPDIR)/mahjongg-solubility.Po
#	source='solubility.c' object='mahjongg-solubility.o' libtool=no \
#	DEPDIR=$(DEPDIR) $(CCDEPMODE) $(depcomp) \
#	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -c -o mahjongg-solubility.o `test -f 'solubility.c' || echo '$(srcdir)/'`solubility.c

mahjongg-solubility.obj: solubility.c
	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -MT mahjongg-solubility.obj -MD -MP -MF $(DEPDIR)/mahjongg-solubility.Tpo -c -o mahjongg-solubility.obj `if test -f 'solubility.c'; then $(CYGPATH_W) 'solubility.c'; else $(CYGPATH_W) '$(srcdir)/solubility.c'; fi`
	mv -f $(DEPDIR)/mahjongg-solubility.Tpo $(DEPDIR)/mahjongg-solubility.Po
#	source='solubility.c' object='mahjongg-solubility.obj' libtool=no \
#	DEPDIR=$(DEPDIR) $(CCDEPMODE) $(depcomp) \
#	$(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(mahjongg_CPPFLAGS) $(CPPFLAGS) $(mahjongg_CFLAGS) $(CFLAGS) -c -o mahjongg-solubility.obj `if test -f 'solubility.c'; then $(CYGPATH_W) 'solubility.c'; else $(CYGPATH_W) '$(srcdir)/solubility.c'; fi`

mostlyclean-libtool:
	-rm -f *.lo

clean-libtool:
	-rm -rf .libs _libs
install-desktopDATA: $(desktop_DATA)
	@$(NORMAL_INSTALL)
	test -z "$(desktopdir)" || $(MKDIR_P) "$(DESTDIR)$(desktopdir)"
	@list='$(desktop_DATA)'; for p in $$list; do \
	  if test -f "$$p"; then d=; else d="$(srcdir)/"; fi; \
	  f=$(am__strip_dir) \
	  echo " $(desktopDATA_INSTALL) '$$d$$p' '$(DESTDIR)$(desktopdir)/$$f'"; \
	  $(desktopDATA_INSTALL) "$$d$$p" "$(DESTDIR)$(desktopdir)/$$f"; \
	done

uninstall-desktopDATA:
	@$(NORMAL_UNINSTALL)
	@list='$(desktop_DATA)'; for p in $$list; do \
	  f=$(am__strip_dir) \
	  echo " rm -f '$(DESTDIR)$(desktopdir)/$$f'"; \
	  rm -f "$(DESTDIR)$(desktopdir)/$$f"; \
	done
install-mapDATA: $(map_DATA)
	@$(NORMAL_INSTALL)
	test -z "$(mapdir)" || $(MKDIR_P) "$(DESTDIR)$(mapdir)"
	@list='$(map_DATA)'; for p in $$list; do \
	  if test -f "$$p"; then d=; else d="$(srcdir)/"; fi; \
	  f=$(am__strip_dir) \
	  echo " $(mapDATA_INSTALL) '$$d$$p' '$(DESTDIR)$(mapdir)/$$f'"; \
	  $(mapDATA_INSTALL) "$$d$$p" "$(DESTDIR)$(mapdir)/$$f"; \
	done

uninstall-mapDATA:
	@$(NORMAL_UNINSTALL)
	@list='$(map_DATA)'; for p in $$list; do \
	  f=$(am__strip_dir) \
	  echo " rm -f '$(DESTDIR)$(mapdir)/$$f'"; \
	  rm -f "$(DESTDIR)$(mapdir)/$$f"; \
	done
install-pixmapDATA: $(pixmap_DATA)
	@$(NORMAL_INSTALL)
	test -z "$(pixmapdir)" || $(MKDIR_P) "$(DESTDIR)$(pixmapdir)"
	@list='$(pixmap_DATA)'; for p in $$list; do \
	  if test -f "$$p"; then d=; else d="$(srcdir)/"; fi; \
	  f=$(am__strip_dir) \
	  echo " $(pixmapDATA_INSTALL) '$$d$$p' '$(DESTDIR)$(pixmapdir)/$$f'"; \
	  $(pixmapDATA_INSTALL) "$$d$$p" "$(DESTDIR)$(pixmapdir)/$$f"; \
	done

uninstall-pixmapDATA:
	@$(NORMAL_UNINSTALL)
	@list='$(pixmap_DATA)'; for p in $$list; do \
	  f=$(am__strip_dir) \
	  echo " rm -f '$(DESTDIR)$(pixmapdir)/$$f'"; \
	  rm -f "$(DESTDIR)$(pixmapdir)/$$f"; \
	done
install-schemaDATA: $(schema_DATA)
	@$(NORMAL_INSTALL)
	test -z "$(schemadir)" || $(MKDIR_P) "$(DESTDIR)$(schemadir)"
	@list='$(schema_DATA)'; for p in $$list; do \
	  if test -f "$$p"; then d=; else d="$(srcdir)/"; fi; \
	  f=$(am__strip_dir) \
	  echo " $(schemaDATA_INSTALL) '$$d$$p' '$(DESTDIR)$(schemadir)/$$f'"; \
	  $(schemaDATA_INSTALL) "$$d$$p" "$(DESTDIR)$(schemadir)/$$f"; \
	done

uninstall-schemaDATA:
	@$(NORMAL_UNINSTALL)
	@list='$(schema_DATA)'; for p in $$list; do \
	  f=$(am__strip_dir) \
	  echo " rm -f '$(DESTDIR)$(schemadir)/$$f'"; \
	  rm -f "$(DESTDIR)$(schemadir)/$$f"; \
	done

# This directory's subdirectories are mostly independent; you can cd
# into them and run `make' without going through this Makefile.
# To change the values of `make' variables: instead of editing Makefiles,
# (1) if the variable is set in `config.status', edit `config.status'
#     (which will cause the Makefiles to be regenerated when you run `make');
# (2) otherwise, pass the desired values on the `make' command line.
$(RECURSIVE_TARGETS):
	@failcom='exit 1'; \
	for f in x $$MAKEFLAGS; do \
	  case $$f in \
	    *=* | --[!k]*);; \
	    *k*) failcom='fail=yes';; \
	  esac; \
	done; \
	dot_seen=no; \
	target=`echo $@ | sed s/-recursive//`; \
	list='$(SUBDIRS)'; for subdir in $$list; do \
	  echo "Making $$target in $$subdir"; \
	  if test "$$subdir" = "."; then \
	    dot_seen=yes; \
	    local_target="$$target-am"; \
	  else \
	    local_target="$$target"; \
	  fi; \
	  (cd $$subdir && $(MAKE) $(AM_MAKEFLAGS) $$local_target) \
	  || eval $$failcom; \
	done; \
	if test "$$dot_seen" = "no"; then \
	  $(MAKE) $(AM_MAKEFLAGS) "$$target-am" || exit 1; \
	fi; test -z "$$fail"

$(RECURSIVE_CLEAN_TARGETS):
	@failcom='exit 1'; \
	for f in x $$MAKEFLAGS; do \
	  case $$f in \
	    *=* | --[!k]*);; \
	    *k*) failcom='fail=yes';; \
	  esac; \
	done; \
	dot_seen=no; \
	case "$@" in \
	  distclean-* | maintainer-clean-*) list='$(DIST_SUBDIRS)' ;; \
	  *) list='$(SUBDIRS)' ;; \
	esac; \
	rev=''; for subdir in $$list; do \
	  if test "$$subdir" = "."; then :; else \
	    rev="$$subdir $$rev"; \
	  fi; \
	done; \
	rev="$$rev ."; \
	target=`echo $@ | sed s/-recursive//`; \
	for subdir in $$rev; do \
	  echo "Making $$target in $$subdir"; \
	  if test "$$subdir" = "."; then \
	    local_target="$$target-am"; \
	  else \
	    local_target="$$target"; \
	  fi; \
	  (cd $$subdir && $(MAKE) $(AM_MAKEFLAGS) $$local_target) \
	  || eval $$failcom; \
	done && test -z "$$fail"
tags-recursive:
	list='$(SUBDIRS)'; for subdir in $$list; do \
	  test "$$subdir" = . || (cd $$subdir && $(MAKE) $(AM_MAKEFLAGS) tags); \
	done
ctags-recursive:
	list='$(SUBDIRS)'; for subdir in $$list; do \
	  test "$$subdir" = . || (cd $$subdir && $(MAKE) $(AM_MAKEFLAGS) ctags); \
	done

ID: $(HEADERS) $(SOURCES) $(LISP) $(TAGS_FILES)
	list='$(SOURCES) $(HEADERS) $(LISP) $(TAGS_FILES)'; \
	unique=`for i in $$list; do \
	    if test -f "$$i"; then echo $$i; else echo $(srcdir)/$$i; fi; \
	  done | \
	  $(AWK) '{ files[$$0] = 1; nonemtpy = 1; } \
	      END { if (nonempty) { for (i in files) print i; }; }'`; \
	mkid -fID $$unique
tags: TAGS

TAGS: tags-recursive $(HEADERS) $(SOURCES)  $(TAGS_DEPENDENCIES) \
		$(TAGS_FILES) $(LISP)
	tags=; \
	here=`pwd`; \
	if ($(ETAGS) --etags-include --version) >/dev/null 2>&1; then \
	  include_option=--etags-include; \
	  empty_fix=.; \
	else \
	  include_option=--include; \
	  empty_fix=; \
	fi; \
	list='$(SUBDIRS)'; for subdir in $$list; do \
	  if test "$$subdir" = .; then :; else \
	    test ! -f $$subdir/TAGS || \
	      tags="$$tags $$include_option=$$here/$$subdir/TAGS"; \
	  fi; \
	done; \
	list='$(SOURCES) $(HEADERS)  $(LISP) $(TAGS_FILES)'; \
	unique=`for i in $$list; do \
	    if test -f "$$i"; then echo $$i; else echo $(srcdir)/$$i; fi; \
	  done | \
	  $(AWK) '{ files[$$0] = 1; nonempty = 1; } \
	      END { if (nonempty) { for (i in files) print i; }; }'`; \
	if test -z "$(ETAGS_ARGS)$$tags$$unique"; then :; else \
	  test -n "$$unique" || unique=$$empty_fix; \
	  $(ETAGS) $(ETAGSFLAGS) $(AM_ETAGSFLAGS) $(ETAGS_ARGS) \
	    $$tags $$unique; \
	fi
ctags: CTAGS
CTAGS: ctags-recursive $(HEADERS) $(SOURCES)  $(TAGS_DEPENDENCIES) \
		$(TAGS_FILES) $(LISP)
	tags=; \
	list='$(SOURCES) $(HEADERS)  $(LISP) $(TAGS_FILES)'; \
	unique=`for i in $$list; do \
	    if test -f "$$i"; then echo $$i; else echo $(srcdir)/$$i; fi; \
	  done | \
	  $(AWK) '{ files[$$0] = 1; nonempty = 1; } \
	      END { if (nonempty) { for (i in files) print i; }; }'`; \
	test -z "$(CTAGS_ARGS)$$tags$$unique" \
	  || $(CTAGS) $(CTAGSFLAGS) $(AM_CTAGSFLAGS) $(CTAGS_ARGS) \
	     $$tags $$unique

GTAGS:
	here=`$(am__cd) $(top_builddir) && pwd` \
	  && cd $(top_srcdir) \
	  && gtags -i $(GTAGS_ARGS) $$here

distclean-tags:
	-rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags

distdir: $(DISTFILES)
	@srcdirstrip=`echo "$(srcdir)" | sed 's/[].[^$$\\*]/\\\\&/g'`; \
	topsrcdirstrip=`echo "$(top_srcdir)" | sed 's/[].[^$$\\*]/\\\\&/g'`; \
	list='$(DISTFILES)'; \
	  dist_files=`for file in $$list; do echo $$file; done | \
	  sed -e "s|^$$srcdirstrip/||;t" \
	      -e "s|^$$topsrcdirstrip/|$(top_builddir)/|;t"`; \
	case $$dist_files in \
	  */*) $(MKDIR_P) `echo "$$dist_files" | \
			   sed '/\//!d;s|^|$(distdir)/|;s,/[^/]*$$,,' | \
			   sort -u` ;; \
	esac; \
	for file in $$dist_files; do \
	  if test -f $$file || test -d $$file; then d=.; else d=$(srcdir); fi; \
	  if test -d $$d/$$file; then \
	    dir=`echo "/$$file" | sed -e 's,/[^/]*$$,,'`; \
	    if test -d $(srcdir)/$$file && test $$d != $(srcdir); then \
	      cp -pR $(srcdir)/$$file $(distdir)$$dir || exit 1; \
	    fi; \
	    cp -pR $$d/$$file $(distdir)$$dir || exit 1; \
	  else \
	    test -f $(distdir)/$$file \
	    || cp -p $$d/$$file $(distdir)/$$file \
	    || exit 1; \
	  fi; \
	done
	list='$(DIST_SUBDIRS)'; for subdir in $$list; do \
	  if test "$$subdir" = .; then :; else \
	    test -d "$(distdir)/$$subdir" \
	    || $(MKDIR_P) "$(distdir)/$$subdir" \
	    || exit 1; \
	    distdir=`$(am__cd) $(distdir) && pwd`; \
	    top_distdir=`$(am__cd) $(top_distdir) && pwd`; \
	    (cd $$subdir && \
	      $(MAKE) $(AM_MAKEFLAGS) \
	        top_distdir="$$top_distdir" \
	        distdir="$$distdir/$$subdir" \
		am__remove_distdir=: \
		am__skip_length_check=: \
	        distdir) \
	      || exit 1; \
	  fi; \
	done
check-am: all-am
check: check-recursive
all-am: Makefile $(PROGRAMS) $(DATA)
installdirs: installdirs-recursive
installdirs-am:
	for dir in "$(DESTDIR)$(bindir)" "$(DESTDIR)$(desktopdir)" "$(DESTDIR)$(mapdir)" "$(DESTDIR)$(pixmapdir)" "$(DESTDIR)$(schemadir)"; do \
	  test -z "$$dir" || $(MKDIR_P) "$$dir"; \
	done
install: install-recursive
install-exec: install-exec-recursive
install-data: install-data-recursive
uninstall: uninstall-recursive

install-am: all-am
	@$(MAKE) $(AM_MAKEFLAGS) install-exec-am install-data-am

installcheck: installcheck-recursive
install-strip:
	$(MAKE) $(AM_MAKEFLAGS) INSTALL_PROGRAM="$(INSTALL_STRIP_PROGRAM)" \
	  install_sh_PROGRAM="$(INSTALL_STRIP_PROGRAM)" INSTALL_STRIP_FLAG=-s \
	  `test -z '$(STRIP)' || \
	    echo "INSTALL_PROGRAM_ENV=STRIPPROG='$(STRIP)'"` install
mostlyclean-generic:

clean-generic:
	-test -z "$(CLEANFILES)" || rm -f $(CLEANFILES)

distclean-generic:
	-test -z "$(CONFIG_CLEAN_FILES)" || rm -f $(CONFIG_CLEAN_FILES)
	-test -z "$(DISTCLEANFILES)" || rm -f $(DISTCLEANFILES)

maintainer-clean-generic:
	@echo "This command is intended for maintainers to use"
	@echo "it deletes files that may require special tools to rebuild."
clean: clean-recursive

clean-am: clean-binPROGRAMS clean-generic clean-libtool mostlyclean-am

distclean: distclean-recursive
	-rm -rf ./$(DEPDIR)
	-rm -f Makefile
distclean-am: clean-am distclean-compile distclean-generic \
	distclean-tags

dvi: dvi-recursive

dvi-am:

html: html-recursive

info: info-recursive

info-am:

install-data-am: install-data-local install-desktopDATA \
	install-mapDATA install-pixmapDATA install-schemaDATA

install-dvi: install-dvi-recursive

install-exec-am: install-binPROGRAMS

install-html: install-html-recursive

install-info: install-info-recursive

install-man:

install-pdf: install-pdf-recursive

install-ps: install-ps-recursive

installcheck-am:

maintainer-clean: maintainer-clean-recursive
	-rm -rf ./$(DEPDIR)
	-rm -f Makefile
maintainer-clean-am: distclean-am maintainer-clean-generic

mostlyclean: mostlyclean-recursive

mostlyclean-am: mostlyclean-compile mostlyclean-generic \
	mostlyclean-libtool

pdf: pdf-recursive

pdf-am:

ps: ps-recursive

ps-am:

uninstall-am: uninstall-binPROGRAMS uninstall-desktopDATA \
	uninstall-mapDATA uninstall-pixmapDATA uninstall-schemaDATA

.MAKE: $(RECURSIVE_CLEAN_TARGETS) $(RECURSIVE_TARGETS) install-am \
	install-strip

.PHONY: $(RECURSIVE_CLEAN_TARGETS) $(RECURSIVE_TARGETS) CTAGS GTAGS \
	all all-am check check-am clean clean-binPROGRAMS \
	clean-generic clean-libtool ctags ctags-recursive distclean \
	distclean-compile distclean-generic distclean-libtool \
	distclean-tags distdir dvi dvi-am html html-am info info-am \
	install install-am install-binPROGRAMS install-data \
	install-data-am install-data-local install-desktopDATA \
	install-dvi install-dvi-am install-exec install-exec-am \
	install-html install-html-am install-info install-info-am \
	install-man install-mapDATA install-pdf install-pdf-am \
	install-pixmapDATA install-ps install-ps-am install-schemaDATA \
	install-strip installcheck installcheck-am installdirs \
	installdirs-am maintainer-clean maintainer-clean-generic \
	mostlyclean mostlyclean-compile mostlyclean-generic \
	mostlyclean-libtool pdf pdf-am ps ps-am tags tags-recursive \
	uninstall uninstall-am uninstall-binPROGRAMS \
	uninstall-desktopDATA uninstall-mapDATA uninstall-pixmapDATA \
	uninstall-schemaDATA


install-schemas-local: $(schema_DATA)
	if test -z "$(DESTDIR)" ; then \
		for p in $^ ; do \
			GCONF_CONFIG_SOURCE=$(GCONF_SCHEMA_CONFIG_SOURCE) $(GCONFTOOL) --makefile-install-rule $$p 2>&1 > /dev/null; \
		done \
	fi

install-scorefiles-local:
	-$(mkinstalldirs) $(DESTDIR)$(scoredir)
	-for i in easy difficult confounding pyramid tictactoe cloud dragon bridges ziggurat; do \
		touch $(DESTDIR)$(scoredir)/mahjongg.$$i.scores; \
		chown $(scores_user):$(scores_group) $(DESTDIR)$(scoredir)/mahjongg.$$i.scores; \
		chmod 664 $(DESTDIR)$(scoredir)/mahjongg.$$i.scores; \
	done
	-if test "x$(setgid)" = "xtrue"; then chgrp $(scores_group) $(DESTDIR)$(bindir)/mahjongg && chmod 2555 $(DESTDIR)$(bindir)/mahjongg ; fi

install-data-local: install-schemas-local install-scorefiles-local

%.desktop:   %.desktop.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
%.schemas:   %.schemas.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -s -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@
# Tell versions [3.59,3.63) of GNU make to not export all variables.
# Otherwise a system limit (for SysV at least) may be exceeded.
.NOEXPORT:
```I'd really appreciate the help.  I hope this isn't too much trouble.  I've been at this for a few days now, and I successfully created the win32 executables only a few minutes ago.

---

### Post by Ptero-4 on 2009-02-23
> **monkeyking said:**
> You might be thinking about the Makefiles generated with autoconf and friends.

If the original poster is using a autoconf and automake Makfile,
the default is --prefix.
But he should use it with ./configure and not ./Makefile
I know about the "--prefix" switch in "./configure". It just was that I though the OP wanted to build his own customized Makefiles.

---

### Post by monkeyking on 2009-02-23
@dwhitney
thanks for your input, you are always helpful and informative.
I am surely to update my Makefile. You have explained the CC option before :)
and the reason it is not included is simply because I copied the Makefile from another package and had not updated it.


To the original poster.
If your Makefile is generated with autotools you shouldn't not change the Makefile itself,
but the arguments you give to

```
./configure ARGS
```

Can you compile your code by hand?
And if so, give us your the command you use to compile

---

### Post by dodle on 2009-03-09
> **bsharp said:**
> If it uses autoconf, there should be an argument called "prefix" that allows you to set a directory. E.G:

```
./configure --prefix=/usr/bin
make
make install
```

Thanks, that is what I was looking for.```
./configure --prefix=/path/to/directory
```

---

