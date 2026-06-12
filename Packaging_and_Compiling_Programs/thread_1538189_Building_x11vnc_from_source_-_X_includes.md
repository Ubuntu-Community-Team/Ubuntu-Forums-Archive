---
title: "Building x11vnc from source - X includes"
date: 2010-07-24
forum: Packaging and Compiling Programs
---

### Post by acmeinc on 2010-07-24
The deb packages seem broke for the latest version of x11vnc (0.9.10) which fixes a bug in a flag which I use.  Also this hasn't been pushed to the apt-get system yet.  So  I'm building from scratch. 

Here's the error:
```

==========================================================================
*** A working X window system build environment is required to build ***
x11vnc.  Make sure any required X development packages are installed.
If they are installed in non-standard locations, one can use the
--x-includes=DIR and --x-libraries=DIR configure options or set the
CPPFLAGS and LDFLAGS environment variables to indicate where the X
window system header files and libraries may be found.  On 64+32 bit
machines you may need to point to lib64 or lib32 directories to pick up
the correct word size.

If you want to build x11vnc without X support (e.g. for -rawfb use only
or for native Mac OS X), specify the --without-x configure option.
==========================================================================
```

Where do the includes exist, or what packages need installed?

Thanks.

---

### Post by Bachstelze on 2010-07-24
Install [font=monospace]xorg-dev[/font].

---

### Post by acmeinc on 2010-07-24
Thanks, that worked.

---

