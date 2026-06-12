---
title: "Error: Try cross compiling at Ubuntu 18.04 for Cubieboard"
date: 2019-09-09
forum: Programming Talk
---

### Post by blaubart on 2019-09-09
Last week I tried to cross compile a program (XCSoar) for Cubieboard. I used Ubuntu 18.04 and the following Dev manual: [download/file.php?id=1017]("https://forum.xcsoar.org/download/file.php?id=1017") for XCSoar7.0.

```
mkdir OpenVariocd OpenVario
git clone git://github.com/XCSoar/XCSoar
cd XCSoar
git pull
git submodule init
git submodule update


sudo apt-get install make librsvg2-bin xsltproc imagemagick gettext ffmpeg git quilt zip m4 automake ttf-bitstream-vera fakeroot g++-arm-linux-gnueabihf


sudo apt-get install make g++ zlib1g-dev libfreetype6-dev libpng-dev libjpeg-dev libtiff5-dev libgeotiff-dev libcurl4-openssl-dev liblua5.2-dev lua5.2-dev libxml-parser-perl libasound2-dev librsvg2-bin xsltproc imagemagick gettext mesa-common-dev libgl1-mesa-dev libegl1-mesa-dev fonts-dejavu


export PKG_CONFIG_PATH=/usr/lib/x86_64-linux-gnu/pkgconfig


make TARGET=CUBIE
```

It ends in an error and I found almost nothing about this error in the internet:

```
CXX     output/CUBIE/dbg/src/IO/MapFile.oIn file included from /usr/arm-linux-gnueabihf/include/wchar.h:30:0,
                 from /usr/arm-linux-gnueabihf/include/c++/7/cwchar:44,
                 from /usr/arm-linux-gnueabihf/include/c++/7/bits/postypes.h:40,
                 from /usr/arm-linux-gnueabihf/include/c++/7/iosfwd:40,
                 from /usr/arm-linux-gnueabihf/include/c++/7/memory:72,
                 from src/IO/MapFile.hpp:27,
                 from src/IO/MapFile.cpp:24:
/usr/include/x86_64-linux-gnu/bits/floatn.h:75:70: error: unknown machine mode ‘__TC__’
 typedef _Complex float __cfloat128 __attribute__ ((__mode__ (__TC__)));
                                                                      ^
/usr/include/x86_64-linux-gnu/bits/floatn.h:87:9: error: ‘__float128’ does not name a type; did you mean ‘__cfloat128’?
 typedef __float128 _Float128;
         ^~~~~~~~~~
         __cfloat128
In file included from /usr/arm-linux-gnueabihf/include/c++/7/cwchar:44:0,
                 from /usr/arm-linux-gnueabihf/include/c++/7/bits/postypes.h:40,
                 from /usr/arm-linux-gnueabihf/include/c++/7/iosfwd:40,
                 from /usr/arm-linux-gnueabihf/include/c++/7/memory:72,
                 from src/IO/MapFile.hpp:27,
                 from src/IO/MapFile.cpp:24:
/usr/arm-linux-gnueabihf/include/wchar.h:406:8: error: ‘_Float128’ does not name a type; did you mean ‘_Float32x’?
 extern _Float128 wcstof128 (const wchar_t *__restrict __nptr,
        ^~~~~~~~~
        _Float32x
/usr/arm-linux-gnueabihf/include/wchar.h:523:8: error: ‘_Float128’ does not name a type; did you mean ‘_Float32x’?
 extern _Float128 wcstof128_l (const wchar_t *__restrict __nptr,
        ^~~~~~~~~
        _Float32x
In file included from /usr/arm-linux-gnueabihf/include/c++/7/cstdlib:75:0,
                 from /usr/arm-linux-gnueabihf/include/c++/7/ext/string_conversions.h:41,
                 from /usr/arm-linux-gnueabihf/include/c++/7/bits/basic_string.h:6361,
                 from /usr/arm-linux-gnueabihf/include/c++/7/string:52,
                 from /usr/arm-linux-gnueabihf/include/c++/7/stdexcept:39,
                 from /usr/arm-linux-gnueabihf/include/c++/7/array:39,
                 from /usr/arm-linux-gnueabihf/include/c++/7/tuple:39,
                 from /usr/arm-linux-gnueabihf/include/c++/7/bits/unique_ptr.h:37,
                 from /usr/arm-linux-gnueabihf/include/c++/7/memory:80,
                 from src/IO/MapFile.hpp:27,
                 from src/IO/MapFile.cpp:24:
/usr/arm-linux-gnueabihf/include/stdlib.h:152:8: error: ‘_Float128’ does not name a type; did you mean ‘_Float32x’?
 extern _Float128 strtof128 (const char *__restrict __nptr,
        ^~~~~~~~~
        _Float32x
/usr/arm-linux-gnueabihf/include/stdlib.h:245:4: error: ‘_Float128’ has not been declared
    _Float128 __f)
    ^~~~~~~~~
/usr/arm-linux-gnueabihf/include/stdlib.h:330:8: error: ‘_Float128’ does not name a type; did you mean ‘_Float32x’?
 extern _Float128 strtof128_l (const char *__restrict __nptr,
        ^~~~~~~~~
        _Float32x
build/compile.mk:107: recipe for target 'output/CUBIE/dbg/src/IO/MapFile.o' failed
make: *** [output/CUBIE/dbg/src/IO/MapFile.o] Error 1
```

Has someone an idea, why I get this error with float128??

---

### Post by norobro on 2019-09-09
[FONT=arial]This is just a WAG since I know nothing about this program or cross compiling for the arm architecture.

```
/usr/include/x86_64-linux-gnu/bits/floatn.h: ...
```The above looks suspicious to me. Shouldn't the compiler be looking in "/usr/arm-linux-gnueabihf/include/bits" for floatn.h?

Are your apt-get commands from the build instructions for the app? It seems to me that you need a few more packages to cross compile.  [https://packages.ubuntu.com/bionic/gcc-arm-linux-gnueabi](https://packages.ubuntu.com/bionic/gcc-arm-linux-gnueabi)

The floatn.h header file is in libc6-dev-armel-cross. [https://packages.ubuntu.com/bionic-updates/all/libc6-dev-armel-cross/filelist](https://packages.ubuntu.com/bionic-updates/all/libc6-dev-armel-cross/filelist)
Try: ```
apt-get install gcc-arm-linux-gnueabi
```Hope this helps.[/FONT]

---

### Post by blaubart on 2019-09-13
after apt-get install gcc-arm-linux-gnueabi I get exactly the same error

I found floatn.h at /usr/include/x86_64-linux-gnu/bits/ and /usr/arm-linux-gnueabihf/include/bits

---

