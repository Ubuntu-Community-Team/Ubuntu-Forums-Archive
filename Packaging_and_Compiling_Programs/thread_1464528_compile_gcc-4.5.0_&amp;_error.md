---
title: "compile gcc-4.5.0 &amp; error"
date: 2010-04-28
forum: Packaging and Compiling Programs
---

### Post by usef62 on 2010-04-28
HI
i have problem in ( make )

depbase=`echo prims.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`;\
        /bin/bash ./libtool --tag=CXX   --mode=compile /gcc-build/./gcc/xgcc -shared-libgcc -B/gcc-build/./gcc -nostdinc++ -L/gcc-build/i486-ubuntu-linux/64/libstdc++-v3/src -L/gcc-build/i486-ubuntu-linux/64/libstdc++-v3/src/.libs -B/usr/i486-ubuntu-linux/bin/ -B/usr/i486-ubuntu-linux/lib/ -isystem /usr/i486-ubuntu-linux/include -isystem /usr/i486-ubuntu-linux/sys-include  -m64 -DHAVE_CONFIG_H -I. -I../../../../gcc-4.5.0-20100311/libjava -I./include -I./gcj  -I../../../../gcc-4.5.0-20100311/libjava -Iinclude -I../../../../gcc-4.5.0-20100311/libjava/include -I../../../../gcc-4.5.0-20100311/libjava/classpath/include -Iclasspath/include -I../../../../gcc-4.5.0-20100311/libjava/classpath/native/fdlibm -I../../../../gcc-4.5.0-20100311/libjava/../boehm-gc/include -I../boehm-gc/include  -I../../../../gcc-4.5.0-20100311/libjava/libltdl -I../../../../gcc-4.5.0-20100311/libjava/libltdl -I../../../../gcc-4.5.0-20100311/libjava/.././libjava/../gcc -I../../../../gcc-4.5.0-20100311/libjava/../zlib -I../../../../gcc-4.5.0-20100311/libjava/../libffi/include -I../libffi/include  -fno-rtti -fnon-call-exceptions  -fdollars-in-identifiers -Wswitch-enum -D_FILE_OFFSET_BITS=64 -ffloat-store -fomit-frame-pointer -Usun -Wextra -Wall -D_GNU_SOURCE -DPREFIX="\"/usr\"" -DTOOLEXECLIBDIR="\"/usr/lib/gcc/i486-ubuntu-linux/4.5/64\"" -DJAVA_HOME="\"/usr\"" -DBOOT_CLASS_PATH="\"/usr/share/java/libgcj-4.5.jar\"" -DJAVA_EXT_DIRS="\"/usr/share/java/ext\"" -DGCJ_ENDORSED_DIRS="\"/usr/share/java/gcj-endorsed\"" -DGCJ_VERSIONED_LIBDIR="\"/usr/lib/../lib64/gcj-4.5-11\"" -DPATH_SEPARATOR="\":\"" -DECJ_JAR_FILE="\"\"" -DLIBGCJ_DEFAULT_DATABASE="\"/usr/lib/../lib64/gcj-4.5-11/classmap.db\"" -DLIBGCJ_DEFAULT_DATABASE_PATH_TAIL="\"gcj-4.5-11/classmap.db\"" -g -O2 -D_GNU_SOURCE  -m64 -MT prims.lo -MD -MP -MF $depbase.Tpo -c -o prims.lo ../../../../gcc-4.5.0-20100311/libjava/prims.cc &&\
        mv -f $depbase.Tpo $depbase.Plo
