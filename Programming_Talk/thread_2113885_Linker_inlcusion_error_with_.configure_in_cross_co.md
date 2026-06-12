---
title: "Linker inlcusion error with ./configure in cross compilation"
date: 2013-02-08
forum: Programming Talk
---

### Post by indarkness on 2013-02-08
Hello !

I'm trying to cross-compile some C++ project for an arm-mv5sft-linux-gnueabi processor,I have set the ./configure in this way

    ```
./configure --build=i686-linux --host=arm-mv5sft-linux-gnueabi --target=arm-mv5sft-linux-gnueabi CC=~/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/arm-mv5sft-linux-gnueabi-gcc CXX=~/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/arm-mv5sft-linux-gnueabi-g++ LD=~/s/arm-mv5sft-linux-gnueabi/SW3.2p1/arm-mv5sft-linux-gnueabi/bin/arm-mv5sft-linux-gnueabi-ld LDFLAGS=-L/usr/include/libdaemon --with-sysroot=/home/thales/s/arm-mv5sft-linux-gnueabi/SW3.2p1/arm-mv5sft-linux-gnueabi --prefix=/justInstalled --disable-shared --enable-threads=posix --enable-long-long --enable-target-optspace --disable-nls --with-float=soft --disable-multilib --enable-symvers=gn
```The configuration succeeded, however when I do make I got an inclusion error 

    > libtool: link: warning: library `/home/j/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/../lib/gcc/arm-mv5sft-linux-gnueabi/4.3.2/../../../../arm-mv5sft-linux-gnueabi/lib/libstdc++.la' was moved.
      CXX    Main.o
    Main.cpp:28:30: error: libdaemon/daemon.h: No such file or directory
    Main.cpp: In function 'int __daemon_run()':
    Main.cpp:175: error: 'daemon_retval_send' was not declared in this scope
    .
    .
    .
    make[1]: Leaving directory `/home/j/ibrdtn-svn/daemon'
    make: *** [all-recursive] Error 1If I go to the file Main.cpp to see what is going on, it's complains of the include of libdeamon

    ```
...
    #include "config.h"
    #include "Configuration.h"
    #include <ibrcommon/Logger.h>
    #include <ibrcommon/data/File.h>
    
    #ifdef HAVE_LIBDAEMON
    #include <libdaemon/daemon.h> //line 28
    #endif
    
    #include <string.h>
    #include <csignal>
    #include <set>
    ...
```I've checked out that I have installed the libdeamon

    ```
@ubuntu:~$ pkg-config --libs libdaemon
    -ldaemon
    @ubuntu:~$locate libdaemon
    /usr/include/libdaemon
    /usr/include/libdaemon/daemon.h
    /usr/include/libdaemon/dexec.h
    /usr/include/libdaemon/dfork.h
    /usr/include/libdaemon/dlog.h
    /usr/include/libdaemon/dnonblock.h
    /usr/include/libdaemon/dpid.h
    /usr/include/libdaemon/dsignal.h
    /usr/lib/libdaemon.a
    /usr/lib/libdaemon.so
    /usr/lib/libdaemon.so.0
    /usr/lib/libdaemon.so.0.5.0
    /usr/lib/pkgconfig/libdaemon.pc
```Why the inclusion is wrong?? I've tried to include using 

    ```
./configure (as before) LDFLAGS=-llibdeamon (as before)
```But the configure tell me that there's an error, and I have to read the conf.log, which says 

    ```
/home/j/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/../lib/gcc/arm-mv5sft-linux-gnueabi/4.3.2/../../../../arm-mv5sft-linux-gnueabi/bin/ld: cannot find -llibdeamon
    collect2: ld returned 1 exit status
```Any idea would be very much appreciated!

Thanks in advance,

Regards

---

### Post by mevun on 2013-02-08
You need a cross-compiled library.  It seems unlikely that is what you have installed.

Depending on what is typically done for your cross-compile, your system may already have typical steps for installing the cross-compiled version.  My experience with OpenWRT and ucLinux is that they have ways to add libraries to the final build of a Linux system.

If this is just a stand-alone cross-compile, then you would download the source to libdaemon and cross-compile that first.  Then re-run configure for your project with the relevant defines for the cross-compiled version of libdaemon.  The biggest hassle will be if libdaemon itself has other dependencies, because those will also need to be cross-compiled.

Hope this makes sense.

---

### Post by indarkness on 2013-02-11
> **mevun said:**
> You need a cross-compiled library.  It seems unlikely that is what you have installed.

