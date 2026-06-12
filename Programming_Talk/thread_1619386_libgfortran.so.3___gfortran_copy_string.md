---
title: "libgfortran.so.3  _gfortran_copy_string"
date: 2010-11-11
forum: Programming Talk
---

### Post by darius007 on 2010-11-11
Hi 

I am running a code that needs certain libgfortran libraries.  Unfortunately I get this error message that  libgfortran.so.1 is  missing:

 libgfortran.so.1: cannot open shared object file: No such file or directory

I linked the ligfortran library as follows: sudo ln -s /usr/lib/libgfortran.so.3 /usr/lib/libgfortran.so.1

and now I got this error:

symbol lookup errorsymbol lookup error: :  ../../program/main/liblapack.so.3../../program/main/liblapack.so.3: :  undefined symbol: _gfortran_copy_stringundefined symbol:  _gfortran_copy_string

Thanks for your help.
Darius

---

### Post by Some Penguin on 2010-11-11
Probably a non-backwards-compatible API change.  Find and install a 1.x version of the gfortran library.

---

### Post by Iowan on 2010-11-12
Duplicate:
[http://ubuntuforums.org/showthread.php?t=1619388]("http://ubuntuforums.org/showthread.php?t=1619388")
From Code of Conduct:
> Do not cross post, or post the same thing in multiple locations.

---

