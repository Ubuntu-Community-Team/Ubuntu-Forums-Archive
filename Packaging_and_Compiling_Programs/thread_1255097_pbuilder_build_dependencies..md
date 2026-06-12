---
title: "pbuilder build dependencies."
date: 2009-09-01
forum: Packaging and Compiling Programs
---

### Post by _sluimers_ on 2009-09-01
I'm trying to get to build a dsc file of mine, but it fails.
pbuilder is not recognizing some of the build dependencies and I wonder what I should do, so pbuilder will.



[EDIT] 
I also have a problem packaging it for ppa. It builds fine, except the executable doesn't get installed.

I heard from another board that both problems might be related to either my control file or my rules file. So I post them below as well.


[/EDIT]

```

#
rogier@rogier-desktop ~/Desktop/PPA/ika $ sudo pbuilder build ika_0.62~46.dsc
#
[sudo] password for rogier:
#
I: using fakeroot in build.
#
Current time: Tue Sep  1 07:06:58 CEST 2009
#
pbuilder-time-stamp: 1251781618
#
Building the build Environment
#
 -> extracting base tarball [/var/cache/pbuilder/base.tgz]
#
 -> creating local configuration
#
 -> copying local configuration
#
 -> mounting /proc filesystem
#
 -> mounting /dev/pts filesystem
#
 -> policy-rc.d already exists
#
Obtaining the cached apt archive contents
#
Installing the build-deps
#
 -> Attempting to satisfy build-dependencies
#
 -> Creating pbuilder-satisfydepends-dummy package
#
Package: pbuilder-satisfydepends-dummy
#
Version: 0.invalid.0
#
Architecture: i386
#
Maintainer: Debian Pbuilder Team <pbuilder-maint@lists.alioth.debian.org>
#
Description: Dummy package to satisfy dependencies with aptitude - created by pbuilder
#
 This package was created automatically by pbuilder and should
#
Depends: debhelper (>= 7), corona, libaudiere-dev, libaudiere-1.9.4, libwxgtk2.8-0, libwxgtk2.8-dev, libsdl1.2-dev, libwxgtk2.6-0, libwxgtk2.6-dev, zlib1g-dev, python-wxgtk2.6, python-wxgtk2.8, python2.6-dev
#
dpkg-deb: building package `pbuilder-satisfydepends-dummy' in `/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
#
Reading package lists... Done
#
Building dependency tree      
#
Reading state information... Done
#
aptitude is already the newest version.
#
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
#
Selecting previously deselected package pbuilder-satisfydepends-dummy.
#
(Reading database ... 10502 files and directories currently installed.)
#
Unpacking pbuilder-satisfydepends-dummy (from .../pbuilder-satisfydepends-dummy.deb) ...
#
dpkg: dependency problems prevent configuration of pbuilder-satisfydepends-dummy:
#
 pbuilder-satisfydepends-dummy depends on debhelper (>= 7); however:
#
  Package debhelper is not installed.
#
 pbuilder-satisfydepends-dummy depends on corona; however:
#
  Package corona is not installed.
#
 pbuilder-satisfydepends-dummy depends on libaudiere-dev; however:
#
  Package libaudiere-dev is not installed.
#
 pbuilder-satisfydepends-dummy depends on libaudiere-1.9.4; however:
#
  Package libaudiere-1.9.4 is not installed.
#
 pbuilder-satisfydepends-dummy depends on libwxgtk2.8-0; however:
#
  Package libwxgtk2.8-0 is not installed.
#
 pbuilder-satisfydepends-dummy depends on libwxgtk2.8-dev; however:
#
  Package libwxgtk2.8-dev is not installed.
#
 pbuilder-satisfydepends-dummy depends on libsdl1.2-dev; however:
#
  Package libsdl1.2-dev is not installed.
#
 pbuilder-satisfydepends-dummy depends on libwxgtk2.6-0; however:
#
  Package libwxgtk2.6-0 is not installed.
