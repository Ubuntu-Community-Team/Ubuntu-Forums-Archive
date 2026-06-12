---
title: "cannot compile program that need zlib"
date: 2009-02-23
forum: Packaging and Compiling Programs
---

### Post by dadakiller on 2009-02-23
when i cross-compile mysql++-3.0.9
compiler say ->configure: error: zlib not found

i have been try to 
1 download zlib or zlib*
or
2 apt-get install libreadline5-dev zlib1g-dev
or
3 ./configure --without-readline --without-zlib

but have same error
can anyone tell me what can i do,thanks

cpu is amd athlon(tm)64 x2 dural
ap is asus wl500w
os is ubuntu-8.10-desktop-i386

here is part of terminal message
-----------------------------------------------------------------

```

root@dada-D:/home/dada/Desktop/123/mysql++-3.0.9# ./configure --host=mipsel --prefix=/home/dada/Desktop/456 --without-zlib
configure: WARNING: If you wanted to set the --build type, don't use --host.
    If a cross compiler is detected then cross compile mode will be used.
checking build system type... i686-pc-linux-gnu
checking host system type... mipsel-unknown-elf
checking target system type... mipsel-unknown-elf
checking for mipsel-gcc... mipsel-gcc
checking for C compiler default output file name... a.out
..
..
..
..
checking whether -lnsl is needed... no
checking for MySQL library directory... /usr/lib
checking for MySQL include directory... /usr/include/mysql
checking if we can link to MySQL C API library directly... no
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for gzread in -lz... no
configure: error: zlib not found


```

here is part of  config.log
-----------------------------------------------------------------
```

...
...

configure:9026: checking if we can link to MySQL C API library directly
configure:9046: mipsel-gcc -o conftest -g -O2  -I/usr/include/mysql  conftest.c  -lmysqlclient  >&5
/home/dada/cross-compiler-mipsel/bin/../libexec/gcc/mipsel-unknown-linux/4.1.2/collect2: cannot find -lmysqlclient
configure:9052: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "mysql++"
| #define PACKAGE_TARNAME "mysql++"
| #define PACKAGE_VERSION "3.0.9"
| #define PACKAGE_STRING "mysql++ 3.0.9"
| #define PACKAGE_BUGREPORT "plusplus@lists.mysql.com"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| /* end confdefs.h.  */
|  #include <mysql.h>
| int
| main ()
| {
|  mysql_store_result(0);
|   ;
|   return 0;
| }
configure:9073: result: no
configure:9090: checking zlib.h usability
configure:9102: mipsel-gcc -c -g -O2  -I/usr/include/mysql conftest.c >&5
configure:9108: $? = 0
configure:9112: test -z 
             || test ! -s conftest.err
configure:9115: $? = 0
configure:9118: test -s conftest.o
configure:9121: $? = 0
configure:9131: result: yes
configure:9135: checking zlib.h presence
configure:9145: mipsel-gcc -E  -I/usr/include/mysql conftest.c
configure:9151: $? = 0
configure:9171: result: yes
configure:9206: checking for zlib.h
configure:9213: result: yes
configure:9222: checking for gzread in -lz
configure:9252: mipsel-gcc -o conftest -g -O2  -I/usr/include/mysql  conftest.c -lz   >&5
/home/dada/cross-compiler-mipsel/bin/../libexec/gcc/mipsel-unknown-linux/4.1.2/collect2: cannot find -lz
configure:9258: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "mysql++"
| #define PACKAGE_TARNAME "mysql++"
| #define PACKAGE_VERSION "3.0.9"
| #define PACKAGE_STRING "mysql++ 3.0.9"
| #define PACKAGE_BUGREPORT "plusplus@lists.mysql.com"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_ZLIB_H 1
| /* end confdefs.h.  */
| 
| /* Override any gcc2 internal prototype to avoid an error.  */
| #ifdef __cplusplus
| extern "C"
| #endif
| /* We use char because int might match the return type of a gcc2
|    builtin and then its argument prototype would still apply.  */
| char gzread ();
| int
| main ()
| {
| gzread ();
|   ;
|   return 0;
| }
configure:9284: result: no
configure:9294: error: zlib not found

```

---

