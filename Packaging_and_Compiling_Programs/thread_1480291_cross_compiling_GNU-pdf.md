---
title: "cross compiling GNU-pdf"
date: 2010-05-11
forum: Packaging and Compiling Programs
---

### Post by Zubair Ahmed on 2010-05-11
When i do ./configure --build i686-pc-linux-gnu --host i586-mingw32msvc 
I get:
checking zlib in ... failed
configure: error: either specify a valid zlib installation with --with-zlib=DIR or disable zlib usage with --without-zlib

Whereas zlib (package zlibc) is installed in my system. When i run "locate zlib " i get:

/usr/include/zlib.h
/usr/include/zlibdefs.h
/usr/src/linux-headers-2.6.31-14/include/linux/zlib.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/zlib
/usr/src/linux-headers-2.6.31-14-generic/include/config/crypto/zlib.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/jffs2/zlib.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/ubifs/fs/zlib.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/zlib/deflate.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/zlib/inflate.h
/usr/src/linux-headers-2.6.31-14-generic/include/linux/zlib.h
/usr/src/linux-headers-2.6.31-20/include/linux/zlib.h
/usr/src/linux-headers-2.6.31-20-generic/include/config/zlib
/usr/src/linux-headers-2.6.31-20-generic/include/config/crypto/zlib.h
/usr/src/linux-headers-2.6.31-20-generic/include/config/jffs2/zlib.h
/usr/src/linux-headers-2.6.31-20-generic/include/config/ubifs/fs/zlib.h
/usr/src/linux-headers-2.6.31-20-generic/include/config/zlib/deflate.h
/usr/src/linux-headers-2.6.31-20-generic/include/config/zlib/inflate.h
/usr/src/linux-headers-2.6.31-20-generic/include/linux/zlib.h
/usr/src/linux-headers-2.6.31-21/include/linux/zlib.h
/usr/src/linux-headers-2.6.31-21-generic/include/config/zlib
/usr/src/linux-headers-2.6.31-21-generic/include/config/crypto/zlib.h
/usr/src/linux-headers-2.6.31-21-generic/include/config/jffs2/zlib.h
/usr/src/linux-headers-2.6.31-21-generic/include/config/ubifs/fs/zlib.h
/usr/src/linux-headers-2.6.31-21-generic/include/config/zlib/deflate.h
/usr/src/linux-headers-2.6.31-21-generic/include/config/zlib/inflate.h
/usr/src/linux-headers-2.6.31-21-generic/include/linux/zlib.h

May be i need to correctly provide --with-zlib=DIR , but i ve tried that too.

---

### Post by qyot27 on 2010-05-12
You need to cross-compile zlib. mingw doesn't see it because dependencies need to be compiled with mingw as well.

---

