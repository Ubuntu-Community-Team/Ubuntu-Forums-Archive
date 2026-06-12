---
title: "Can someone help me compile this from source please?"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by hopelessone on 2012-06-02
Hi,

Ubuntu 12.04 64bit, XBMC, VDR installed from repositories.

I want to compile the plugin:
vdr-plugin-xvdr
As XBMC need it..I got as far as:
```
blade@pangolin:~/src/vdr-plugin-xvdr$ make
g++ -O2 -g -Wall -Woverloaded-virtual -fPIC -DPIC -c -DPLUGIN_NAME_I18N='"xvdr"' -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -DXVDR_VERSION='"0.9.5"' -I../../../include -I../../../../DVB/include -I../../.. -I./src -I. -o src/config/config.o src/config/config.c
src/config/config.c:30:24: fatal error: vdr/plugin.h: No such file or directory
compilation terminated.
make: *** [src/config/config.o] Error 1
```

No idea what to do next?

---

### Post by d.atanasov on 2012-06-02
do you have some file with README or INSTALL in the folder ? Perhaps just look inside and see what file is missing ? If not please consider that some times firs the software need to be configured (just type configure into the folder then make or make-install).

---

### Post by hopelessone on 2012-06-02
Unfortunately theres no readme file, but heres the make file:
```
#
# Makefile for a Video Disk Recorder plugin
#
# $Id$

# The official name of this plugin.
# This name will be used in the '-P...' option of VDR to load the plugin.
# By default the main source file also carries this name.
#
PLUGIN = xvdr

### The version number of this plugin (taken from the main source file):

VERSION = $(shell grep 'static const char \*VERSION *=' src/xvdr/xvdr.h | awk '{ print $$6 }' | sed -e 's/[";]//g')

### The C++ compiler and options:

OPTLEVEL ?= 2
CXXFLAGS = -O$(OPTLEVEL) -g -Wall -Woverloaded-virtual -fPIC -DPIC

### The directory environment:

DVBDIR = ../../../../DVB
VDRDIR = ../../..
LIBDIR = ../../lib
TMPDIR = /tmp

### Allow user defined options to overwrite defaults:

-include $(VDRDIR)/Make.config
-include $(VDRDIR)/Make.global

### The version number of VDR (taken from VDR's "config.h"):

APIVERSION = $(shell grep 'define APIVERSION ' $(VDRDIR)/config.h | awk '{ print $$3 }' | sed -e 's/"//g')

### The name of the distribution archive:

ARCHIVE = vdr-plugin-$(PLUGIN)-$(VERSION)
PACKAGE = $(ARCHIVE)

### Includes and Defines (add further entries here):

INCLUDES += -I$(VDRDIR)/include -I$(DVBDIR)/include -I$(VDRDIR) -I./src -I.

DEFINES += -DPLUGIN_NAME_I18N='"$(PLUGIN)"' -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -DXVDR_VERSION='"$(VERSION)"'
ifeq ($(DEBUG),1)
  DEFINES += -DDEBUG=1
endif
ifeq ($(CONSOLEDEBUG),1)
  DEFINES += -DCONSOLEDEBUG=1
endif

### The object files (add further files here):

OBJS = \
	src/config/config.o \
	src/demuxer/bitstream.o \
	src/demuxer/demuxer.o \
	src/demuxer/demuxer_LATM.o \
	src/demuxer/demuxer_AC3.o \
	src/demuxer/demuxer_DTS.o \
	src/demuxer/demuxer_h264.o \
	src/demuxer/demuxer_MPEGAudio.o \
	src/demuxer/demuxer_MPEGVideo.o \
	src/demuxer/demuxer_Subtitle.o \
	src/demuxer/demuxer_Teletext.o \
	src/live/channelcache.o \
	src/live/livepatfilter.o \
	src/live/livequeue.o \
	src/live/livereceiver.o \
	src/live/livestreamer.o \
	src/net/cxsocket.o \
	src/net/requestpacket.o \
	src/net/responsepacket.o \
	src/recordings/recordingscache.o \
	src/recordings/recplayer.o \
	src/tools/hash.o \
	src/xvdr/xvdr.o \
	src/xvdr/xvdrclient.o \
	src/xvdr/xvdrserver.o

### Implicit rules:

all-redirect: all

%.o: %.c
	$(CXX) $(CXXFLAGS) -c $(DEFINES) $(INCLUDES) -o $@ $<

# Dependencies:

MAKEDEP = g++ -MM -MG
DEPFILE = .dependencies
$(DEPFILE): Makefile
	@$(MAKEDEP) $(DEFINES) $(INCLUDES) $(OBJS:%.o=%.c) > $@

-include $(DEPFILE)

### Targets:

all: libvdr-$(PLUGIN).so

libvdr-$(PLUGIN).so: $(OBJS)
	$(CXX) $(CXXFLAGS) -shared $(OBJS) -o $@ -lz
	@cp $@ $(LIBDIR)/$@.$(APIVERSION)

dist: clean
	@-rm -rf $(TMPDIR)/$(ARCHIVE)
	@mkdir $(TMPDIR)/$(ARCHIVE)
	@cp -a * $(TMPDIR)/$(ARCHIVE)
	@-rm -f $(TMPDIR)/$(ARCHIVE)/*.so.*
	@-rm -f $(TMPDIR)/$(ARCHIVE)/*.so
	@-rm -rf $(TMPDIR)/$(ARCHIVE)/debian/vdr-plugin-$(PLUGIN)
	@-rm -rf $(TMPDIR)/$(ARCHIVE)/debian/*.log
	@-rm -rf $(TMPDIR)/$(ARCHIVE)/debian/*.substvars
	@-rm -rf $(TMPDIR)/$(ARCHIVE)/debian/.gitignore
	@-rm -rf $(TMPDIR)/$(ARCHIVE)/.git*
	@tar czf $(PACKAGE).tar.gz -C $(TMPDIR) $(ARCHIVE)
	@-rm -rf $(TMPDIR)/$(ARCHIVE)/
	@echo Distribution package created as $(PACKAGE).tar.gz

clean:
	@-rm -f $(OBJS) $(DEPFILE) *.so *.tgz core* *~

install:
	@install -d ../../man
	@install README ../../man/$(PLUGIN).man
```

