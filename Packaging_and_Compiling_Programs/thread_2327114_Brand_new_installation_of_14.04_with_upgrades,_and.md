---
title: "Brand new installation of 14.04 with upgrades, and g++ with gtkmm NG"
date: 2016-06-07
forum: Packaging and Compiling Programs
---

### Post by Gran3D on 2016-06-07
This is brand new system.  Started with blank 50GB hard drive and the 14.04 distribution DVD.  Loaded all up.  Seems OK. 
Problem comes when trying compile my old sudoku program which was originally developed with anjuta.  Cant get it to go using the shell
I use:

cd Desktop/LWG/sud
g++ -v -o sud -I/usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/include/gtkmm-3.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include bar.cc SudokuBasics.cc jar.cc unit.cc hole.cc wiggle.cc main.cc

and get

lawrence@deskdell:~$ cd Desktop/LWG/sud
lawrence@deskdell:~/Desktop/LWG/sud$ g++ -v -o sud -I/usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/include/gtkmm-3.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include bar.cc SudokuBasics.cc jar.cc unit.cc hole.cc wiggle.cc main.cc
Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.8/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.4-2ubuntu1~14.04.3' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3) 
COLLECT_GCC_OPTIONS='-v' '-o' 'sud' '-I' '/usr/lib/x86_64-linux-gnu/glibmm-2.4/include' '-I' '/usr/include/glibmm-2.4' '-I' '/usr/include/gtkmm-3.0' '-I' '/usr/include/glib-2.0' '-I' '/usr/lib/x86_64-linux-gnu/glib-2.0/include' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1plus -quiet -v -I /usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I /usr/include/glibmm-2.4 -I /usr/include/gtkmm-3.0 -I /usr/include/glib-2.0 -I /usr/lib/x86_64-linux-gnu/glib-2.0/include -imultiarch x86_64-linux-gnu -D_GNU_SOURCE bar.cc -quiet -dumpbase bar.cc -mtune=generic -march=x86-64 -auxbase bar -version -fstack-protector -Wformat -Wformat-security -o /tmp/ccdW06OT.s
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring duplicate directory "/usr/include/x86_64-linux-gnu/c++/4.8"
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/x86_64-linux-gnu/glibmm-2.4/include
 /usr/include/glibmm-2.4
 /usr/include/gtkmm-3.0
 /usr/include/glib-2.0
 /usr/lib/x86_64-linux-gnu/glib-2.0/include
 /usr/include/c++/4.8
 /usr/include/x86_64-linux-gnu/c++/4.8
 /usr/include/c++/4.8/backward
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 9ddcbef7de15d896f5df83657bc78822
In file included from /usr/include/glibmm-2.4/glibmm.h:87:0,
                 from /usr/include/gtkmm-3.0/gtkmm.h:87,
                 from sudmat.h:21,
                 from bar.cc:3:
/usr/include/glibmm-2.4/glibmm/thread.h:58:27: fatal error: sigc++/sigc++.h: No such file or directory
 #include <sigc++/sigc++.h>
                           ^
compilation terminated.
COLLECT_GCC_OPTIONS='-v' '-o' 'sud' '-I' '/usr/lib/x86_64-linux-gnu/glibmm-2.4/include' '-I' '/usr/include/glibmm-2.4' '-I' '/usr/include/gtkmm-3.0' '-I' '/usr/include/glib-2.0' '-I' '/usr/lib/x86_64-linux-gnu/glib-2.0/include' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1plus -quiet -v -I /usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I /usr/include/glibmm-2.4 -I /usr/include/gtkmm-3.0 -I /usr/include/glib-2.0 -I /usr/lib/x86_64-linux-gnu/glib-2.0/include -imultiarch x86_64-linux-gnu -D_GNU_SOURCE SudokuBasics.cc -quiet -dumpbase SudokuBasics.cc -mtune=generic -march=x86-64 -auxbase SudokuBasics -version -fstack-protector -Wformat -Wformat-security -o /tmp/ccdW06OT.s
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring duplicate directory "/usr/include/x86_64-linux-gnu/c++/4.8"
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/x86_64-linux-gnu/glibmm-2.4/include
 /usr/include/glibmm-2.4
 /usr/include/gtkmm-3.0
 /usr/include/glib-2.0
 /usr/lib/x86_64-linux-gnu/glib-2.0/include
 /usr/include/c++/4.8
 /usr/include/x86_64-linux-gnu/c++/4.8
 /usr/include/c++/4.8/backward
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 9ddcbef7de15d896f5df83657bc78822
In file included from /usr/include/glibmm-2.4/glibmm.h:87:0,
                 from /usr/include/gtkmm-3.0/gtkmm.h:87,
                 from sudmat.h:21,
                 from SudokuBasics.cc:3:
/usr/include/glibmm-2.4/glibmm/thread.h:58:27: fatal error: sigc++/sigc++.h: No such file or directory
 #include <sigc++/sigc++.h>
                           ^
