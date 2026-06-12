---
title: "C++ standard library path"
date: 2009-02-11
forum: Programming Talk
---

### Post by ehsan.s on 2009-02-11
hi.
I have a trouble with making some source codes. when I make sources it has an error that says some header files not found (e.g. vector.h).
I've compiled these sources in SUSE Linux and no error has been occured.
I guess standard library file names in ubuntu has been changed or standard library path has not been set properly.
can anybody help me?
thank you

---

### Post by Victor Liu on 2009-02-11
C++ standard headers are usually in /usr/include. What header files are missing? By the way, the C++ standard filename for vector is just <vector> without the extension.

---

### Post by jespdj on 2009-02-11
Install the package **build-essential** to get the C/C++ compiler and the header files for the standard libraries:
```
sudo apt-get install build-essential
```
For most other libraries, there's a "...-dev" package. If the program that you are trying to compile uses certain libraries, then install the "libsomething-dev" package for that library.

---

### Post by ehsan.s on 2009-02-11
I made the changes but it still has same problems. if there is older version of libraries, can you tell me how to install it?
I completely mixed up.

---