---

### Post by d.atanasov on 2012-06-02
From the first post of yours the error suggest that the header file with all functions is missing. I don`t have much experience with XBMC but you could try to locate where is this file "plugin.h" and put it at the right path. This is only suggestion perhaps if someone else has a better solution would be nicer? i will try to find something in google about this...


[http://code.google.com/p/xbmc-iplayer/wiki/HowToInstall](http://code.google.com/p/xbmc-iplayer/wiki/HowToInstall) Can you locate your profile folder for XBMC? perhaps you don`t need to do make install of the plugins just place the plugins in this folder and after that find them in XBMC.

---

### Post by steeldriver on 2012-06-02
Are you sure you have all the prerequisite dev packages installed? I took a quick look in synaptic and found:

```
vdr-dev
This package contains the header files of VDR.
You need this package to be able to build vdr-plugins!
```Based on these lines in the make file (which are the basis for the -I  includes) it looks like you need to be building this in a very specific  development environment, presumably VDRDIR is what you get from installing the vbr-dev package - it may also need some overall dvb dev package to set up the root DVBDIR

```

DVBDIR = ../../../../DVB 
VDRDIR = ../../.. 
LIBDIR = ../../lib

```Hope this helps

---

### Post by hopelessone on 2012-06-02
Hi !

vdr-dev, no I didnt have that installed...

Thanks!

---

### Post by mc4man on 2012-06-02
In 12.04 or earlier you could if desired just build as a package, as in  - 
at the vdr-plugin-xvdr-0.9.5$ prompt
```
fakeroot debian/rules binary
```

(assumes you have fakeroot installed & what's shown in the /debian/control file
> Build-Depends: debhelper (>= 5), cdbs, dpatch, vdr-dev (>= 1.6.0), zlib1g-dev

---

