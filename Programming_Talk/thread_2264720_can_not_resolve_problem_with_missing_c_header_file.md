---
title: "can not resolve problem with missing c header files"
date: 2015-02-09
forum: Programming Talk
---

### Post by shahin on 2015-02-09
This seems to be an old issue, and the fix is to install 32 bit C library, and gcc multilibrary. I have done everything suggested in different posts online, but I still have the issue. I run 64 bit 14.10 aka Utopic, and I am trying to use the arm toolchain. My goal is to verify that I can compile a simple program like hello.c and then move on to more elaborate ones that use the library. Here is the error message I get:
```
cd /home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin
sansari@ubuntu:~/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin$ !1996
./arm-linux-androideabi-gcc --verbose -o hello -c hello.c 
Using built-in specs.
COLLECT_GCC=./arm-linux-androideabi-gcc
Target: arm-linux-androideabi
Configured with: /s/ndk-toolchain/src/build/../gcc/gcc-4.9/configure --prefix=/tmp/ndk-andrewhsieh/build/toolchain/prefix --target=arm-linux-androideabi --host=x86_64-linux-gnu --build=x86_64-linux-gnu --with-gnu-as --with-gnu-ld --enable-languages=c,c++ --with-gmp=/tmp/ndk-andrewhsieh/build/toolchain/temp-install --with-mpfr=/tmp/ndk-andrewhsieh/build/toolchain/temp-install --with-mpc=/tmp/ndk-andrewhsieh/build/toolchain/temp-install --with-cloog=/tmp/ndk-andrewhsieh/build/toolchain/temp-install --with-isl=/tmp/ndk-andrewhsieh/build/toolchain/temp-install --with-ppl=/tmp/ndk-andrewhsieh/build/toolchain/temp-install --disable-ppl-version-check --disable-cloog-version-check --disable-isl-version-check --enable-cloog-backend=isl --with-host-libstdcxx='-static-libgcc -Wl,-Bstatic,-lstdc++,-Bdynamic -lm' --disable-libssp --enable-threads --disable-nls --disable-libmudflap --disable-libgomp --disable-libstdc__-v3 --disable-sjlj-exceptions --disable-shared --disable-tls --disable-libitm --with-float=soft --with-fpu=vfp --with-arch=armv5te --enable-target-optspace --enable-initfini-array --disable-nls --prefix=/tmp/ndk-andrewhsieh/build/toolchain/prefix --with-sysroot=/tmp/ndk-andrewhsieh/build/toolchain/prefix/sysroot --with-binutils-version=2.24 --with-mpfr-version=3.1.1 --with-mpc-version=1.0.1 --with-gmp-version=5.0.5 --with-gcc-version=4.9 --with-gdb-version=7.6 --with-python=/usr/local/google/home/andrewhsieh/mydroid/ndk/prebuilt/linux-x86_64/bin/python-config.sh --with-gxx-include-dir=/tmp/ndk-andrewhsieh/build/toolchain/prefix/include/c++/4.9 --with-bugurl=http://source.android.com/source/report-bugs.html --enable-languages=c,c++ --disable-bootstrap --enable-plugins --enable-libgomp --disable-libsanitizer --enable-gold --enable-graphite=yes --with-cloog-version=0.18.0 --with-isl-version=0.11.1 --enable-eh-frame-hdr-for-static --with-arch=armv5te --program-transform-name='s&^&arm-linux-androideabi-&' --enable-gold=default
Thread model: posix
gcc version 4.9 20140827 (prerelease) (GCC) 
COLLECT_GCC_OPTIONS='-v' '-o' 'hello' '-c' '-march=armv5te' '-mfloat-abi=soft' '-mfpu=vfp' '-mtls-dialect=gnu'
 /home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../libexec/gcc/arm-linux-androideabi/4.9/cc1 -quiet -v -iprefix /home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/arm-linux-androideabi/4.9/ hello.c -mbionic -fpic -quiet -dumpbase hello.c -march=armv5te -mfloat-abi=soft -mfpu=vfp -mtls-dialect=gnu -auxbase-strip hello -version -o /tmp/ccWTqx17.s
GNU C (GCC) version 4.9 20140827 (prerelease) (arm-linux-androideabi)
	compiled by GNU C version 4.6.x-google 20120106 (prerelease), GMP version 5.0.5, MPFR version 3.1.1, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring nonexistent directory "/home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/arm-linux-androideabi/4.9/../../../../arm-linux-androideabi/include"
ignoring duplicate directory "/home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/../../lib/gcc/arm-linux-androideabi/4.9/include"
ignoring nonexistent directory "/tmp/ndk-andrewhsieh/build/toolchain/prefix/sysroot/usr/local/include"
ignoring duplicate directory "/home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/../../lib/gcc/arm-linux-androideabi/4.9/include-fixed"
ignoring nonexistent directory "/home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/../../lib/gcc/arm-linux-androideabi/4.9/../../../../arm-linux-androideabi/include"
ignoring nonexistent directory "/tmp/ndk-andrewhsieh/build/toolchain/prefix/sysroot/usr/include"
#include "..." search starts here:
#include <...> search starts here:
 /home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/arm-linux-androideabi/4.9/include
 /home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/arm-linux-androideabi/4.9/include-fixed
End of search list.
GNU C (GCC) version 4.9 20140827 (prerelease) (arm-linux-androideabi)
	compiled by GNU C version 4.6.x-google 20120106 (prerelease), GMP version 5.0.5, MPFR version 3.1.1, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: d2d5f14f00a1381638660b109dec18f8
In file included from hello.c:3:0:
/usr/include/stdio.h:27:23: fatal error: features.h: No such file or directory
 # include <features.h>
                       ^
compilation terminated.

```