compilation terminated.
COLLECT_GCC_OPTIONS='-v' '-o' 'sud' '-I' '/usr/lib/x86_64-linux-gnu/glibmm-2.4/include' '-I' '/usr/include/glibmm-2.4' '-I' '/usr/include/gtkmm-3.0' '-I' '/usr/include/glib-2.0' '-I' '/usr/lib/x86_64-linux-gnu/glib-2.0/include' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1plus -quiet -v -I /usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I /usr/include/glibmm-2.4 -I /usr/include/gtkmm-3.0 -I /usr/include/glib-2.0 -I /usr/lib/x86_64-linux-gnu/glib-2.0/include -imultiarch x86_64-linux-gnu -D_GNU_SOURCE jar.cc -quiet -dumpbase jar.cc -mtune=generic -march=x86-64 -auxbase jar -version -fstack-protector -Wformat -Wformat-security -o /tmp/ccdW06OT.s
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring duplicate directory "/usr/include/x86_64-linux-gnu/c++/4.8"
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/x86_64-linux-gnu/glibmm-2.4/include
 /usr/include/glibmm-2.4
 /usr/include/gtkmm-3.0
 /usr/include/glib-2.0
 /usr/lib/x86_64-linux-gnu/glib-2.0/include
 /usr/include/c++/4.8
 /usr/include/x86_64-linux-gnu/c++/4.8
 /usr/include/c++/4.8/backward
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 9ddcbef7de15d896f5df83657bc78822
In file included from /usr/include/glibmm-2.4/glibmm.h:87:0,
                 from /usr/include/gtkmm-3.0/gtkmm.h:87,
                 from jar.h:22,
                 from jar.cc:20:
/usr/include/glibmm-2.4/glibmm/thread.h:58:27: fatal error: sigc++/sigc++.h: No such file or directory
 #include <sigc++/sigc++.h>
                           ^
compilation terminated.
COLLECT_GCC_OPTIONS='-v' '-o' 'sud' '-I' '/usr/lib/x86_64-linux-gnu/glibmm-2.4/include' '-I' '/usr/include/glibmm-2.4' '-I' '/usr/include/gtkmm-3.0' '-I' '/usr/include/glib-2.0' '-I' '/usr/lib/x86_64-linux-gnu/glib-2.0/include' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1plus -quiet -v -I /usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I /usr/include/glibmm-2.4 -I /usr/include/gtkmm-3.0 -I /usr/include/glib-2.0 -I /usr/lib/x86_64-linux-gnu/glib-2.0/include -imultiarch x86_64-linux-gnu -D_GNU_SOURCE unit.cc -quiet -dumpbase unit.cc -mtune=generic -march=x86-64 -auxbase unit -version -fstack-protector -Wformat -Wformat-security -o /tmp/ccdW06OT.s
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring duplicate directory "/usr/include/x86_64-linux-gnu/c++/4.8"
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/x86_64-linux-gnu/glibmm-2.4/include
 /usr/include/glibmm-2.4
 /usr/include/gtkmm-3.0
 /usr/include/glib-2.0
 /usr/lib/x86_64-linux-gnu/glib-2.0/include
 /usr/include/c++/4.8
 /usr/include/x86_64-linux-gnu/c++/4.8
 /usr/include/c++/4.8/backward
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 9ddcbef7de15d896f5df83657bc78822
In file included from /usr/include/glibmm-2.4/glibmm.h:87:0,
                 from /usr/include/gtkmm-3.0/gtkmm.h:87,
                 from sudmat.h:21,
                 from unit.cc:13:
/usr/include/glibmm-2.4/glibmm/thread.h:58:27: fatal error: sigc++/sigc++.h: No such file or directory
 #include <sigc++/sigc++.h>
                           ^
compilation terminated.
COLLECT_GCC_OPTIONS='-v' '-o' 'sud' '-I' '/usr/lib/x86_64-linux-gnu/glibmm-2.4/include' '-I' '/usr/include/glibmm-2.4' '-I' '/usr/include/gtkmm-3.0' '-I' '/usr/include/glib-2.0' '-I' '/usr/lib/x86_64-linux-gnu/glib-2.0/include' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1plus -quiet -v -I /usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I /usr/include/glibmm-2.4 -I /usr/include/gtkmm-3.0 -I /usr/include/glib-2.0 -I /usr/lib/x86_64-linux-gnu/glib-2.0/include -imultiarch x86_64-linux-gnu -D_GNU_SOURCE hole.cc -quiet -dumpbase hole.cc -mtune=generic -march=x86-64 -auxbase hole -version -fstack-protector -Wformat -Wformat-security -o /tmp/ccdW06OT.s
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring duplicate directory "/usr/include/x86_64-linux-gnu/c++/4.8"
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/x86_64-linux-gnu/glibmm-2.4/include
 /usr/include/glibmm-2.4
 /usr/include/gtkmm-3.0
 /usr/include/glib-2.0
 /usr/lib/x86_64-linux-gnu/glib-2.0/include
 /usr/include/c++/4.8
 /usr/include/x86_64-linux-gnu/c++/4.8
 /usr/include/c++/4.8/backward
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 9ddcbef7de15d896f5df83657bc78822
In file included from /usr/include/glibmm-2.4/glibmm.h:87:0,
                 from /usr/include/gtkmm-3.0/gtkmm.h:87,
                 from sudmat.h:21,
                 from hole.cc:20:
