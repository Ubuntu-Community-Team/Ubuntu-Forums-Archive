---
title: "Can't ./configure eggdrop1.6.19"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by _Silver on 2008-05-24
~/eggdrop1.6.19$ ./configure

This is Eggdrop's GNU configure script.
It's going to run a bunch of tests to hopefully make your compile
work without much twiddling.

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
~/eggdrop1.6.19$ 

Can someone tell me how to start my eggdrop, thanks in advice.

---

### Post by cdtech on 2008-05-24
sudo apt-get install build-essential

Then try to ./configure

---

### Post by _Silver on 2008-05-24
> **cdtech said:**
> sudo apt-get install build-essential

Then try to ./configure

Thank you for your last post, but I have a new problem now
How to install Tcl?

configure: error:

  Tcl cannot be found on this system.

  Eggdrop requires Tcl to compile. If you already have Tcl installed on
  this system, and I just wasn't looking in the right place for it, re-run
  ./configure using the --with-tcllib='/path/to/libtcl.so' and
  --with-tclinc='/path/to/tcl.h' options.

  See doc/COMPILE-GUIDE's 'Tcl Detection and Installation' section for more
  information.

---

### Post by Hossie on 2008-05-24
```
sudo apt-get install tcl tcl-dev
```

---

### Post by L0cKd0wN on 2008-06-11
This helped me a lot, thank you! :)

---

