---
title: "Beginner's questions: packaging Gimp with addons"
date: 2010-04-19
forum: Packaging and Compiling Programs
---

### Post by eyedeal on 2010-04-19
Hi,

I've used Arch Linux for a long while, and there we started a project called Painters Studio. It's basically Gimp with some custom patches, and lots of addons.

Since I started using Ubuntu, I was meaning to package that for Karmic as well.

I've got some questions, though. (Bear with me, I have no C development experience, so makefiles and everything else is a bit new to me.)

I took the sources for the stock Gimp 2.6.7 (atp-get source gimp) and successfully(?) modified it to suit the needs of the Painters Studio. Here's how the control file looks like now:

```
Source: painters-studio
Priority: optional
Section: graphics
Maintainer: Branko Vukelic <bg.branko@gmail.com>
Standards-Version: 3.8.2
Build-Depends: debhelper (>= 5.0.53), cdbs (>= 0.4.37), autotools-dev,
 patchutils, gettext, intltool (>= 0.36.3), libx11-dev, libice-dev, libsm-dev,
 libxmu-dev, libxpm-dev, libxt-dev,
 libaa1-dev, libgtk2.0-dev (>= 2.10.13), libglib2.0-dev (>= 2.16.0),
 libpango1.0-dev (>= 1.12.2), libjpeg62-dev,
 libart-2.0-dev, libpng12-dev | libpng-dev,
 zlib1g-dev, libtiff4-dev, python-dev (>= 2.3.5), python-gtk2-dev (>= 2.10.4),
 python-support (>= 0.4), libexif-dev (>= 0.6.15), libmng-dev,
 librsvg2-dev (>= 2.7.2-2), libfontconfig1-dev (>= 2.2.0),
 libwmf-dev (>= 0.2.8-1.1), libfreetype6-dev (>= 2.2),
 libpoppler-glib-dev (>= 0.3.1),
 libasound2-dev (>= 1.0.0) [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386],
 libhal-dev (>= 0.5.7), libdbus-glib-1-dev (>= 0.70),
 liblcms1-dev | liblcms-dev, libgegl-0.0-dev, libbabl-0.0-0-dev
Build-Conflicts: libgimp2.0
Homepage: http://codaset.com/foxbunny/gimp-studio

Package: libgimp2.0
Architecture: any
Section: libs
Depends: ${shlibs:Depends}
Recommends: painters-studio, painters-studio-data (>= ${source:Upstream-Version}), painters-studio-data (<= ${source:Upstream-Version}-z)
Description: Libraries for Painters Studio
 This package includes the libgimp libraries, which are
 necessary to run Painters Studio and third-party Gimp plugins.

Package: painters-studio
Architecture: any
Section: graphics
Provides: gimp-helpbrowser, gimp-python
Depends: libgimp2.0 (>= ${source:Upstream-Version}), libgimp2.0 (<= ${source:Upstream-Version}-z), painters-studio-data (>= ${source:Upstream-Version}), painters-studio-data (<= ${source:Upstream-Version}-z), python-gtk2 (>= 2.8.0), ${shlibs:Depends}, ${python:Depends}
Conflicts: gimp (<= 2.6.8), gimp-data (<< 2.3.17-2), gimp-wget (<< 2.3.12-1), libgimp-perl (<= 2.0.dfsg+2.2pre1.dfsg-2), gimp-svg, gimp-print (<= 5.0.1-3), gimp-help (<< 2+0.13-1), gimp-helpbrowser, gimp-python (<< 2.6.0), gimp-gnomevfs (<< 2.6.0), gimp-libcurl (<< 2.6.0)
Replaces: gimp (<= 2.6.8), gimp-data (<< 2.3.17-2), gimp-wget (<< 2.3.12-1), libgimp-perl (<= 2.0.dfsg+2.2pre1.dfsg-2), gimp-svg, gimp-print (<= 5.0.1-3), gimp-helpbrowser, gimp-python (<< 2.6.0), gimp-gnomevfs (<< 2.6.0), gimp-libcurl (<< 2.6.0)
Suggests: gimp-help-en | gimp-help, libgimp-perl, painters-studio-data-extras, gvfs-backends, libasound2, ghostscript
Description: Painters Studio
 Gimp lets you draw, paint, edit images, and much more! Gimp
 includes the functionality and plug-ins of other famous image
 editing and processing programs. Painters Studio is a modified version
 of Gimp with improved stability, feature-packed to fulfill the needs of
 professional digital artists, photographers, and designers alike.
 .
 If you'd like to be able to open files remotely (like over HTTP or FTP),
 install the gvfs-backends package.
 .
 If you'd like to use a MIDI device as an input controller in Painters Studio,
 install libasound2 and read the how-to at /usr/share/doc/gimp/README.MIDI
 .
 If you'd like to be able to read and write PostScript files from Painters 
 Studio, install the ghostscript package.

Package: painters-studio-data
Architecture: all
Section: graphics
Recommends: painters-studio
Conflicts: gimp (<= 2.6.8), gimp-python (<< 2.6.0)
Replaces: gimp (<= 2.6.8), gimp-python (<< 2.6.0)
Description: Data files for Painters Studio
 This package contains architecture-independent supporting data files
 for use with Painters Studio.

Package: libgimp2.0-dev
Architecture: any
Section: libdevel
Depends: libgimp2.0 (= ${binary:Version}), libgtk2.0-dev (>= 2.10.0), pkg-config
Suggests: libgimp2.0-doc
Description: Headers and other files for compiling plugins for Painters Studio
 This package contains the header files for Painters Studio
 Program, along with the static versions of libgimp.
 It also includes the gimptool-2.0 utility.
 .
 Install this package if you wish to compile your own plugins,
 or if you wish to develop packages that use libgimp. 

Package: libgimp2.0-doc
Architecture: all
Section: doc
Depends: lynx | www-browser
Description: Developers' Documentation for the Gimp library
 This package contains the HTML documentation for the Gimp library in
 /usr/share/gtk-doc/html/ .

Package: painters-studio-dbg
Priority: extra
Architecture: any
Section: debug
Depends: gimp (= ${binary:Version}) | libgimp2.0 (= ${source:Version}), ${shlibs:Depends}
Description: Debugging symbols for Painters Studio
 This package includes the debugging symbols useful for debugging
 Gimp and its libraries, contained in the gimp and libgimp2.0 packages.
 The debugging symbols are used for execution tracing and core dump
 analysis.
```

What I'd like to do now is:

1. Make sure Painters Studio replaces Gimp (which it doesn't)
2. I'd also like to add another package (painters-studio-data-extra) which contains a bunch of brushes, tool presets, etc. This I have no idea how to do.
3. Add a notification like I've seen in packages like postfix (debconf?), where some post-install configuration can be done: namely, copy tool-presets into .gimp-2.6 directory of the selected user accounts (unfortunately tool-presets can only be installed in user directories, but they are essential for Painters Studio)

Can someone please guide me through this or point me to resources? I've read the complete and hands-on guides, but complete guide is just too overwhelming, while hands-on doesn't really cover these specific cases.

---