/usr/include/glibmm-2.4/glibmm/thread.h:58:27: fatal error: sigc++/sigc++.h: No such file or directory
 #include <sigc++/sigc++.h>
                           ^
compilation terminated.
COLLECT_GCC_OPTIONS='-v' '-o' 'sud' '-I' '/usr/lib/x86_64-linux-gnu/glibmm-2.4/include' '-I' '/usr/include/glibmm-2.4' '-I' '/usr/include/gtkmm-3.0' '-I' '/usr/include/glib-2.0' '-I' '/usr/lib/x86_64-linux-gnu/glib-2.0/include' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1plus -quiet -v -I /usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I /usr/include/glibmm-2.4 -I /usr/include/gtkmm-3.0 -I /usr/include/glib-2.0 -I /usr/lib/x86_64-linux-gnu/glib-2.0/include -imultiarch x86_64-linux-gnu -D_GNU_SOURCE wiggle.cc -quiet -dumpbase wiggle.cc -mtune=generic -march=x86-64 -auxbase wiggle -version -fstack-protector -Wformat -Wformat-security -o /tmp/ccdW06OT.s
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring duplicate directory "/usr/include/x86_64-linux-gnu/c++/4.8"
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/x86_64-linux-gnu/glibmm-2.4/include
 /usr/include/glibmm-2.4
 /usr/include/gtkmm-3.0
 /usr/include/glib-2.0
 /usr/lib/x86_64-linux-gnu/glib-2.0/include
 /usr/include/c++/4.8
 /usr/include/x86_64-linux-gnu/c++/4.8
 /usr/include/c++/4.8/backward
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 9ddcbef7de15d896f5df83657bc78822
In file included from /usr/include/glibmm-2.4/glibmm.h:87:0,
                 from /usr/include/gtkmm-3.0/gtkmm.h:87,
                 from sudmat.h:21,
                 from wiggle.cc:1:
/usr/include/glibmm-2.4/glibmm/thread.h:58:27: fatal error: sigc++/sigc++.h: No such file or directory
 #include <sigc++/sigc++.h>
                           ^
compilation terminated.
COLLECT_GCC_OPTIONS='-v' '-o' 'sud' '-I' '/usr/lib/x86_64-linux-gnu/glibmm-2.4/include' '-I' '/usr/include/glibmm-2.4' '-I' '/usr/include/gtkmm-3.0' '-I' '/usr/include/glib-2.0' '-I' '/usr/lib/x86_64-linux-gnu/glib-2.0/include' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1plus -quiet -v -I /usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I /usr/include/glibmm-2.4 -I /usr/include/gtkmm-3.0 -I /usr/include/glib-2.0 -I /usr/lib/x86_64-linux-gnu/glib-2.0/include -imultiarch x86_64-linux-gnu -D_GNU_SOURCE main.cc -quiet -dumpbase main.cc -mtune=generic -march=x86-64 -auxbase main -version -fstack-protector -Wformat -Wformat-security -o /tmp/ccdW06OT.s
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring duplicate directory "/usr/include/x86_64-linux-gnu/c++/4.8"
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/x86_64-linux-gnu/glibmm-2.4/include
 /usr/include/glibmm-2.4
 /usr/include/gtkmm-3.0
 /usr/include/glib-2.0
 /usr/lib/x86_64-linux-gnu/glib-2.0/include
 /usr/include/c++/4.8
 /usr/include/x86_64-linux-gnu/c++/4.8
 /usr/include/c++/4.8/backward
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
GNU C++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 9ddcbef7de15d896f5df83657bc78822
In file included from /usr/include/glibmm-2.4/glibmm.h:87:0,
                 from /usr/include/gtkmm-3.0/gtkmm.h:87,
                 from sudmat.h:21,
                 from main.cc:2:
/usr/include/glibmm-2.4/glibmm/thread.h:58:27: fatal error: sigc++/sigc++.h: No such file or directory
 #include <sigc++/sigc++.h>
                           ^
compilation terminated.
lawrence@deskdell:~/Desktop/LWG/sud$ 

Does anybody know where to go from here?

---

### Post by steeldriver on 2016-06-07
I'd suggest using pkg-config - something like

```

g++ -o sud bar.cc SudokuBasics.cc jar.cc unit.cc hole.cc wiggle.cc main.cc `pkg-config --cflags --libs glibmm-2.4`

```
or
```

g++ -o sud `pkg-config --cflags glibmm-2.4` bar.cc SudokuBasics.cc jar.cc unit.cc hole.cc wiggle.cc main.cc `pkg-config --libs glibmm-2.4`

```

If you want to do it manually, then run 

```

pkg-config --cflags --libs glibmm-2.4

```

or (separately)

```

pkg-config --cflags glibmm-2.4

pkg-config --libs glibmm-2.4

```

to see what the suggested include / library directives are.

You may need to play with the order of your .cc files as well - normally, they (as well as the libraries they link) need to go in order from "high" to "low"

---