Depending on what is typically done for your cross-compile, your system may already have typical steps for installing the cross-compiled version.  My experience with OpenWRT and ucLinux is that they have ways to add libraries to the final build of a Linux system.

If this is just a stand-alone cross-compile, then you would download the source to libdaemon and cross-compile that first.  Then re-run configure for your project with the relevant defines for the cross-compiled version of libdaemon.  The biggest hassle will be if libdaemon itself has other dependencies, because those will also need to be cross-compiled.

Hope this makes sense.

Yes I understood what you meant, indeed I have tried to crosscompile the libdaemon library but I cannot achieve it,I've download the libdaemon source [http://0pointer.de/lennart/projects/libdaemon/libdaemon-0.14.tar.gz](http://0pointer.de/lennart/projects/libdaemon/libdaemon-0.14.tar.gz), after untar it I went to the directory where the code is in and executed  
```
./configure --build=i686-linux --host=arm-mv5sft-linux-gnueabi --target=arm-mv5sft-linux-gnueabi CC=~/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/arm-mv5sft-linux-gnueabi-gcc CXX=~/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/arm-mv5sft-linux-gnueabi-g++ LD=/home/t/s/arm-mv5sft-linux-gnueabi/SW3.2p1/arm-mv5sft-linux-gnueabi/bin/arm-mv5sft-linux-gnueabi-ld --prefix=/usr
``` and finally install the library by doing 

    ```
make install DESTDIR=/home/t/libdaemon-0.14
```However, when I relaunch the configure of the main project like this 

    ```
./configure --build=i686-linux --host=arm-mv5sft-linux-gnueabi --target=arm-mv5sft-linux-gnueabi CC=~/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/arm-mv5sft-linux-gnueabi-gcc CXX=~/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/arm-mv5sft-linux-gnueabi-g++ LD=/home/t/s/arm-mv5sft-linux-gnueabi/SW3.2p1/arm-mv5sft-linux-gnueabi/bin/arm-mv5sft-linux-gnueabi-ld CCPFLAGS=-I/home/t/libdaemon-0.14/usr/include LDFLAGS=-L/home/t/libdaemon-0.14/lib --with-sysroot=/home/t/s/arm-mv5sft-linux-gnueabi/SW3.2p1/arm-mv5sft-linux-gnueabi --prefix=/justInstalled --disable-shared --enable-threads=posix --enable-long-long --enable-target-optspace --disable-nls --with-float=soft --disable-multilib --enable-symvers=gnu
```I still get the same error at the beginning of this post... What am I doing wrong?

thanks in advance

---

### Post by mevun on 2013-02-12
Oops, I missed something in your first post.

Instead of [B]LDFLAGS=-llibdaemon
[/B]use [B]LDFLAGS=-ldaemon
[/B]
Normally, the linker knows that the library name starts with "lib" and ends with ".so".  And, of course, make sure you spell daemon correctly.

---

### Post by indarkness on 2013-02-12
> **mevun said:**
> Oops, I missed something in your first post.

Instead of [B]LDFLAGS=-llibdaemon
[/B]use [B]LDFLAGS=-ldaemon
[/B]
Normally, the linker knows that the library name starts with "lib" and ends with ".so".  And, of course, make sure you spell daemon correctly.

Thanks for replying,I've tried that but it doesn't work, the ,/configure of the main project complains about it.

I think I now the problem, libdeamon is not being cross-compiled for the arm, and I cannot understand why, after cross-compiling the library libdeamon I have checked that the library isn't crosscompiled for arm,it's still for the build a intel as it can be seen

```
    :~/libdaemon-0.14$ file -F usr/*/*.*
    usr/lib/libdaemon.lausr/lib/libdaemon.a       libtool library file, 
    usr/lib/libdaemon.sousr/lib/libdaemon.a       symbolic link to `libdaemon.so.0.5.0'
    usr/lib/libdaemon.so.0usr/lib/libdaemon.a     symbolic link to `libdaemon.so.0.5.0'
    usr/lib/libdaemon.so.0.5.0usr/lib/libdaemon.a ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, BuildID[sha1]=0xe4959941fb153e1dec5ec84f798dc32928219ae2, not stripped
```If I try to compile the main project with that "crosscompiled" library I get this

```
    libtool: link: warning: library `/home/j/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/../lib/gcc/arm-mv5sft-linux-gnueabi/4.3.2/../../../../arm-mv5sft-linux-gnueabi/lib/libstdc++.la' was moved.
    /home/j/libdaemon-0.14/usr/lib/libdaemon.so: could not read symbols: File in wrong format
    collect2: ld returned 1 exit status
    make[3]: *** [dtnd] Error 1