#
 pbuilder-satisfydepends-dummy depends on libwxgtk2.6-dev; however:
#
  Package libwxgtk2.6-dev is not installed.
#
 pbuilder-satisfydepends-dummy depends on zlib1g-dev; however:
#
  Package zlib1g-dev is not installed.
#
 pbuilder-satisfydepends-dummy depends on python-wxgtk2.6; however:
#
  Package python-wxgtk2.6 is not installed.
#
 pbuilder-satisfydepends-dummy depends on python-wxgtk2.8; however:
#
  Package python-wxgtk2.8 is not installed.
#
 pbuilder-satisfydepends-dummy depends on python2.6-dev; however:
#
  Package python2.6-dev is not installed.
#
dpkg: error processing pbuilder-satisfydepends-dummy (--install):
#
 dependency problems - leaving unconfigured
#
Errors were encountered while processing:
#
 pbuilder-satisfydepends-dummy
#
Reading package lists... Done
#
Building dependency tree      
#
Reading state information... Done
#
Initializing package states... Done
#
Writing extended state information... Done
#
The following packages are BROKEN:
#
  pbuilder-satisfydepends-dummy
#
The following NEW packages will be installed:
#
  bsdmainutils{a} debhelper{a} file{a} gettext{a} gettext-base{a}
#
  groff-base{a} html2text{a} intltool-debian{a} libasound2{a} libcroco3{a}
#
  libdirectfb-1.0-0{a} libdrm2{a} libgl1-mesa-dev{a} libgl1-mesa-glx{a}
#
  libglib2.0-0{a} libglu1-mesa{a} libglu1-mesa-dev{a} libmagic1{a}
#
  libpthread-stubs0{a} libpthread-stubs0-dev{a} libpython2.6{a}
#
  libsdl1.2-dev{a} libsdl1.2debian{a} libsdl1.2debian-alsa{a}
#
  libsqlite3-0{a} libsysfs2{a} libts-0.0-0{a} libx11-6{a} libx11-data{a}
#
  libx11-dev{a} libxau-dev{a} libxau6{a} libxcb1{a} libxcb1-dev{a}
#
  libxdamage1{a} libxdmcp-dev{a} libxdmcp6{a} libxext6{a} libxfixes3{a}
#
  libxml2{a} libxxf86vm1{a} man-db{a} mesa-common-dev{a} mime-support{a}
#
  po-debconf{a} python2.6{a} python2.6-dev{a} x11-common{a}
#
  x11proto-core-dev{a} x11proto-input-dev{a} x11proto-kb-dev{a}
#
  xtrans-dev{a} zlib1g-dev{a}
#
The following packages are RECOMMENDED but will NOT be installed:
#
  curl libaa1-dev libasound2-dev libaudio-dev libcaca-dev
#
  libcompress-zlib-perl libdirectfb-dev libesd0-dev libglib2.0-data
#
  libmail-sendmail-perl libxext-dev libxt-dev lynx shared-mime-info wget
#
  xml-core
#
0 packages upgraded, 53 newly installed, 0 to remove and 0 not upgraded.
#
Need to get 18.4MB/21.8MB of archives. After unpacking 69.6MB will be used.
#
The following packages have unmet dependencies:
#
  pbuilder-satisfydepends-dummy: Depends: corona which is a virtual package.
#
                                 Depends: libaudiere-dev which is a virtual package.
#
                                 Depends: libaudiere-1.9.4 which is a virtual package.
#
                                 Depends: libwxgtk2.8-0 which is a virtual package.
#
                                 Depends: libwxgtk2.8-dev which is a virtual package.
#
                                 Depends: libwxgtk2.6-0 which is a virtual package.
#
                                 Depends: libwxgtk2.6-dev which is a virtual package.
#
                                 Depends: python-wxgtk2.6 which is a virtual package.
#
                                 Depends: python-wxgtk2.8 which is a virtual package.
#
The following actions will resolve these dependencies:
#
 
