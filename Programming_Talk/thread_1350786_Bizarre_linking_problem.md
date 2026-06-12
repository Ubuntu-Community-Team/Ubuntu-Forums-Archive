---
title: "Bizarre linking problem"
date: 2009-12-09
forum: Programming Talk
---

### Post by Vadi on 2009-12-09
> vadi@vadi-laptop:~/mudlet-1.0.4/bin$ ldd ./mudlet
	linux-gate.so.1 =>  (0x00e62000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x00128000)
	liblua5.1.so.0 => not found
	libQtGui.so.4 => not found
	libQtNetwork.so.4 => not found
	libQtCore.so.4 => not found
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x001b2000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00a77000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00c9b000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x007cf000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x001cb000)
	/lib/ld-linux.so.2 (0x00c74000)
vadi@vadi-laptop:~/mudlet-1.0.4/bin$ export LD_LIBRARY_PATH=$PWD:$LD_LIBRARY_PATH
vadi@vadi-laptop:~/mudlet-1.0.4/bin$ ldd ./mudlet
	linux-gate.so.1 =>  (0x0062f000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x00b17000)
	liblua5.1.so.0 => /home/vadi/mudlet-1.0.4/bin/liblua5.1.so.0 (0x0072f000)
	libQtGui.so.4 => /home/vadi/mudlet-1.0.4/bin/libQtGui.so.4 (0x00f93000)
	libQtCore.so.4 => /home/vadi/mudlet-1.0.4/bin/libQtCore.so.4 (0x001e5000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x006fe000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x0048d000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00c10000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00d08000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x0075b000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00ce7000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x00110000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x00116000)
	libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x0011f000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x0057f000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00c7e000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x001d5000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x005fe000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00edd000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00630000)
	libz.so.1 => /lib/libz.so.1 (0x00619000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x0065d000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x0089f000)
	/lib/ld-linux.so.2 (0x00f76000)
	libuuid.so.1 => /lib/libuuid.so.1 (0x00f02000)
	libexpat.so.1 => /lib/libexpat.so.1 (0x00a32000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x001de000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x0066d000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x0068b000)
vadi@vadi-laptop:~/mudlet-1.0.4/bin$ 

When I point LD_LIBRARY_PATH to look for libraries in the folder the binary is in, libQtNetwork suddenly becomes unlinked from it, and the app fails to start when it needs to fall functions from it.

Any idea why is libQtNetwork becoming disjointed?

---

### Post by dwhitney67 on 2009-12-10
On your system, where does libQtNetwork.so reside?

On my system, it is conveniently located in /usr/lib, which is one of the paths in the ldconfig cache.  Thus if I needed to link to this library, and run my application, I would not have to fiddle with LD_LIBRARY_PATH.

Is it possible that you do not have the (full) Qt-4 development package installed on your system?

---

### Post by Vadi on 2009-12-10
"On your system, where does libQtNetwork.so reside?"

In the same folder that the binary is in, which is why I had to update LD_LIBRARY_PATH to make it find it.

"Is it possible that you do not have the (full) Qt-4 development package installed on your system?"

Afraid no

---

### Post by Zugzwang on 2009-12-10
> **Vadi said:**
> "On your system, where does libQtNetwork.so reside?"

In the same folder that the binary is in, which is why I had to update LD_LIBRARY_PATH to make it find it.

"Is it possible that you do not have the (full) Qt-4 development package installed on your system?"

Afraid no

In this case, you do *not* have the QT4 package installed, as this file is part the libqt4-network" package:

