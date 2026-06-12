---
title: "Launchpad invoking 64-bit programme in 32-bit build environment"
date: 2016-02-08
forum: Packaging and Compiling Programs
---

### Post by lads on 2016-02-08
I am trying to package a Qt programme for Trusty. I have successfully built the package in my system and uploaded it to a PPA. The *control* file includes the following:

   ```
 Build-Depends: debhelper (>= 8.0.0), cdbs, libpq-dev, libxml2-dev, clang, qt5-qmake, qt5-default, qttools5-dev-tools, qt5-image-formats-plugins
```

The Launchpad [log file]("https://launchpad.net/~luis-de-sousa/+archive/ubuntu/modelling/+build/8963272/+files/buildlog_ubuntu-trusty-i386.pgmodeler_0.8.2-beta-1ubuntu7_BUILDING.txt.gz") appears to show that *qt5-make* is in fact installed in the build system. However, the compilation is issuing this error:

```
    /usr/lib/x86_64-linux-gnu/qt5/bin/qmake -o Makefile pgmodeler.pro
    make[1]: /usr/lib/x86_64-linux-gnu/qt5/bin/qmake: Command not found
    make[1]: *** [Makefile] Error 127
    make[1]: Failed to remake makefile `Makefile'.
```

Why is the 64-bit version of *qmake* being invoked instead of the 32-bit?

Thank you.

---