#
Remove the following packages:
#
pbuilder-satisfydepends-dummy
#
 
#
Score is -9850
#
 
#
Writing extended state information... Done
#
debconf: delaying package configuration, since apt-utils is not installed
#
(Reading database ... 10502 files and directories currently installed.)
#
Removing pbuilder-satisfydepends-dummy ...
#
Selecting previously deselected package libmagic1.
#
(Reading database ... 10502 files and directories currently installed.)
#
Unpacking libmagic1 (from .../libmagic1_4.26-2ubuntu3_i386.deb) ...
#
Selecting previously deselected package file.
#
Unpacking file (from .../file_4.26-2ubuntu3_i386.deb) ...
#
Selecting previously deselected package libsqlite3-0.
#
Unpacking libsqlite3-0 (from .../libsqlite3-0_3.6.10-1_i386.deb) ...
#
Selecting previously deselected package mime-support.
#
Unpacking mime-support (from .../mime-support_3.44-1_all.deb) ...
#
Selecting previously deselected package python2.6.
#
Unpacking python2.6 (from .../python2.6_2.6.2-0ubuntu1_i386.deb) ...
#
Selecting previously deselected package bsdmainutils.
#
Unpacking bsdmainutils (from .../bsdmainutils_6.1.10ubuntu3_i386.deb) ...
#
Setting up libmagic1 (4.26-2ubuntu3) ...
#
 
#
Setting up file (4.26-2ubuntu3) ...
#
Setting up libsqlite3-0 (3.6.10-1) ...
#
 
#
Setting up mime-support (3.44-1) ...
#
 
#
Setting up python2.6 (2.6.2-0ubuntu1) ...
#
 
#
Setting up bsdmainutils (6.1.10ubuntu3) ...
#
 
#
Processing triggers for libc6 ...
#
ldconfig deferred processing now taking place
#
Reading package lists... Done            
#
Building dependency tree      
#
Reading state information... Done
#
Reading extended state information      
#
Initializing package states... Done
#
Writing extended state information... Done
#
 
#
Current status: 0 broken [-1].
#
Aptitude couldn't satisfy the build dependencies
#
E: pbuilder-satisfydepends failed.
#
Copying back the cached apt archive contents
#
-> unmounting dev/pts filesystem
#
-> unmounting proc filesystem
#
-> cleaning the build env
#
   -> removing directory /var/cache/pbuilder/build//6993 and its subdirectories

```

control file:
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
Description: ika is a Python based Multi-Platform (RPG) GameMaker. 
 This is the core engine of ika.
 Visit ika's homepage at http://ika.sf.net
```

rules file:
```
#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.
 
# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1
 
 
 
 
 
configure: configure-stamp
configure-stamp:
        dh_testdir
        # Add here commands to configure the package.
 
        touch configure-stamp
 
 
build: build-stamp
 
build-stamp: configure-stamp  
        dh_testdir
 
        # Add here commands to compile the package.
        $(MAKE)
        #docbook-to-man debian/ika.sgml > ika.1
 
        touch $@
 
clean: 
        dh_testdir
        dh_testroot
        rm -f build-stamp configure-stamp
 
        # Add here commands to clean up after the build process.
        $(MAKE) clean
 
        dh_clean 
 
install: build
        dh_testdir
        dh_testroot
        dh_prep  
        dh_installdirs
 
        # Add here commands to install the package into debian/ika.
        $(MAKE) DESTDIR=$(CURDIR)/debian/ika install
 
 
# Build architecture-independent files here.
binary-indep: install
# We have nothing to do by default.
 
# Build architecture-dependent files here.
binary-arch: install
        dh_testdir
        dh_testroot
        dh_installchangelogs 
        dh_installdocs
        dh_installexamples
        dh_install
#       dh_installmenu
#       dh_installdebconf
#       dh_installlogrotate
#       dh_installemacsen
#       dh_installpam
#       dh_installmime
#       dh_python
#       dh_installinit
#       dh_installcron
#       dh_installinfo
        dh_installman
        dh_link
        dh_strip
        dh_compress
        dh_fixperms
#       dh_perl
#       dh_makeshlibs
        dh_installdeb
        dh_shlibdeps
        dh_gencontrol
        dh_md5sums
        dh_builddeb
 
binary: binary-indep binary-arch
.PHONY: build clean binary-indep binary-arch binary install configure
```