[http://packages.ubuntu.com/search?searchon=contents&keywords=libQtNetwork.so.4&mode=exactfilename&suite=karmic&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libQtNetwork.so.4&mode=exactfilename&suite=karmic&arch=any)

So if you have it installed, you should have a copy in "/usr/lib" as well.
You might want to consider installing the "libqt4-dev" package to get the thing running as intended.

---

### Post by Vadi on 2009-12-10
No, that's the thing - I don't want to install any packages. I need to provide all the necessary libraries with the binary, and make it work. And they are indeed here:

> vadi@vadi-laptop:~/mudlet-1.0.4/bin$ ls -l
total 22928
lrwxrwxrwx 1 vadi vadi       46 2009-12-09 16:53 liblua5.1.so.0 -> /home/vadi/mudlet-1.0.4/bin/liblua5.1.so.0.0.0
-rw-r--r-- 1 vadi vadi   178240 2009-04-29 09:50 liblua5.1.so.0.0.0
lrwxrwxrwx 1 vadi vadi       46 2009-12-09 16:53 libQtCore.so.4 -> /home/vadi/mudlet-1.0.4/bin/libQtCore.so.4.6.0
-rwxr-xr-x 1 vadi vadi  3197172 2009-11-30 10:35 libQtCore.so.4.6.0
lrwxrwxrwx 1 vadi vadi       45 2009-12-09 16:53 libQtGui.so.4 -> /home/vadi/mudlet-1.0.4/bin/libQtGui.so.4.6.0
-rwxr-xr-x 1 vadi vadi 13166179 2009-11-30 10:35 libQtGui.so.4.6.0
lrwxrwxrwx 1 vadi vadi       45 2009-12-09 16:53 libQtNetwork.so.4 -> /home/vadi/mudlet-1.0.4/bin/libQtGui.so.4.6.0
-rwxr-xr-x 1 vadi vadi  1464734 2009-11-30 10:35 libQtNetwork.so.4.6.0
-rwxr-xr-x 1 vadi vadi  5457319 2009-12-09 14:27 mudlet
-rwxr-xr-x 1 vadi vadi      455 2009-12-09 16:56 run-mudlet.sh
vadi@vadi-laptop:~/mudlet-1.0.4/bin$ 


Just ... libQtNetwork dependency is being forgotten when I update the LD_LIBRARY_PATH.

---

### Post by dwhitney67 on 2009-12-10
The libraries you are pointing out are shared-object libraries; if you require to build the libraries into your application so that your application can be portable from one system to another, regardless if the foreign system has Qt installed, then you will need the static library.

As for building your application, I cannot help you directly because I have not used Qt in ages.  But the gist of it is to specify to the linker (in your case, probably g++) the location of the shared-object library and the library name itself.

For example:
```

g++ mySource.o -L/home/me/myQt/lib -lQtNetwork -o myApp

```
When you run the applicaton:
```

LD_LIBRARY_PATH=/home/me/myQt/lib ./myApp

```
Now, as I said earlier, this will *not* make your application portable to systems that do not have Qt.

P.S.  I worked on a project a couple of years ago in which my company (that is, mainly I) supported two versions of Qt.  I wrote something like:
```

#
#  This file contains information relevant to compiling and linking
#  with Qt.
#

QTVER := 3.2.3

ifeq (${NEWBLD}, true)
        QTDIR := ${LFS}/usr/local/qt-x11-free-$(QTVER)
        LD_LIBRARY_PATH := $(QTDIR)/lib:${LFS}/usr/lib:${LFS}/usr/X11R6/lib:$(LD_LIBRARY_PATH)
else
        QTDIR := ${PROJ_HOME}/dev/qt/qt-x11-free-$(QTVER)
        LD_LIBRARY_PATH := $(QTDIR)/lib:${PROJ_HOME}/dev/lib:$(LD_LIBRARY_PATH)
endif

QMAKESPEC   := $(QTDIR)/mkspecs/linux-g++
QMAKE       := $(QTDIR)/bin/qmake
QMAKE_DEBUG :=
QCXXFLAGS   := -pipe -w -O2 -DQT_NO_DEBUG -DQT_SHARED

ifeq ($(DEBUG), 1)
        QMAKE_DEBUG := "CONFIG+=debug"
        QCXXFLAGS   := -pipe -Wall -W -g -DQT_NO_DEBUG -DQT_SHARED
endif

export QTVER QTDIR QMAKESPEC QMAKE QMAKE_DEBUG QCXXFLAGS LD_LIBRARY_PATH


# Define compilation and link statements so that detailed output is suppressed.
#
CXX   = $(GCC)
QCXX  = @echo $(PRODUCT) ui Makefile - compiling: $$<;$(CXX)
QUIC  = @echo $(PRODUCT) ui Makefile - UICing: $$^;$(QTDIR)/bin/uic
QLINK = @echo $(PRODUCT) ui Makefile - linking: UI;$(CXX)


all: userInterfaces


userInterfaces: projects
        @for i in $(UI_DIRS) ; do \
            echo '#----------------------------------'; \
            echo '## Building user interface in' $$i; \
            echo '#----------------------------------'; \
            make -C $$i CXX="$(QCXX)" UIC="$(QUIC)" LINK="$(QLINK)" CXXFLAGS="$(QCXXFLAGS)"; \
            if [ $$? != 0 ]; then exit 1; fi; \
        done

projects:
        @for i in $(UI_DIRS) ; do \
            if [ -e $$i/*.pro ]; then \
               echo '#----------------------------------'; \
               echo '## Generating Makefile in' $$i; \
               echo '#----------------------------------'; \
               $(QMAKE) -o $$i/Makefile $$i/*.pro; \
            fi; \
        done

```
Anyhow, the crux of the matter is getting QMAKE to generate the appropriate Makefile for the environment that you wish to use; QMAKE relies on the contents of your project's .pro file to some extent.

---

### Post by Vadi on 2009-12-10
Can't really do a static build because I need the normal ones for PPAs and such.

Is there no way I can just tell it to "look for libs in this dir"?

---

### Post by dwhitney67 on 2009-12-11
> **Vadi said:**
> 
Is there no way I can just tell it to "look for libs in this dir"?
You can shout at the compiler; though I don't know if you will have much success with this approach.

An alternative is to read my previous post; I provided two different ways to build the project... the simple C++ way from the command line (which is adaptable to a Makefile), and more complicated approach which involves using QMake.

If you don't understand something I posted, just say so.  If you do not care to even try either of these approaches, then I guess you will have to go back to shouting at the compiler.

---

### Post by Vadi on 2009-12-11
No, the point is that I don't want to do static linking. Dynamic is working out just fine, and on Windows too, where I just ship my binary and place the libs it needs in the same folder.

Is Linux incapable of doing the same thing?

---

### Post by Zugzwang on 2009-12-11
> **Vadi said:**
> No, the point is that I don't want to do static linking. Dynamic is working out just fine, and on Windows too, where I just ship my binary and place the libs it needs in the same folder.


For avoiding confusion, you should probably also add that you do this in order to avoid having to release your application as LGPL/GPL which would be necessary if you did it by static linking (and distributed it).

Here's one thing you could try although I have no clue if it works. It's just a wild guess. Try placing the libraries in the current directory during linking and add "." as library path to the linker.

---

### Post by nvteighen on 2009-12-11
I still don't get what's the issue with downloading the libraries' package.

Do this:
1) Distribute your application as a .deb, using Qt4 as dependency (so, the packages will be immediately installed).
or:
2) Create .tar.gz that includes the .so and write an installer script (e.g. Makefile... but any scripting language will do) that, after checking the libraries aren't installed, installs them to /usr/local/lib and runs ldconfig to update the linker's cache.

