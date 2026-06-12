---
title: "autoconf and static libraries"
date: 2006-08-16
forum: Programming Talk
---

### Post by slightly72 on 2006-08-16
This is probably not a strictly Ubuntu topic, but here it goes.

I'm working on some software (call it "foo") that'll be integrated with a public domain CAD tool (call it "bar"). "bar" installs both some binaries and a static library (say, "libbar.a") in its directory (/usr/local/bar).

I'm using the autoconf and automake tools to generate the makefiles and whatnot for "foo", but have a problem with making autoconf automatically generate the appropriate compiler flags for linking libbar.a with foo. I've tried AC_CHECK_LIB, but it either cannot find libbar.a (I've set up LD_LIBRARY_PATH to /usr/local/bar/lib, where libbar.a is installed) or cannot process static libraries.

My current solution is to add to Makefile.am 

foo_LDFLAGS = -L/usr/local/bar/lib

but it's not a good solution -- since foo's going to be public domain, cannot predict where the users might have installed bar.

So, is there a way to have autoconf (or the "configure") script detect the location of libbar.a? I've searched in autoconf manuals, but all examples seem to refer to dynamic libraries.

I'm using autoconf 2.59, automake 1.9.6 -- working on Dapper.

Thank you.

---

### Post by simonn on 2006-08-17
If it is a static library it will be compiled into the executable, so it does not need to be installed on the users system - that's the difference between static and dynamic libraries.

---

### Post by slightly72 on 2006-08-17
Right, correct.

After a lot more tries, it seems that autoconf will detect static libraries and set up the appropriate compilation flags, but depends on where the library is. That is, I've copied libbar.a to /usr/lib, and everything was fine with AC_CHECK_LIB. I still haven't figured out in which directories AC_CHECK_LIB searches for libraries (and that's a curious ommission in the GNU autoconf docs) -- or, for that matter, how to add new directories (e.g. those in the $LD_LIBRARY_PATH) to the default search path.

If anyone can help, I'd really appreciate it.

Another solution is to add a switch to configure, which allows the user to specify where the libs are. That might be the appropriate solution in the end.

---

