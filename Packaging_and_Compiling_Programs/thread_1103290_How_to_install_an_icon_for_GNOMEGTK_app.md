---
title: "How to install an icon for GNOME/GTK app?"
date: 2009-03-22
forum: Packaging and Compiling Programs
---

### Post by moma on 2009-03-22
Hello,
[COLOR="Red"][/COLOR]
How to make Makefile.am to install icon for a GTK/GNOME application?

[[img]http://bildr.no/thumb/367281.jpeg[/img]](http://bildr.no/view/367281)

My [Gscreendump...]("http://ubuntuforums.org/showthread.php?t=1096860") app installs itself and "gscreendump.desktop" file correctly, but what is the best way to make it put icon file (gscreendump.png) in right place?

Here's my Makefile.am.
The "dist_desktop_DATA = data/gscreendump.desktop" line seems to install gscreendump.desktop file in right place (in /usr/share/applications/gscreendump.desktop ). But what's the simplest way to install data/gscreendump.png (the icon) in /usr/share/icons/....?  

Should I just use xdg* tools?
---------------------------------------------------------------

[COLOR="Red"]EDIT: [/COLOR]Ok, I have now solved it.

I created a scalable SVG icon for Gscreendump. Then Makefile.am (or the final makefile) will install it to the  $(themedir)/$(size)/$(context) directory. Study the following lines:

[COLOR="DarkGreen"]# Install "gscreendump.svg" icon file 
themedir = $(datadir)/icons/gnome
size = scalable
context = apps

iconsdir = $(themedir)/$(size)/$(context)
icons_DATA = data/gscreendump.svg

EXTRA_DIST = autogen.sh  $(icons_DATA)[/COLOR]

It's easier to provide one scalable SVG icon instead of several PNG icons for all possible sizes 16x16,...,32x32,...48x48. 

This is my final Makefile.am. It installs both "gscreendump.desktop" and "gscreendump.svg" files to the right places (assume I).
```
## Process this file with automake to produce Makefile.in

SUBDIRS = src po

EXTRA_DIST = \
	autogen.sh \
        $(icons_DATA)

# Install "gscreendump.svg" icon file
themedir = $(datadir)/icons/gnome
size = scalable
context = apps

iconsdir = $(themedir)/$(size)/$(context)
icons_DATA = data/gscreendump.svg

# Install "gscreendump.desktop" file
desktopdir = $(datadir)/applications
dist_desktop_DATA = data/gscreendump.desktop

install-data-local:
	@$(NORMAL_INSTALL)
	if test -d $(srcdir)/pixmaps; then \
	  $(mkinstalldirs) $(DESTDIR)$(pkgdatadir)/pixmaps; \
	  for pixmap in $(srcdir)/pixmaps/*; do \
	    if test -f "$$pixmap"; then \
	      $(INSTALL_DATA) "$$pixmap" $(DESTDIR)$(pkgdatadir)/pixmaps; \
	    fi \
	  done \
	fi

	if test -f $(srcdir)/COPYING; then \
	    $(INSTALL_DATA) $(srcdir)/COPYING  $(DESTDIR)$(pkgdatadir); \
	fi

	if test -d $(srcdir)/commands; then \
	  $(mkinstalldirs) $(DESTDIR)$(pkgdatadir)/commands; \
	  cp -fr $(srcdir)/commands/*  $(DESTDIR)$(pkgdatadir)/commands/; \
	fi

	sed -i "s|__GSCREENDUMP_DATA_DIRECTORY__|$(DESTDIR)$(pkgdatadir)/|" $(DESTDIR)$(pkgdatadir)/commands/command.lst
	sed -i "s|__GSCREENDUMP_DATA_DIRECTORY__|$(DESTDIR)$(pkgdatadir)/|" $(DESTDIR)$(pkgdatadir)/commands/readme.txt


dist-hook:
	if test -d pixmaps; then \
	  mkdir $(distdir)/pixmaps; \
	  for pixmap in pixmaps/*; do \
	    if test -f "$$pixmap"; then \
	      cp -p "$$pixmap" $(distdir)/pixmaps; \
	    fi \
	  done \
	fi

	if test -f ./COPYING; then \
	  cp -p ./COPYING $(distdir); \
	fi

	if test -d commands; then \
	  mkdir $(distdir)/commands; \
	  cp -pfr commands/* $(distdir)/commands/; \
	fi

	sed -i "s|__GSCREENDUMP_DATA_DIRECTORY__|$(distdir)/|" $(distdir)/commands/command.lst
	sed -i "s|__GSCREENDUMP_DATA_DIRECTORY__|$(distdir)/|" $(distdir)/commands/readme.txt
```

Of course, I have created a data directory under gscreendump source.
$ [COLOR="Green"]pwd [/COLOR]
/media/sdb4/development/gscreendump

$ [COLOR="Green"]ls -l[/COLOR]
...
-rwxr-xr-x 1 moma moma 294855 2009-03-22 19:56 configure
drwxr-xr-x 2 moma moma   4096 2009-03-23 15:10 data
-rw-r--r-- 1 moma moma  11004 2009-03-15 09:25 INSTALL
-rw-r--r-- 1 moma moma   6459 2009-03-15 13:16 README
-rw-r--r-- 1 moma moma   1811 2009-03-23 15:10 Makefile.am
...

$ [COLOR="Green"]ls -l data[/COLOR]
-rw-r--r-- 1 moma moma   687 2009-03-23 12:55 gscreendump.desktop
-rw-r--r-- 1 moma moma 15614 2009-03-23 15:09 gscreendump.svg
----------------------

Please download and try the amazing Gscreendump already today ;-)
[http://code.google.com/p/gscreendump/wiki/PicturesAndScreenshots](http://code.google.com/p/gscreendump/wiki/PicturesAndScreenshots)
But read the [http://code.google.com/p/gscreendump/wiki/Installation](http://code.google.com/p/gscreendump/wiki/Installation) wiki first.

---

### Post by moma on 2009-03-23
I marked the thread as solved. Read the 1.st posting.

---

### Post by Shnatsel on 2009-03-24
Is there any way to avoid using automake and install some icons via basic makefile?

---

### Post by moma on 2009-03-26
Hello Shnatsel.
Sorry for a late reply.

Yes, you can easily add your own install rule and commands to a Makefile. Look at this example Makefile.
```

# Makefile
CC=gcc
CFLAGS=-Wall
LD=gcc
LDFLAGS=

OBJECTS=main.o
TARGET=main
INCLUDE=
LIB=

all: $(TARGET)

clean:
	rm $(TARGET) $(OBJECTS)

# Target
$(TARGET): $(OBJECTS) Makefile
	$(LD) $(LDFLAGS) -o $(TARGET) $(OBJECTS) $(LIB)

# Pseudo rules
%.o: %.c Makefile
	$(CC) $(CFLAGS) -o $@ -c $< $(INCLUDE)

%.o: %.cpp Makefile
	$(CPP) $(CPPFLAGS) -o $@ -c $< $(INCLUDE)


DESTIN_DIR=/usr/share/some_directory/

install:
	for icon in icons/*png; do \
	  echo "Installing icon: $$icon"; \
	  cp "$$icon" $(DESTIN_DIR); \
	done
```


The install: rule copies some icons to $(DESTIN_DIR). Notice that the shell variables must have two $s, like the "$$icon". 

Then you would run the **install** rule by typing:
$ [COLOR="SeaGreen"]make install[/COLOR] 
(normally as root or sudo)

Notice also that the first line of rule must start with a TAB character. Eg: 
[COLOR="Silver"][TAB][/COLOR] 	for ff in icons/*png; do \
         .....

More info [here...]("http://www.gnu.org/software/make/manual/make.html#Commands_002fSearch")

---

### Post by Shnatsel on 2009-03-27
Thank you very much! :D

---

### Post by Shnatsel on 2009-03-28
Moma, thank you a lot, now I can install my icons via make install, but now another problem arose: i can't create a .DEB package for Ubuntu. I'm using debcreator, and it fails some pre-build check. Does it require some files other than Makefile to bulid a package?

---

### Post by andrewsomething on 2009-03-29
> **moma said:**
> 
Ok, I have now solved it.

I created a scalable SVG icon for Gscreendump. Then Makefile.am (or the final makefile) will install it to the  $(themedir)/$(size)/$(context) directory. Study the following lines:

[COLOR="DarkGreen"]# Install "gscreendump.svg" icon file 
themedir = $(datadir)/icons/gnome
size = scalable
context = apps

iconsdir = $(themedir)/$(size)/$(context)
icons_DATA = data/gscreendump.svg

EXTRA_DIST = autogen.sh  $(icons_DATA)[/COLOR]


Hi,

You're installing your icon into the gnome icon theme's directory. That's not necessarily a problem as just about every one will have it installed, and most icon themes for GNOME will include gnome as well. But if I understand things correctly it is usually standard practice to install program icons to $(datadir)/icons/hicolor Every icon theme should have an includes on the hicolor theme.

---

