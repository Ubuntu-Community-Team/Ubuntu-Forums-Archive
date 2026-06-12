---
title: "mingw32 cross-compile libs"
date: 2006-06-13
forum: Programming Talk
---

### Post by quintok on 2006-06-13
I'm attempting to build wine's crosstest applications so that they work under win32 (to debug etc).  I've installed mingw* (binutils and runtime) however I'm still missing libraries or so it says.

when it gets to advpack test (from current cvs) it complains that lcabinet is missing.  I asked in the IRC and they directed me to make the library myself, which I did (as it's part of wine)... by doing:
dlls/cabinet/$ make libcabinet.a
which made libcabinet.a and libcabinet.def, I moved them to /usr/i586-mingw32msvc/lib/ which was where all the other .a files were.  Then it said I had missing symbols from the libcabinet.a but didn't say which (nor did ranlib help).

Is there a mingw32 win32 library I'm missing from the ubuntu repositories, if not... any suggestions on how to fix?

---

### Post by toojays on 2006-06-14
There are three mingw packages (mingw, mingw-binutils, mingw-runtime) which should provide everything you need.

Do the wine developers use mingw to build their testsuite? I would've thought they'd use winegcc.

Try grabbing the [deb source used by WineHQ](http://www.winehq.org/site/download-deb), and see if that builds the tests.

Post the output of the build log where your error is and someone might be able to help you better.

---

