---
title: "Autotools question (code generator + library + executable)"
date: 2005-12-04
forum: Programming Talk
---

### Post by knipknap on 2005-12-04
Hi,

I am trying to fiddle with the Automake files for the following file structure:

.
|-Makefile.am
|-autogen.sh
|-configure.ac
|-data
| |-Makefile.am
| |-com.nokia.mcclient.service.in
| |-mcclient.desktop
| `-mcclient.desktop.in.in
|-libmcc
| |-Makefile
| |-McClient.c
| |-McClient.h
| |-McClient.marshall.list
| |-TcpListener.c
| |-TcpListener.h
| |-TcpListener.marshall.list
| `-test.c
|-po
| |-Makefile.am
| |-POTFILES.in
| `-en_GB.po
`-src
 |-Makefile.am
 |-appdata.h
 |-main.c
 `-ui
  |-callbacks.c
  |-callbacks.h
  |-interface.c
  `-interface.h


Current behavior:

- Using "make" in the libmcc/ directory successfully builds a binary out of test.c. That build also includes running a code generator that created four files out of *.marshall.list. The makefile is here:
[http://debain.org/stuff/mcrec/mcclient/libmcc/Makefile]("http://debain.org/stuff/mcrec/mcclient/libmcc/Makefile")

- Using "make" in the root directory builds a binary from src/main.c. The makefiles are here:
[http://debain.org/stuff/mcrec/mcclient/Makefile.am]("http://debain.org/stuff/mcrec/mcclient/Makefile.am")
[http://debain.org/stuff/mcrec/mcclient/src/Makefile.am]("http://debain.org/stuff/mcrec/mcclient/src/Makefile.am")


What I would like it to do:

Using "make" in the root directory should
a) build a library out of libmcc/ (test.c no longer needed) and
b) link the executable in src/ statically agains that library.


Why does it not work so far?:
a) I have no idea how to port libmcc/ from automake to autoconf, because the code generator for *.marshall.list needs to be triggered from that script.
b) I don't know how to compile libmcc/ as a library.
c) I don't know how to link against that library in src/Makefile.am.


Other information:

Browse the source online here:
[http://svn.gna.org/viewcvs/mcreceiver/trunk/mcclient/]("http://svn.gna.org/viewcvs/mcreceiver/trunk/mcclient/")

A tarball is here:
[http://debain.org/stuff/mcrec/mcclient.tgz]("http://debain.org/stuff/mcrec/mcclient.tgz")

Any help appreciated.

---

### Post by knipknap on 2005-12-05
I am trying to make the question a little more specific. I have created the following Makefile.am for libmcc/, which should (in theory) work if all files are there:
```
INCLUDES = $(MB_CFLAGS) \
        -DLOCALEDIR=\"$(localedir)\"

lib_LTLIBRARIES = libmcc.la
libmcc_la_LIBADD = $(MB_LIBS)

libmcc_la_CFLAGS=       $(INCLUDES) \
                -DPREFIX=\"$(prefix)\" -I$(top_srcdir)

libmcc_la_SOURCES = \
        TcpListenerMarshal.h \
        TcpListenerMarshal.c \
        TcpListener.h \
        TcpListener.c \
        McClientMarshal.h \
        McClientMarshal.c \
        McClient.h \
        McClient.c
```
However, because the snippet does not yet run glib-genmarshal to generate the *Marshal.h files that are listed in libmcc_la_SOURCES, it can never work. Any idea how to do that?

---

### Post by knipknap on 2005-12-05
Tim Janik was kind enough to help me on IRC. It works now, the resulting file libmcc/Makefile.am is here:
```
INCLUDES = $(GOBJECT_CFLAGS) \
        -DLOCALEDIR=\"$(localedir)\"

lib_LTLIBRARIES = libmcc.la
libmcc_la_LIBADD = $(GOBJECT_LIBS)

libmcc_la_CFLAGS=       $(INCLUDES) \
                -DPREFIX=\"$(prefix)\" -I$(top_srcdir)

libmcc_la_SOURCES = \
        TcpListenerMarshal.h \
        TcpListenerMarshal.c \
        TcpListener.h \
        TcpListener.c \
        McClientMarshal.h \
        McClientMarshal.c \
        McClient.h \
        McClient.c

EXTRA_DIST = \
        TcpListenerMarshal.list \
        McClientMarshal.list

BUILT_SOURCES = \
        TcpListenerMarshal.h \
        TcpListenerMarshal.c \
        McClientMarshal.h \
        McClientMarshal.c

nodist_libmcc_la_SOURCES = \
        $(BUILT_SOURCES)

TcpListenerMarshal.c: TcpListenerMarshal.h TcpListener.marshal.list
        echo "#include \"TcpListenerMarshal.h\"" > TcpListenerMarshal.c.tmp
        @GLIB_GENMARSHAL@ --body --prefix=tcp_listener $(srcdir)/TcpListener.marshal.list >> TcpListenerMarshal.c.tmp
        mv TcpListenerMarshal.c.tmp TcpListenerMarshal.c

TcpListenerMarshal.h: TcpListener.marshal.list
        @GLIB_GENMARSHAL@ --header --prefix=tcp_listener $(srcdir)/TcpListener.marshal.list >> TcpListenerMarshal.h.tmp
        mv TcpListenerMarshal.h.tmp TcpListenerMarshal.h

McClientMarshal.c: McClientMarshal.h McClient.marshal.list
        echo "#include \"McClientMarshal.h\"" > TcpListenerMarshal.c.tmp
        @GLIB_GENMARSHAL@ --body --prefix=mc_client $(srcdir)/McClient.marshal.list > McClientMarshal.c.tmp
        mv McClientMarshal.c.tmp McClientMarshal.c

McClientMarshal.h: McClient.marshal.list
        @GLIB_GENMARSHAL@ --header --prefix=mc_client $(srcdir)/McClient.marshal.list > McClientMarshal.h.tmp
        mv McClientMarshal.h.tmp McClientMarshal.h

CLEANFILES = $(BUILT_SOURCES) *Marshal.[ch].tmp
```

---

