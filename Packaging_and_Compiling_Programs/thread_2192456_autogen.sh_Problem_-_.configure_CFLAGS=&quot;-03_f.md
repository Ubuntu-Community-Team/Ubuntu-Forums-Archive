---
title: "autogen.sh Problem - ./configure CFLAGS=&quot;-03 fails"
date: 2013-12-07
forum: Packaging and Compiling Programs
---

### Post by Resistent on 2013-12-07
Hi all,

My first compile with ./autogen.sh , and problem.


[LIST=1]
[*]I get the quarkcoin-cpuminer-2.3.2.tar.gz file from [https://github.com/Neisklar/quarkcoin-cpuminer/releases](https://github.com/Neisklar/quarkcoin-cpuminer/releases)
[*]Extracted to the folder quarkcoin-cpuminer-2.3.2
[*]entered this directory
[*]executed ```
[FONT=dejavu sans mono]./autogen.sh[/FONT]
```[FONT=dejavu sans mono]
(which gives me a Warning, but can be ignored I think, I am right?
```
Makefile.am:12: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')

```[/FONT]
[*]Then I exetuded ./configure CFLAGS="-03" as [advised]("http://quark.freeforums.net/thread/173/mine-linux-mining-step-quark?page=1&scrollTo=2653") , but get this, so [COLOR=#ff0000]no "Makefile" was created[/COLOR]
```
hecking build system type... x86_64-unknown-linux-gnuchecking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
[COLOR=#ff0000]checking whether the C compiler works... no[/COLOR]
configure: error: in `/home/istvan/Downloads/quarkcoin-cpuminer-2.3.2':
[COLOR=#ff0000]configure: error: C compiler cannot create executables[/COLOR]
See `[COLOR=#ff0000]config.log[/COLOR]' for more details

```
[*]Says, whether the C compiler works... no
[*]In config.log in the middle I found this (is this enough for identify the problem?)```
configure:3387: $? = 0configure:3376: gcc -v >&5
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.8/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.8.1-10ubuntu9' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu9) 
configure:3387: $? = 0
configure:3376: gcc -V >&5
[COLOR=#ff0000]gcc: error: unrecognized command line option '-V'[/COLOR]
[COLOR=#ff0000]gcc: fatal error: no input files[/COLOR]
compilation terminated.
configure:3387: $? = 4
configure:3376: gcc -qversion >&5
[COLOR=#ff0000]gcc: error: unrecognized command line option '-qversion'[/COLOR]
[COLOR=#ff0000]gcc: fatal error: no input files[/COLOR]
[COLOR=#ff0000]compilation terminated.[/COLOR]
configure:3387: $? = 4
configure:3407: checking whether the C compiler works
configure:3429: gcc -03   conftest.c  >&5
[COLOR=#ff0000]gcc: error: unrecognized command line option '-03'[/COLOR]
configure:3433: $? = 1
configure:3471: result: no
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "cpuminer"
| #define PACKAGE_TARNAME "cpuminer"
| #define PACKAGE_VERSION "2.3.2"
| #define PACKAGE_STRING "cpuminer 2.3.2"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE_URL ""
| #define PACKAGE "cpuminer"
| #define VERSION "2.3.2"
| /* end confdefs.h.  */
```
[/LIST]

Does this mean that I cannot use ```
./configure CFLAGS="-03"
``` 
so I cannot use CFLAGS="-Zero3"  ?

The last step would be to execute "makefile", but I cannot as "Makefile" file was not generated.

Can anybody help me?

thx

---

### Post by morgrum on 2014-01-13
That's the "Optimize" flag.  It should be the letter O, not a zero.

---

