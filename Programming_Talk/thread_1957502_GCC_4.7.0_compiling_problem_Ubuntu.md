---
title: "GCC 4.7.0 compiling problem Ubuntu"
date: 2012-04-12
forum: Programming Talk
---

### Post by erotavlas on 2012-04-12
Hi,

I have tried to compile GCC 4.7.0 under Ubuntu 11.10 64 bit with the following configuration parameters:

configure -v --enable-languages=c,c++,fortran --prefix=/opt/gcc-4.7.0 --enable-shared --enable-linker-build-id --program-suffix=-4.7.0 --enable-threads=posix --disable-werror --with-cpu=native --with-arch=native --with-tune=native --enable-nls --without-included-gettext --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-checking=release --with-system-zlib --with-fpmath=avx --enable-lto --with-ppl --with-cloog

This is the output before the last error:
```

libtool: link: ranlib .libs/libstdc++convenience.a
libtool: link: rm -fr .libs/libstdc++convenience.lax
libtool: link: ( cd ".libs" && rm -f "libstdc++convenience.la" && ln -s "../libstdc++convenience.la" "libstdc++convenience.la" )
if test ! -d /home/username/Desktop/gcc-build/x86_64-unknown-linux-gnu/libstdc++-v3/src/debug; then \
      mkdir -p /home/username/Desktop/gcc-build/x86_64-unknown-linux-gnu/libstdc++-v3/src/debug; \
      for d in c++98 c++11; do mkdir -p  /home/username/Desktop/gcc-build/x86_64-unknown-linux-gnu/libstdc++-v3/src/debug/$d; done; \
      (cd /home/username/Desktop/gcc-build/x86_64-unknown-linux-gnu/libstdc++-v3/src/debug; \
      sed -e 's/top_builddir = \.\./top_builddir = ..\/../' \
          -e 's/top_build_prefix = \.\./top_build_prefix = ..\/../' \
          -e 's/srcdir = \.\./srcdir = ..\/../' \
          -e 's/VPATH = \.\./VPATH = ..\/../' \
          -e 's/glibcxx_basedir = \.\./glibcxx_basedir = ..\/../' \
          -e 's/MKDIR_P = \.\./MKDIR_P = ..\/../' \
      < ../Makefile > Makefile ; \
      for d in . c++98 c++11; do \
      sed -e 's/top_builddir = \.\./top_builddir = ..\/../' \
          -e 's/top_build_prefix = \.\./top_build_prefix = ..\/../' \
          -e 's/srcdir = \.\./srcdir = ..\/../' \
          -e 's/VPATH = \.\./VPATH = ..\/../' \
          -e 's/glibcxx_basedir = \.\./glibcxx_basedir = ..\/../' \
          -e 's/MKDIR_P = \.\./MKDIR_P = ..\/../' \
      < ../$d/Makefile > $d/Makefile ; \
      done) ; \
    fi; \
    echo `date` > stamp-debug;
(cd /home/username/Desktop/gcc-build/x86_64-unknown-linux-gnu/libstdc++-v3/src/debug; \
      mv Makefile Makefile.tmp; \
      sed -e 's,all-local: all-once,all-local:,' \
          -e 's,install-data-local: install-data-once,install-data-local:,' \
          -e 's,src/c,src/debug/c,' \
      < Makefile.tmp > Makefile ; \
      make CXXFLAGS='-gdwarf-4 -g3 -O0' \
      toolexeclibdir=/opt/gcc-4.7.0/lib/../lib64/debug all) ;
mv: cannot stat `Makefile': No such file or directory
/bin/bash: line 2: Makefile.tmp: No such file or directory
make[7]: Entering directory `/home/username/Desktop/gcc-build/x86_64-unknown-linux-gnu/libstdc++-v3/src/debug'
make[7]: *** No rule to make target `all'.  Stop.
make[7]: Leaving directory `/home/username/Desktop/gcc-build/x86_64-unknown-linux-gnu/libstdc++-v3/src/debug'
make[6]: *** [build-debug] Error 2
make[6]: Leaving directory `/home/username/Desktop/gcc-build/x86_64-unknown-linux-gnu/libstdc++-v3/src'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/username/Desktop/gcc-build/x86_64-unknown-linux-gnu/libstdc++-v3/src'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/username/Desktop/gcc-build/x86_64-unknown-linux-gnu/libstdc++-v3'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/username/Desktop/gcc-build/x86_64-unknown-linux-gnu/libstdc++-v3'
make[2]: *** [all-stagefeedback-target-libstdc++-v3] Error 2
make[2]: Leaving directory `/home/username/Desktop/gcc-build'
make[1]: *** [stagefeedback-bubble] Error 2
make[1]: Leaving directory `/home/username/Desktop/gcc-build'
make: *** [profiledbootstrap] Error 2

```I have tried to compile GCC 4.6.3 with the same configuration parameters and it works. So there should be some change in GCC 4.7.0.

I have already asked on GCC help mailing list [http://gcc.gnu.org/ml/gcc-help/2012-04/msg00099.html](http://gcc.gnu.org/ml/gcc-help/2012-04/msg00099.html). They say that it is a problem of Ubuntu. It probably has changed the library libc. If I remove the option --enable-libstdcxx-debug, I can compile with success also with GCC 4.7.0. Can you help me?

Thank you

---

### Post by kc1di on 2012-04-12
See the following similar thread , no fix yet but some things you may want to look at.  gcc 4.7 has a PPA for 12.04 and can be install from there. But won't work in 11.10. 

[http://ubuntuforums.org/showthread.php?t=1957189]("http://ubuntuforums.org/showthread.php?t=1957189")

---

### Post by erotavlas on 2012-04-13
Hi,

thank you very much for your answer. I can install the GCC from package but I can't configure it to use custom plug-in and custom features.
The problem is the following: with Ubuntu 11.10 64 bit I can compile well the GCC 4.6.3 but not the GCC 4.7.0. If I remove the --enable-libstdcxx-debug option I can compile also the latest version.
The problem is related to Ubuntu and how it manages the libc libc6-dbg_*.deb. 
Any help is welcome.

Thank you

---

