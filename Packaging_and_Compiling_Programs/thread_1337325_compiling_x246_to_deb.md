---
title: "compiling x246 to deb"
date: 2009-11-25
forum: Packaging and Compiling Programs
---

### Post by ras123 on 2009-11-25
Hi,
How I can make lib files using debuild? I found many tutorial for making .debs but none to make libs.
Please help me to make x264 libs
Source is here

$git clone git://git.videolan.org/x264.git

---

### Post by SevenMachines on 2009-11-25
.debs are packages, whether your compiling a lib or an executable or installing any other scripts and files they are all contained in the deb. the actual  process involved in packaging a library is the same as packaging anything else

---

### Post by ras123 on 2009-11-25
Thanks, one more question, is it possible to build many type packages from a single source? I bit confused with a control file for x264 taken from a ppa,
```

Source: x264
Section: libs
Priority: optional
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
XSBC-Original-Maintainer: Christian Marillat <marillat@debian.org>
Bugs: mailto:marillat@debian.org
Homepage: http://www.videolan.org/developers/x264.html
Standards-Version: 3.7.3
Build-Depends: debhelper (>= 5), yasm [i386 amd64], libgtk2.0-dev, libgpac-dev,
 quilt

Package: x264
Section: graphics
Architecture: any
Depends: ${shlibs:Depends}
Conflicts: x264-bin
Replaces: x264-bin
Description: video encoder for the H.264/MPEG-4 AVC standard
 x264 is an advanced commandline encoder for creating H.264 (MPEG-4 AVC)
 video streams.
 .
 x264 supports the following features:
  * CABAC (context-based adaptive binary arithmetic coding) and CAVLC
    (context-based adaptive variable length coding
  * multiple reference frames
  * 16x16, 8x8 and 4x4 intra-predicted macroblocks
  * all P-frame inter-predicted macroblock types
  * B-Inter-predicted macroblock types from 16x16 down to 8x8
  * rate distortion optimization
  * multiple rate control modes (constant quantizer, constant quality, single
    or multipass ABR with the option of VBV)
  * scene cut detection
  * adaptive B-frame placement, with the option of keeping B-frames as
    references / arbitrary frame order
  * 8x8 and 4x4 adaptive spatial transform (high profile)
  * lossless mode (high 4:4:4 profile)
  * custom quantization matrices (high profile)
  * parallel encoding on multiple CPUs
  * interlaced streams

Package: libx264-59
Section: libs
Architecture: any
Depends: ${shlibs:Depends}
Description: x264 video coding library
 libx264 is an advanced encoding library for creating H.264 (MPEG-4 AVC)
 video streams.
 .
 This package contains the libx264 shared library.

Package: libx264-dev
Section: libdevel
Architecture: any
Depends: libx264-59 (= ${binary:Version})
Description: development files for libx264
 libx264 is an advanced encoding library for creating H.264 (MPEG-4 AVC)
 video streams.
 .
 This package contains the static library and headers used to build programs
 that use libx264.

```

Is the above make all (x264, libx264-59, libx264-dev), and kindly explain the differences of x264 and libx264?

---

### Post by SevenMachines on 2009-11-25
In a control file with entries like the one you mention you'll generally find that
mypackage - contains binaries and so on for running the programs
libmypackage - the libraries used by the binaries
libmypackage-dev - the headers and anything else needed to compile against the libraries

obviously thats just a rough generalisation but reasonable guide for a lot of packages

{EDIT} yes, you can have multiple entries like that in debian/control resulting in the creation of multiple packages from the same source code

---

### Post by ras123 on 2009-11-25
> **SevenMachines said:**
> 
mypackage - contains binaries and so on for running the programs
libmypackage - the libraries used by the binaries

I couldn't get the idea how same file can be used as library (I think this is used by some other programs) and an executable!

---

