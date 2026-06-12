---
title: "makefile, cpp-6, missing debug symbols"
date: 2016-10-07
forum: Packaging and Compiling Programs
---

### Post by kornelixgmx.de on 2016-10-07
The following makefile produces debug symbols in the executable with Ubuntu 16.04, but NOT with Ubuntu 16.10.
Specifically, addr2line produces only "??" outputs. How can I get the debug symbols again?

```

PROGRAM = zfuncstest
VERSION = 6.5
SOURCE = $(PROGRAM)-$(VERSION).cc

# defaults for parameters that may be pre-defined
CXXFLAGS += -Wall -ggdb
PREFIX ?= /usr
CPPFLAGS ?= -O0

# target install directories
BINDIR = $(PREFIX)/bin
SHAREDIR = $(PREFIX)/share/$(PROGRAM)
DATADIR = $(SHAREDIR)/data
ICONDIR = $(SHAREDIR)/icons
LOCALESDIR = $(SHAREDIR)/locales
DOCDIR = $(PREFIX)/share/doc/$(PROGRAM)
MANDIR = $(PREFIX)/share/man/man1
APPDATADIR = $(PREFIX)/share/appdata
MENUFILE = $(PREFIX)/share/applications/$(PROGRAM).desktop

CFLAGS = $(CXXFLAGS) -c `pkg-config --cflags gtk+-3.0`
CFLAGS += $(CPPFLAGS)
LIBS = `pkg-config --libs gtk+-3.0` -lpthread

$(PROGRAM): $(PROGRAM).o zfuncs.o
    $(CXX) $(LDFLAGS) -o $(PROGRAM) $(PROGRAM).o zfuncs.o $(LIBS)

$(PROGRAM).o: $(SOURCE)
    $(CXX) $(CFLAGS) -o $(PROGRAM).o $(SOURCE)

zfuncs.o: zfuncs.cc zfuncs.h
    $(CXX) $(CFLAGS) zfuncs.cc    \
          -D PREFIX=\"$(PREFIX)\" -D DOCDIR=\"$(DOCDIR)\"

install: $(PROGRAM) uninstall
    mkdir -p  $(DESTDIR)$(BINDIR)
    mkdir -p  $(DESTDIR)$(DATADIR)
    mkdir -p  $(DESTDIR)$(ICONDIR)
    mkdir -p  $(DESTDIR)$(LOCALESDIR)
    mkdir -p  $(DESTDIR)$(DOCDIR)
    mkdir -p  $(DESTDIR)$(MANDIR)
    mkdir -p  $(DESTDIR)$(PREFIX)/share/applications
    mkdir -p  $(DESTDIR)$(APPDATADIR)
    cp -f  $(PROGRAM) $(DESTDIR)$(BINDIR)
    cp -f -R  data/* $(DESTDIR)$(DATADIR)
    cp -f -R  icons/* $(DESTDIR)$(ICONDIR)
    cp -f -R  locales/* $(DESTDIR)$(LOCALESDIR)
    cp -f -R  doc/* $(DESTDIR)$(DOCDIR)
    gzip -f -9 $(DESTDIR)$(DOCDIR)/changelog
    # man page
    cp -f doc/$(PROGRAM).man $(PROGRAM).1
    gzip -f -9 $(PROGRAM).1
    cp $(PROGRAM).1.gz $(DESTDIR)$(MANDIR)
    rm -f $(PROGRAM).1.gz
    # menu (desktop) file
    cp -f desktop $(DESTDIR)$(MENUFILE)

uninstall:
    rm -f  $(DESTDIR)$(BINDIR)/$(PROGRAM)
    rm -f -R  $(DESTDIR)$(SHAREDIR)
    rm -f -R  $(DESTDIR)$(DOCDIR)
    rm -f  $(DESTDIR)$(MANDIR)/$(PROGRAM).1.gz
    rm -f  $(DESTDIR)$(MENUFILE)

clean: 
    rm -f  $(PROGRAM)
    rm -f  *.o

```

---

### Post by kornelixgmx.de on 2016-10-07
Correction: 
Debug symbols are present. **addr2line** utility no longer works, produces only "??:0"

---

### Post by kornelixgmx.de on 2016-10-08
SOLVED
The problem is that the library program backtrace_symbols() has changed its output format and the utility addr2line has been changed accordingly. After changing my source program to parse the new format, it works OK. The documentation for this change has been left behind somewhere.

---