and why not makefile:
```

CXX = g++

CXXFLAGS = -O2 -Wall -I. -Icommon -Iengine -I/usr/include/python2.6 -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D__WXGTK__ -D_LARGE_FILES -Wno-unknown-pragmas -Wno-c++0x-compat -Wno-unused-variable -fno-strict-aliasing -DNDEBUG -g -fwrapv -pthread -Bsymbolic-functions -lwx_gtk2u_richtext-2.8 -lwx_gtk2u_aui-2.8 -lwx_gtk2u_xrc-2.8 -lwx_gtk2u_qa-2.8 -lwx_gtk2u_html-2.8 -lwx_gtk2u_adv-2.8 -lwx_gtk2u_core-2.8 -lwx_baseu_xml-2.8 -lwx_baseu_net-2.8 -lwx_baseu-2.8 -ldl -lutil -lm -lpython2.6 -lSDL -lGL -lGLU -lcorona -lutil -laudiere

# LDFLAGS = -Wl <- What is -Wl anyway?

MDIR = engine
CDIR = common

SOURCESC = aries.cpp base64.cpp Canvas.cpp chr.cpp compression.cpp configfile.cpp fileio.cpp fontfile.cpp log.cpp map.cpp mem.cpp oldbase64.cpp rle.cpp utility.cpp vergemap.cpp vergepal.cpp version.cpp vsp.cpp
_OBJECTSC = $(SOURCESC:.cpp=.o)
OBJECTSC = $(patsubst %,$(CDIR)/%,$(_OBJECTSC))

SOURCESM = animscript.cpp benchmark.cpp entity.cpp font.cpp FPSCounter.cpp input.cpp joystick.cpp keyboard.cpp main.cpp mouse.cpp script.cpp scriptobject.cpp sound.cpp sprite.cpp tileset.cpp script/CanvasObject.cpp script/ColoursObject.cpp script/ControlObject.cpp script/EntityObject.cpp script/ErrorObject.cpp script/FontObject.cpp script/ImageObject.cpp script/InputDeviceObject.cpp script/InputObject.cpp script/JoystickObject.cpp script/KeyboardObject.cpp script/MapObject.cpp script/ModuleFuncs.cpp script/MouseObject.cpp script/MusicObject.cpp script/SoundObject.cpp script/TileSetObject.cpp script/VideoObject.cpp opengl/Driver.cpp opengl/Image.cpp soft32/Driver.cpp soft32/Image.cpp video/ColourHandler.cpp

_OBJECTSM = $(SOURCESM:.cpp=.o)
OBJECTSM = $(patsubst %,$(MDIR)/%,$(_OBJECTSM))

OBJECTS = $(OBJECTSC) $(OBJECTSM) 

PREFIX=debian/tmp/usr
BINDIR=$(PREFIX)/games

.PHONY : clean install ika

ika: $(OBJECTS)
	$(CXX) $(CXXFLAGS) -o $(MDIR)/ika $(OBJECTS)

$(CDIR)/%.o: %.cpp 
	$(CXX) $(CXXFLAGS) $< -o $@
$(MDIR)/%.o: %.cpp 
	$(CXX) $(CXXFLAGS) $< -o $@

install: $(MDIR)/ika
	mkdir -p $(BINDIR)
	install $(MDIR)/ika $(BINDIR)/ika

clean:
	rm -f ika $(OBJECTS) 


```

---

### Post by _sluimers_ on 2009-09-02
I solved the pbuilder problem by putting the base.tgz file in the same folder as the dsc file, but the package still doesn't have the executable just like in ppa.

---

