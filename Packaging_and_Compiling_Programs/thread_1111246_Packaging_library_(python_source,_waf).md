---
title: "Packaging library (python source, waf)"
date: 2009-03-30
forum: Packaging and Compiling Programs
---

### Post by mira.mikes on 2009-03-30
Hello,

I am trying build package of library written in Python using waf.
My build process ending with this error:

#########

distclean finished successfully
rm -f config.sub config.guess autowaf.pyc
dh_clean
dpkg-source -b slv2-0.6.2
dpkg-source: info: using source format `1.0'
dpkg-source: info: building slv2 using existing slv2_0.6.2.orig.tar.gz
dpkg-source: info: building slv2 in slv2_0.6.2-1.diff.gz
dpkg-source: info: building slv2 in slv2_0.6.2-1.dsc
debian/rules build
make: *** No rule to make target `configure', needed by `config.status'. Stop.
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
pbuilder: Failed autobuilding of package

#########

My debian/rules file looks like this:

#########

#!/usr/bin/make -f
# -*- makefile -*-

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

WAF = ./waf


# These are used for cross-compiling and for saving the configure script
# from having to guess our platform (since we know it already)
DEB_HOST_GNU_TYPE ?= $(shell dpkg-architecture -qDEB_HOST_GNU_TYPE)
DEB_BUILD_GNU_TYPE ?= $(shell dpkg-architecture -qDEB_BUILD_GNU_TYPE)


# shared library versions, option 1
#version=2.0.5
#major=2
# option 2, assuming the library is created as src/.libs/libfoo.so.2.0.5 or so
version=`ls src/.libs/lib*.so.* | \
awk '{if (match($$0,/[0-9]+\.[0-9]+\.[0-9]+$$/)) print substr($$0,RSTART)}'`
major=`ls src/.libs/lib*.so.* | \
awk '{if (match($$0,/\.so\.[0-9]+$$/)) print substr($$0,RSTART+4)}'`

config.status: configure
dh_testdir
# Add here commands to configure the package.
ifneq "$(wildcard /usr/share/misc/config.sub)" ""
cp -f /usr/share/misc/config.sub config.sub
endif
ifneq "$(wildcard /usr/share/misc/config.guess)" ""
cp -f /usr/share/misc/config.guess config.guess
endif
$(WAF) configure --host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE) --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info CFLAGS="$(CFLAGS)" LDFLAGS="-Wl,-z,defs"


build: build-stamp
build-stamp: config.status
dh_testdir

# Add here commands to compile the package.
$(WAF) configure --prefix=/usr
$(WAF)

touch $@

clean:
dh_testdir
dh_testroot
rm -f build-stamp

# Add here commands to clean up after the build process.
$(WAF) distclean
rm -f config.sub config.guess autowaf.pyc

dh_clean

install: build
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs

$(WAF) DESTDIR=$(CURDIR)/debian/slv2-9 install-exec
$(WAF) DESTDIR=$(CURDIR)/debian/slv2-9-dev install-data
$(WAF) DESTDIR=$(CURDIR)/debian/slv2-doc install-man


# Build architecture-independent files here.
binary-indep: build install
dh_installman

# Build architecture-dependent files here.
binary-arch: build install
dh_testdir
dh_testroot
dh_installchangelogs
dh_installdocs
dh_installexamples
# dh_install
# dh_installdebconf
# dh_installlogrotate
# dh_installpam
# dh_installmime
# dh_installman
dh_link
dh_strip
dh_compress
dh_fixperms
# dh_perl
# dh_python
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dh_md5sums
dh_builddeb

binary: binary-indep binary-arch
.PHONY: build clean binary-indep binary-arch binary install

########

Please can somebody advise me where can be problem?

Thanks for help

mira

---

