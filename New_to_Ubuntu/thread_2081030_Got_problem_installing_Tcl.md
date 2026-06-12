---
title: "Got problem installing Tcl"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by Quickiez on 2012-11-05
Hi guys i have a problem... im going to install an eggdrop but when i configure it it says 


hecking for working mmap... yes
checking for Tcl library... not found
checking for Tcl header... not found
checking whether the Tcl system has changed... yes
configure: error:

  Tcl cannot be found on this system.

  Eggdrop requires Tcl and the Tcl development files to compile.
  If you already have Tcl installed on this system, make sure you
  also have the development files (common package names include
  'tcl-dev' and 'tcl-devel'). If I just wasn't looking
  in the right place for it, re-run ./configure using the
  --with-tcllib='/path/to/libtcl.so' and
  --with-tclinc='/path/to/tcl.h' options.

  See doc/COMPILE-GUIDE's 'Tcl Detection and Installation' section for more
  information.

ive written sudo apt-get install tk8.5 tcl8.5
but still have the same problem why?

Thanks in advance

---

### Post by squakie on 2012-11-05
You also need the tcl development libraries:

tcl8.4-dev

and/or

tcl8.5-dev


You can use the package manager to install them or the command line if you prefer.

---