I have tried installing cd /home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin
sansari@ubuntu:~/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin$ !1996
./arm-linux-androideabi-gcc --verbose -o hello -c hello.c 
Using built-in specs.
COLLECT_GCC=./arm-linux-androideabi-gcc
Target: arm-linux-androideabi
Configured with: /s/ndk-toolchain/src/build/../gcc/gcc-4.9/configure --prefix=/tmp/ndk-andrewhsieh/build/toolchain/prefix --target=arm-linux-androideabi --host=x86_64-linux-gnu --build=x86_64-linux-gnu --with-gnu-as --with-gnu-ld --enable-languages=c,c++ --with-gmp=/tmp/ndk-andrewhsieh/build/toolchain/temp-install --with-mpfr=/tmp/ndk-andrewhsieh/build/toolchain/temp-install --with-mpc=/tmp/ndk-andrewhsieh/build/toolchain/temp-install --with-cloog=/tmp/ndk-andrewhsieh/build/toolchain/temp-install --with-isl=/tmp/ndk-andrewhsieh/build/toolchain/temp-install --with-ppl=/tmp/ndk-andrewhsieh/build/toolchain/temp-install --disable-ppl-version-check --disable-cloog-version-check --disable-isl-version-check --enable-cloog-backend=isl --with-host-libstdcxx='-static-libgcc -Wl,-Bstatic,-lstdc++,-Bdynamic -lm' --disable-libssp --enable-threads --disable-nls --disable-libmudflap --disable-libgomp --disable-libstdc__-v3 --disable-sjlj-exceptions --disable-shared --disable-tls --disable-libitm --with-float=soft --with-fpu=vfp --with-arch=armv5te --enable-target-optspace --enable-initfini-array --disable-nls --prefix=/tmp/ndk-andrewhsieh/build/toolchain/prefix --with-sysroot=/tmp/ndk-andrewhsieh/build/toolchain/prefix/sysroot --with-binutils-version=2.24 --with-mpfr-version=3.1.1 --with-mpc-version=1.0.1 --with-gmp-version=5.0.5 --with-gcc-version=4.9 --with-gdb-version=7.6 --with-python=/usr/local/google/home/andrewhsieh/mydroid/ndk/prebuilt/linux-x86_64/bin/python-config.sh --with-gxx-include-dir=/tmp/ndk-andrewhsieh/build/toolchain/prefix/include/c++/4.9 --with-bugurl=http://source.android.com/source/report-bugs.html --enable-languages=c,c++ --disable-bootstrap --enable-plugins --enable-libgomp --disable-libsanitizer --enable-gold --enable-graphite=yes --with-cloog-version=0.18.0 --with-isl-version=0.11.1 --enable-eh-frame-hdr-for-static --with-arch=armv5te --program-transform-name='s&^&arm-linux-androideabi-&' --enable-gold=default
Thread model: posix
gcc version 4.9 20140827 (prerelease) (GCC) 
COLLECT_GCC_OPTIONS='-v' '-o' 'hello' '-c' '-march=armv5te' '-mfloat-abi=soft' '-mfpu=vfp' '-mtls-dialect=gnu'
 /home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../libexec/gcc/arm-linux-androideabi/4.9/cc1 -quiet -v -iprefix /home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/arm-linux-androideabi/4.9/ hello.c -mbionic -fpic -quiet -dumpbase hello.c -march=armv5te -mfloat-abi=soft -mfpu=vfp -mtls-dialect=gnu -auxbase-strip hello -version -o /tmp/ccWTqx17.s
