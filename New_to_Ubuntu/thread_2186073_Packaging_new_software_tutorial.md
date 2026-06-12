---
title: "Packaging new software tutorial"
date: 2013-11-05
forum: New to Ubuntu
---

### Post by morganfraughton on 2013-11-05
I am attempting to get through the "packaging new software" section ([http://developer.ubuntu.com/packaging/html/packaging-new-software.html](http://developer.ubuntu.com/packaging/html/packaging-new-software.html)) of ubuntu's packaging guide. I have hit a roadblock and am hoping that somebody can point me in the right direction. 

When I get to the point were it asks me to insert the code:

```
$ bzr builddeb -- -us -uc
```

I get this message in the terminal:

```

make[1]: Entering directory `/home/morgan/build-area/hello-2.9'
There seems to be no Makefile in this directory.
You must run ./configure before running 'make'.
make[1]: *** [abort-due-to-no-makefile] Error 1
make[1]: Leaving directory `/home/morgan/build-area/hello-2.9'
dh_auto_clean: make -j1 distclean returned exit code 2
make: *** [clean] Error 2
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
debuild: fatal error at line 1361:
dpkg-buildpackage -rfakeroot -D -us -uc failed
bzr: ERROR: The build failed.
morgan@morgans-laptop:~/hello/debian$ 

```

I am assuming that this means I am missing a makefile so it is not able to get past that. I just dont understand why I am missing a makefile or where to get it.

To get to this point I have followed the "GETTING SET UP" article ([http://developer.ubuntu.com/packaging/html/getting-set-up.html](http://developer.ubuntu.com/packaging/html/getting-set-up.html)) and the "PACKAGING NEW SOFTWARE" article ([http://developer.ubuntu.com/packaging/html/packaging-new-software.html](http://developer.ubuntu.com/packaging/html/packaging-new-software.html)) point by point.

---

### Post by sanderj on 2013-11-05
I've never built a package this way, but when I read the doc, you should be in hello/debian. Are you there? Show with pwd.

---

### Post by morganfraughton on 2013-11-05
Yes, I am in hello/debian *see the bottom of the following code. I dont know what its doing over in build-area/hello-2.9. Seemed kind of weird to me.

```
make[1]: Entering directory `/home/morgan/build-area/hello-2.9'
There seems to be no Makefile in this directory.
You must run ./configure before running 'make'.
make[1]: *** [abort-due-to-no-makefile] Error 1
make[1]: Leaving directory `/home/morgan/build-area/hello-2.9'
dh_auto_clean: make -j1 distclean returned exit code 2
make: *** [clean] Error 2
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
debuild: fatal error at line 1361:
dpkg-buildpackage -rfakeroot -D -us -uc failed
bzr: ERROR: The build failed.
morgan@morgans-laptop:~/hello/debian$ pwd
/home/morgan/hello/debian

```

---

