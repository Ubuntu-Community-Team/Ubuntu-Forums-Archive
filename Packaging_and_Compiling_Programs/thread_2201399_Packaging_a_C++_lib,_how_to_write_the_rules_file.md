---
title: "Packaging a C++ lib, how to write the rules file ?"
date: 2014-01-24
forum: Packaging and Compiling Programs
---

### Post by VinsS on 2014-01-24
I have a lib written in C++ that I need to made a debian package.

It is just one .cpp file and his .h header file, I've made a build.sh for the compilation.

This is the rules file that I use for the packaging/
```

#!/usr/bin/make -f

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

override_dh_auto_configure:
override_dh_auto_build:
override_dh_auto_clean:
override_dh_auto_install:
override_dh_installchangelogs:
    dh_installchangelogs NEWS

build: 
build-arch:
build-indep:
build-stamp:
clean:
install:
# Build architecture-independent files here.
binary-indep:
# Build architecture-dependent files here.
binary-arch: build install
    set -e; \
    /bin/sh build.sh; \
    mkdir -p debian/tmp/usr/lib; \
    cp libcvengine.so debian/tmp/usr/lib;
binary:  binary-arch
.PHONY: build clean binary-indep binary-arch binary install

```

And the traceback:
```

 vincent@tiemoko:~/oqapy-2/cvengine-0.1.0$ LANG=C debuild -d -us -uc
 dpkg-buildpackage -rfakeroot -d -us -uc
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
dpkg-buildpackage: source package cvengine
dpkg-buildpackage: source version 0.1.0
dpkg-buildpackage: source changed by Vincent Vande Vyvre < ... >
 dpkg-source --before-build cvengine-0.1.0
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
make: Nothing to be done for `clean'.
 dpkg-source -b cvengine-0.1.0
dpkg-source: info: using source format `3.0 (quilt)'
dpkg-source: info: building cvengine using existing ./cvengine_0.1.0.orig.tar.gz
dpkg-source: info: building cvengine in cvengine_0.1.0.debian.tar.gz
dpkg-source: info: building cvengine in cvengine_0.1.0.dsc
 debian/rules build
make: Nothing to be done for `build'.
 fakeroot debian/rules binary
set -e; \
    /bin/sh build.sh; \
    mkdir -p debian/tmp/usr/lib; \
    cp libcvengine.so debian/tmp/usr/lib;
compiling cvengine.cpp
cvengine.cpp: In constructor 'CvEngine::CvEngine()':
cvengine.cpp:13:10: warning: unused variable 'isLoaded_' [-Wunused-variable]
cvengine.cpp:14:10: warning: unused variable 'isGreyLevels_' [-Wunused-variable]
create libcvengine.so
 dpkg-genchanges  >../cvengine_0.1.0_i386.changes
dpkg-genchanges: error: cannot read files list file: No such file or directory
dpkg-buildpackage: error: dpkg-genchanges gave error exit status 2
debuild: fatal error at line 1350:
dpkg-buildpackage -rfakeroot -d -us -uc failed

```

Seeing the [http://www.debian.org/doc/manuals/maint-guide/](http://www.debian.org/doc/manuals/maint-guide/) don't help me.

Any help will be apreciate.

---

### Post by VinsS on 2014-01-25
Solved,

My file rules was too complicated.
With this one, that works:
```

#!/usr/bin/make -f

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

%:
    dh $@

override_dh_auto_configure:
override_dh_auto_build:
    set -e; \
    /bin/sh build.sh;
override_dh_auto_clean:
override_dh_auto_install:
override_dh_installchangelogs:
    dh_installchangelogs NEWS

```

And now, the log is OK:
```

...
   dh_md5sums
   dh_builddeb
dpkg-deb: building package `libcvengine0' in `../libcvengine0_0.1.0_i386.deb'.
 dpkg-genchanges  >../libcvengine_0.1.0_i386.changes
dpkg-genchanges: including full source code in upload
 dpkg-source --after-build libcvengine-0.1.0
dpkg-buildpackage: full upload (original source is included)
Now running lintian...
W: libcvengine source: non-native-package-with-native-version
Finished running lintian.

```

---