GNU C (GCC) version 4.9 20140827 (prerelease) (arm-linux-androideabi)
	compiled by GNU C version 4.6.x-google 20120106 (prerelease), GMP version 5.0.5, MPFR version 3.1.1, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring nonexistent directory "/home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/arm-linux-androideabi/4.9/../../../../arm-linux-androideabi/include"
ignoring duplicate directory "/home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/../../lib/gcc/arm-linux-androideabi/4.9/include"
ignoring nonexistent directory "/tmp/ndk-andrewhsieh/build/toolchain/prefix/sysroot/usr/local/include"
ignoring duplicate directory "/home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/../../lib/gcc/arm-linux-androideabi/4.9/include-fixed"
ignoring nonexistent directory "/home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/../../lib/gcc/arm-linux-androideabi/4.9/../../../../arm-linux-androideabi/include"
ignoring nonexistent directory "/tmp/ndk-andrewhsieh/build/toolchain/prefix/sysroot/usr/include"
#include "..." search starts here:
#include <...> search starts here:
 /home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/arm-linux-androideabi/4.9/include
 /home/sansari/ndk/android-ndk-r10d/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/../lib/gcc/arm-linux-androideabi/4.9/include-fixed
End of search list.
GNU C (GCC) version 4.9 20140827 (prerelease) (arm-linux-androideabi)
	compiled by GNU C version 4.6.x-google 20120106 (prerelease), GMP version 5.0.5, MPFR version 3.1.1, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: d2d5f14f00a1381638660b109dec18f8
In file included from hello.c:3:0:
/usr/include/stdio.h:27:23: fatal error: features.h: No such file or directory
 # include <features.h>
                       ^
compilation terminated.

I have tried installing libc6-dev-amd64, gcc-multilib, libc6-dev-i386. I have also tried re-installing some of them, and using aptitude.

---

### Post by TheFu on 2015-02-09
a) Are the header files you want on the box?
b) Did you include those directories in the compile options?  -I is the normal switch.

---

### Post by spjackson on 2015-02-10
> 
This seems to be an old issue, and the fix is to install 32 bit C library, and gcc multilibrary.

No, that is the wrong thing to do. The problems to which these are the solution are different from your own.
> 
I have tried installing libc6-dev-amd64, gcc-multilib, libc6-dev-i386. I have also tried re-installing some of them, and using aptitude. 

Ditto.

You are using the Android NDK. You need to use the headers and libraries that come with the NDK, not ones that may happen to exist elsewhere on your system. (Well, the headers *might* work, but there should be no expectation that they will. As sure as eggs are eggs, the libraries won't.)

> 
ignoring nonexistent directory "/tmp/ndk-andrewhsieh/build/toolchain/prefix/sysroot/usr/include"

This is a big clue. The toolchain can't find the headers where it expects to find them.

> 
/usr/include/stdio.h:27:23: fatal error: features.h: No such file or directory
 # include <features.h>

Precisely. If the toolchain is falling back to this default location, you know something's wrong.

Have you moved the NDK since installing it? However it has got in this state, I suggest you focus on reinstalling/configuring the NDK. Installing packages that are unrelated to the NDK is going to get you nowhere in all likelihood.

---

