---
title: "cmake bug or my bad?"
date: 2014-02-13
forum: Programming Talk
---

### Post by kangaba on 2014-02-13
Hi,
Here's part of my CMakeLists.txt file on Windows 7:
```

find_package(PkgConfig)
pkg_check_modules(Zlib zlib)
if (Zlib_FOUND)
    include_directories(${Zlib_INCLUDE_DIRS})
    link_directories(${Zlib_LIBRARY_DIRS})
endif (Zlib_FOUND)
```
 **link_directories**(..) is the problem, because for some reason ${Zlib_LIBRARY_DIRS} equals to
C:/Program;Files;(x86)/zlib/lib
instead of
C:/Program Files (x86)/zlib/lib
I know this from doing: message(STATUS "Zlib library dirs: ${Zlib_LIBRARY_DIRS}")

Is it a bug in Windows, cmake or my bad?

zlib.pc is installed at
C:\Program Files (x86)\zlib\share\pkgconfig
 and reads:
```
prefix=C:/Program Files (x86)/zlib
exec_prefix=C:/Program Files (x86)/zlib
libdir=C:/Program Files (x86)/zlib/lib
sharedlibdir=C:/Program Files (x86)/zlib/lib
includedir=C:/Program Files (x86)/zlib/include

Name: zlib
Description: zlib compression library
Version: 1.2.8

Requires:
Libs: -L${libdir} -L${sharedlibdir} -lz
Cflags: -I${includedir}


```

---

### Post by xb12x2 on 2014-02-13
Here's a link that might help:

[URL="https://stackoverflow.com/questions/3328199/how-to-specify-a-path-with-white-space-in-it-with-cmake"]https://stackoverflow.com/questions/3328199/how-to-specify-a-path-with-white-space-in-it-with-cmake



[/URL]

---

### Post by kangaba on 2014-02-14
Thanks, however I've got a variable, not a string whose contents I write myself.

---