```So what can I do??

The configure for the libdaemon is this
```
~/libdaemon-0.14$ ./configure --build=i686-linux --host=arm-linux-gnueabi --enable-shared --prefix=/usr
~/libdaemon-0.14$ sudo make DESTDIR=/home/j/libdaemon-0.14 install
and when I

```

And when I call the configure of main project I do

./configure --build=i686-linux --host=arm-mv5sft-linux-gnueabi --target=arm-mv5sft-linux-gnueabi CC=~/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/arm-mv5sft-linux-gnueabi-gcc CXX=~/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/arm-mv5sft-linux-gnueabi-g++ LD=/home/thales/s/arm-mv5sft-linux-gnueabi/SW3.2p1/arm-mv5sft-linux-gnueabi/bin/arm-mv5sft-linux-gnueabi-ld CXXFLAGS="-I//home/j/libdaemon-0.14/usr/include" LDFLAGS="-L/home/j/libdaemon-0.14/usr/lib" --with-sysroot=/home/thales/s/arm-mv5sft-linux-gnueabi/SW3.2p1/arm-mv5sft-linux-gnueabi --prefix=/justInstalled --disable-shared --enable-threads=posix --enable-long-long --enable-target-optspace --disable-nls --with-float=soft --disable-multilib --enable-symvers=gnu

---

### Post by indarkness on 2013-02-12
> **mevun said:**
> Oops, I missed something in your first post.

Instead of [B]LDFLAGS=-llibdaemon
[/B]use [B]LDFLAGS=-ldaemon
[/B]
Normally, the linker knows that the library name starts with "lib" and ends with ".so".  And, of course, make sure you spell daemon correctly.

Thanks for replying,I've tried that but it doesn't work, the ,/configure of the main project complains about it.

I think I now the problem, libdeamon is not being cross-compiled for the arm, and I cannot understand why, after cross-compiling the library libdeamon I have checked that the library isn't crosscompiled for arm,it's still for the build a intel as it can be seen

```
    :~/libdaemon-0.14$ file -F usr/*/*.*
    usr/lib/libdaemon.lausr/lib/libdaemon.a       libtool library file, 
    usr/lib/libdaemon.sousr/lib/libdaemon.a       symbolic link to `libdaemon.so.0.5.0'
    usr/lib/libdaemon.so.0usr/lib/libdaemon.a     symbolic link to `libdaemon.so.0.5.0'
    usr/lib/libdaemon.so.0.5.0usr/lib/libdaemon.a ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, BuildID[sha1]=0xe4959941fb153e1dec5ec84f798dc32928219ae2, not stripped
```If I try to compile the main project with that "crosscompiled" library I get this

```
    libtool: link: warning: library `/home/j/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/../lib/gcc/arm-mv5sft-linux-gnueabi/4.3.2/../../../../arm-mv5sft-linux-gnueabi/lib/libstdc++.la' was moved.
    /home/j/libdaemon-0.14/usr/lib/libdaemon.so: could not read symbols: File in wrong format
    collect2: ld returned 1 exit status
    make[3]: *** [dtnd] Error 1
```So what can I do??

The configure for the libdaemon is this
```
~/libdaemon-0.14$ ./configure --build=i686-linux --host=arm-linux-gnueabi --enable-shared --prefix=/usr
~/libdaemon-0.14$ sudo make DESTDIR=/home/j/libdaemon-0.14 install
and when I

```And when I call the configure of main project I do

```
./configure --build=i686-linux --host=arm-mv5sft-linux-gnueabi --target=arm-mv5sft-linux-gnueabi CC=~/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/arm-mv5sft-linux-gnueabi-gcc CXX=~/s/arm-mv5sft-linux-gnueabi/SW3.2p1/bin/arm-mv5sft-linux-gnueabi-g++ LD=/home/j/s/arm-mv5sft-linux-gnueabi/SW3.2p1/arm-mv5sft-linux-gnueabi/bin/arm-mv5sft-linux-gnueabi-ld CXXFLAGS="-L/home/j/libdaemon-0.14/usr/include" LDFLAGS="-L/home/j/libdaemon-0.14/usr/lib" --with-sysroot=/home/j/s/arm-mv5sft-linux-gnueabi/SW3.2p1/arm-mv5sft-linux-gnueabi --prefix=/justInstalled --disable-shared --enable-threads=posix --enable-long-long --enable-target-optspace --disable-nls --with-float=soft --disable-multilib --enable-symvers=gnu

```

---