libtool: compile:  /gcc-build/./gcc/xgcc -shared-libgcc -B/gcc-build/./gcc -nostdinc++ -L/gcc-build/i486-ubuntu-linux/64/libstdc++-v3/src -L/gcc-build/i486-ubuntu-linux/64/libstdc++-v3/src/.libs -B/usr/i486-ubuntu-linux/bin/ -B/usr/i486-ubuntu-linux/lib/ -isystem /usr/i486-ubuntu-linux/include -isystem /usr/i486-ubuntu-linux/sys-include -m64 -DHAVE_CONFIG_H -I. -I../../../../gcc-4.5.0-20100311/libjava -I./include -I./gcj -I../../../../gcc-4.5.0-20100311/libjava -Iinclude -I../../../../gcc-4.5.0-20100311/libjava/include -I../../../../gcc-4.5.0-20100311/libjava/classpath/include -Iclasspath/include -I../../../../gcc-4.5.0-20100311/libjava/classpath/native/fdlibm -I../../../../gcc-4.5.0-20100311/libjava/../boehm-gc/include -I../boehm-gc/include -I../../../../gcc-4.5.0-20100311/libjava/libltdl -I../../../../gcc-4.5.0-20100311/libjava/libltdl -I../../../../gcc-4.5.0-20100311/libjava/.././libjava/../gcc -I../../../../gcc-4.5.0-20100311/libjava/../zlib -I../../../../gcc-4.5.0-20100311/libjava/../libffi/include -I../libffi/include -fno-rtti -fnon-call-exceptions -fdollars-in-identifiers -Wswitch-enum -D_FILE_OFFSET_BITS=64 -ffloat-store -fomit-frame-pointer -Usun -Wextra -Wall -D_GNU_SOURCE -DPREFIX=\"/usr\" -DTOOLEXECLIBDIR=\"/usr/lib/gcc/i486-ubuntu-linux/4.5/64\" -DJAVA_HOME=\"/usr\" -DBOOT_CLASS_PATH=\"/usr/share/java/libgcj-4.5.jar\" -DJAVA_EXT_DIRS=\"/usr/share/java/ext\" -DGCJ_ENDORSED_DIRS=\"/usr/share/java/gcj-endorsed\" -DGCJ_VERSIONED_LIBDIR=\"/usr/lib/../lib64/gcj-4.5-11\" -DPATH_SEPARATOR=\":\" -DECJ_JAR_FILE=\"\" -DLIBGCJ_DEFAULT_DATABASE=\"/usr/lib/../lib64/gcj-4.5-11/classmap.db\" -DLIBGCJ_DEFAULT_DATABASE_PATH_TAIL=\"gcj-4.5-11/classmap.db\" -g -O2 -D_GNU_SOURCE -m64 -MT prims.lo -MD -MP -MF .deps/prims.Tpo -c ../../../../gcc-4.5.0-20100311/libjava/prims.cc  -fPIC -DPIC -o .libs/prims.o
../../../../gcc-4.5.0-20100311/libjava/prims.cc: In function 'void _Jv_catch_fpe(int, siginfo_t*, void*)':
../../../../gcc-4.5.0-20100311/libjava/prims.cc:193:3: error: 'REG_EIP' was not declared in this scope
../../../../gcc-4.5.0-20100311/libjava/prims.cc:193:3: error: 'REG_EAX' was not declared in this scope
../../../../gcc-4.5.0-20100311/libjava/prims.cc:193:3: error: 'REG_EDX' was not declared in this scope
make[5]: *** [prims.lo] Error 1
make[5]: Leaving directory `/gcc-build/i486-ubuntu-linux/64/libjava'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/gcc-build/i486-ubuntu-linux/64/libjava'
make[3]: *** [multi-do] Error 1
make[3]: Leaving directory `/gcc-build/i486-ubuntu-linux/libjava'
make[2]: *** [all-multi] Error 2
make[2]: Leaving directory `/gcc-build/i486-ubuntu-linux/libjava'
make[1]: *** [all-target-libjava] Error 2
make[1]: Leaving directory `/gcc-build'
make: *** [all] Error 2

---

### Post by SevenMachines on 2010-04-29
it looks like you're using a recent snapshot of gcc, the 4.5 release is now done, do you get the same problems with the actual release version?
[ftp://ftp.mirrorservice.org/sites/sourceware.org/pub/gcc/releases/](ftp://ftp.mirrorservice.org/sites/sourceware.org/pub/gcc/releases/)

---

### Post by MadCow108 on 2010-04-29
it is also packaged here if that is an option:
[https://launchpad.net/~ubuntu-toolchain/+archive/test](https://launchpad.net/~ubuntu-toolchain/+archive/test)

---