---

### Post by Vadi on 2009-12-11
It's already GPL, not a problem.

@nvteighen: I don't want to install the libs system-wide, as that affects other programs. So I'm keeping them in my own folder. Problem is getting the program to use them.

---

### Post by nvteighen on 2009-12-12
> **Vadi said:**
> 
@nvteighen: I don't want to install the libs system-wide, as that affects other programs. So I'm keeping them in my own folder. Problem is getting the program to use them.

Why will they affect other programs? Installing Qt won't harm anything at all, unless you are sticking to an old version of KDE that uses Qt3... Moreover, if you've got any program that uses Qt, the APT system will have it already installed in your computer.

---

### Post by Vadi on 2009-12-12
I'm not using the apt system, I'm using the "tar.bz2" system, where I need to provide my own, non-patched Qt libs.

Ubuntu provides buggy ones, and Trolltech doesn't give a damn because Ubuntu isn't Opensuse. So I have to provide the binaries they do in order to have a problem-free experience. Hence, I need to make my binary be able to use them - even if other Qt libs exist on the system or not.

---

### Post by nvteighen on 2009-12-12
> **Vadi said:**
> I'm not using the apt system, I'm using the "tar.bz2" system, where I need to provide my own, non-patched Qt libs.

Ubuntu provides buggy ones, and Trolltech doesn't give a damn because Ubuntu isn't Opensuse. So I have to provide the binaries they do in order to have a problem-free experience. Hence, I need to make my binary be able to use them - even if other Qt libs exist on the system or not.

Ah, ok... Well, have you considered dynamic loading? (dlopen and friends)

---

### Post by dwhitney67 on 2009-12-12
> **Vadi said:**
> I'm not using the apt system, I'm using the "tar.bz2" system, where I need to provide my own, non-patched Qt libs.

Ubuntu provides buggy ones, and Trolltech doesn't give a damn because Ubuntu isn't Opensuse. So I have to provide the binaries they do in order to have a problem-free experience. Hence, I need to make my binary be able to use them - even if other Qt libs exist on the system or not.

Sigh... let's move forward on this.

1.  Post where I can get the compressed tar-ball (the .tar.bz2).

2.  Write and post here a small Qt app that displays "Hello World" in a button.

I will take care of the rest of getting this "baby" app to build with your "special" Qt library, and post back the "how to".  You should be able to then adapt my instructions to your larger project.

---

