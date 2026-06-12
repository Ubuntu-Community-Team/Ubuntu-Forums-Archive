---
title: "dpkg-source: unrepresentable changes to source"
date: 2008-08-19
forum: Packaging and Compiling Programs
---

### Post by picpak on 2008-08-19
I'm in the middle of "debianizing" sakura. However, when I go to compile the deb with debuild, this is what I get:

```
kim@ubuntu:~/sakura-2.2.0/debian$ debuild
 dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package sakura
dpkg-buildpackage: source version 2.2.0-1ubuntu1~ppa1
dpkg-buildpackage: source changed by Kim <k_belding@hotmail.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
#-/usr/bin/make clean
#dh_clean 
 dpkg-source -b sakura-2.2.0
Use of uninitialized value in pattern match (m//) at /usr/bin/dpkg-source line 429.
dpkg-source: warning: Version number suggests Ubuntu changes, but Maintainer: does not have Ubuntu address
dpkg-source: warning: Version number suggests Ubuntu changes, but there is no XSBC-Original-Maintainer field
dpkg-source: building sakura using existing sakura_2.2.0.orig.tar.gz
dpkg-source: building sakura in sakura_2.2.0-1ubuntu1~ppa1.diff.gz
dpkg-source: cannot represent change to src/sakura: binary file contents changed
dpkg-source: warning: ignoring deletion of directory CMakeFiles
dpkg-source: warning: ignoring deletion of file CMakeFiles/progress.make
dpkg-source: warning: ignoring deletion of file CMakeFiles/CMakeDetermineCompilerABI_CXX.bin
dpkg-source: warning: ignoring deletion of file CMakeFiles/Makefile.cmake
dpkg-source: warning: ignoring deletion of file CMakeFiles/CMakeDirectoryInformation.cmake
dpkg-source: warning: ignoring deletion of directory CMakeFiles/CompilerIdCXX
dpkg-source: warning: ignoring deletion of file CMakeFiles/CompilerIdCXX/CMakeCXXCompilerId.cpp
dpkg-source: warning: ignoring deletion of file CMakeFiles/CompilerIdCXX/a.out
dpkg-source: warning: ignoring deletion of file CMakeFiles/CMakeCXXCompiler.cmake
dpkg-source: warning: ignoring deletion of directory CMakeFiles/sakura.dir
dpkg-source: warning: ignoring deletion of file CMakeFiles/sakura.dir/progress.make
dpkg-source: warning: ignoring deletion of file CMakeFiles/sakura.dir/build.make
dpkg-source: warning: ignoring deletion of file CMakeFiles/sakura.dir/cmake_clean.cmake
dpkg-source: warning: ignoring deletion of file CMakeFiles/sakura.dir/depend.make
dpkg-source: warning: ignoring deletion of directory CMakeFiles/sakura.dir/src
dpkg-source: warning: ignoring deletion of file CMakeFiles/sakura.dir/src/sakura.o
dpkg-source: warning: ignoring deletion of file CMakeFiles/sakura.dir/DependInfo.cmake
dpkg-source: warning: ignoring deletion of file CMakeFiles/sakura.dir/link.txt
dpkg-source: warning: ignoring deletion of file CMakeFiles/sakura.dir/C.includecache
dpkg-source: warning: ignoring deletion of file CMakeFiles/sakura.dir/depend.internal
dpkg-source: warning: ignoring deletion of file CMakeFiles/sakura.dir/flags.make
dpkg-source: warning: ignoring deletion of directory CMakeFiles/CMakeTmp
dpkg-source: warning: ignoring deletion of directory CMakeFiles/CMakeTmp/CMakeFiles
dpkg-source: warning: ignoring deletion of directory CMakeFiles/CMakeTmp/CMakeFiles/cmTryCompileExec.dir
dpkg-source: warning: ignoring deletion of file CMakeFiles/CMakeSystem.cmake
dpkg-source: warning: ignoring deletion of file CMakeFiles/Makefile2
dpkg-source: warning: ignoring deletion of directory CMakeFiles/CompilerIdC
dpkg-source: warning: ignoring deletion of file CMakeFiles/CompilerIdC/CMakeCCompilerId.c
dpkg-source: warning: ignoring deletion of file CMakeFiles/CompilerIdC/a.out
dpkg-source: warning: ignoring deletion of file CMakeFiles/cmake.check_cache
dpkg-source: warning: ignoring deletion of file CMakeFiles/CMakeOutput.log
dpkg-source: warning: ignoring deletion of directory CMakeFiles/distclean.dir
dpkg-source: warning: ignoring deletion of file CMakeFiles/distclean.dir/progress.make
dpkg-source: warning: ignoring deletion of file CMakeFiles/distclean.dir/build.make
dpkg-source: warning: ignoring deletion of file CMakeFiles/distclean.dir/cmake_clean.cmake
dpkg-source: warning: ignoring deletion of file CMakeFiles/distclean.dir/DependInfo.cmake
dpkg-source: warning: ignoring deletion of file CMakeFiles/CMakeCCompiler.cmake
dpkg-source: warning: ignoring deletion of file CMakeFiles/CMakeDetermineCompilerABI_C.bin
dpkg-source: warning: ignoring deletion of file cmake_install.cmake
dpkg-source: warning: ignoring deletion of file CMakeCache.txt
dpkg-source: warning: ignoring deletion of file Makefile
dpkg-source: warning: ignoring deletion of file po/cs.mo
dpkg-source: warning: ignoring deletion of file po/hu.mo
dpkg-source: warning: ignoring deletion of file po/ru.mo
dpkg-source: warning: ignoring deletion of file po/it.mo
dpkg-source: warning: ignoring deletion of directory po/CMakeFiles
dpkg-source: warning: ignoring deletion of file po/CMakeFiles/progress.make
dpkg-source: warning: ignoring deletion of directory po/CMakeFiles/translations.dir
dpkg-source: warning: ignoring deletion of file po/CMakeFiles/translations.dir/progress.make
dpkg-source: warning: ignoring deletion of file po/CMakeFiles/translations.dir/build.make
dpkg-source: warning: ignoring deletion of file po/CMakeFiles/translations.dir/cmake_clean.cmake
dpkg-source: warning: ignoring deletion of file po/CMakeFiles/translations.dir/depend.make
dpkg-source: warning: ignoring deletion of file po/CMakeFiles/translations.dir/DependInfo.cmake
dpkg-source: warning: ignoring deletion of file po/CMakeFiles/translations.dir/depend.internal
dpkg-source: warning: ignoring deletion of file po/CMakeFiles/CMakeDirectoryInformation.cmake
dpkg-source: warning: ignoring deletion of file po/de.mo
dpkg-source: warning: ignoring deletion of file po/es.mo
dpkg-source: warning: ignoring deletion of file po/pt_BR.mo
dpkg-source: warning: ignoring deletion of file po/zh_CN.mo
dpkg-source: warning: ignoring deletion of file po/cmake_install.cmake
dpkg-source: warning: ignoring deletion of file po/ja.mo
dpkg-source: warning: ignoring deletion of file po/fr.mo
dpkg-source: warning: ignoring deletion of file po/Makefile
dpkg-source: warning: ignoring deletion of file po/ca.mo
dpkg-source: warning: ignoring deletion of file po/sakura.pot
dpkg-source: unrepresentable changes to source
dpkg-source: building sakura in sakura_2.2.0-1ubuntu1~ppa1.dsc
dpkg-buildpackage: failure: dpkg-source -b sakura-2.2.0 gave error exit status 1
debuild: fatal error at line 1329:
dpkg-buildpackage -rfakeroot -D -us -uc failed
kim@ubuntu:~/sakura-2.2.0/debian$ 
```

