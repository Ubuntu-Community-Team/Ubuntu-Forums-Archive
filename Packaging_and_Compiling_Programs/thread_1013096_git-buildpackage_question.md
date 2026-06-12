---
title: "git-buildpackage question"
date: 2008-12-16
forum: Packaging and Compiling Programs
---

### Post by bfallik-litl on 2008-12-16
I'm using git-buildpackage (0.4.10) on Ubuntu Hardy.  I'm using "apt-get source" to download a source package, and then using git-import-dsc to import the dsc and associated orig.tar.gz and diff.gz files.  This seems to work correctly.  I then git-import-orig a new upstream tarball, which also succeeds.  However, when I try to build the package, the build (configure stage) fails due to missing PKG_CONFIG_PATH.

The package itself uses CDBS, and debian/rules sets up PKG_CONFIG_PATH manually, via DEB_CONFIGURE_SCRIPT_ENV.  When git-buildpackage invokes the build, it first launches configure (with PKG_CONFIG_PATH passed in) and then config.status a second time, without it.  If I set "AC_ARG_VAR(PKG_CONFIG_PATH)" in configure.ac, PKG_CONFIG_PATH *is* passed into config.status, however modifying the sources is not a permanent solution here.

When I used debuild or dpkg-buildpackage on the source package itself (without git-buildpackage at all), config.status is never invoked and the build succeeds.

What could be  different in the environment, filesystem, or steps between these two runs such that the build fails in git-buildpackage, but not in debuild?  I've tried passing --git-builder manually but that does not resolve the issue.

Thanks,
brian

---

### Post by dmitrijledkov on 2008-12-17
That's quite funky. What is the package you are building? I want to try it myself =D

---