This is my debian/rules:

```
#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1



configure: configure-stamp
configure-stamp:
	dh_testdir
	# Add here commands to configure the package.

	touch configure-stamp


build: build-stamp

build-stamp: configure-stamp 
	dh_testdir

	# Add here commands to compile the package.
	$(MAKE)
	#docbook-to-man debian/sakura.sgml > sakura.1
	touch $@

clean:
	dh_testdir
	dh_testroot
	rm -f build-stamp configure-stamp

	# Add here commands to clean up after the build process.
	-$(MAKE) clean

	dh_clean 

install: build
	dh_testdir
	dh_testroot
	dh_clean -k 
	dh_installdirs

	# Add here commands to install the package into debian/sakura.
	$(MAKE) DESTDIR=$(CURDIR)/debian/sakura install


# Build architecture-independent files here.
binary-indep: build install
# We have nothing to do by default.

# Build architecture-dependent files here.
binary-arch: build install
	dh_testdir
	dh_testroot
	dh_installchangelogs 
	dh_installdocs
	dh_installexamples
#	dh_install
#	dh_installmenu
#	dh_installdebconf	
#	dh_installlogrotate
#	dh_installemacsen
#	dh_installpam
#	dh_installmime
#	dh_python
#	dh_installinit
#	dh_installcron
#	dh_installinfo
	dh_installman
	dh_link
	dh_strip
	dh_compress
	dh_fixperms
#	dh_perl
#	dh_makeshlibs
	dh_installdeb
	dh_shlibdeps
	dh_gencontrol
	dh_md5sums
	dh_builddeb

binary: binary-indep binary-arch
.PHONY: build clean binary-indep binary-arch binary install configure
```

The error is probably in the "clean:" section. Do you know how to fix it?

---

