---
title: "How do I change permission for a file in debian/rules"
date: 2009-08-24
forum: Packaging and Compiling Programs
---

### Post by matthaeus123 on 2009-08-24
How do I change permission for a file in debian/rules so I do not run into this problem when compiling the program?
I am building this program in the ubuntu PPA jail.


```
test -z "/usr/lib/gimp/2.0/python" || /bin/mkdir -p "/build/buildd/gimp-2.7.2/debian/tmp//usr/lib/gimp/2.0/python"
 /usr/bin/install -c -m 644 /build/buildd/gimp-2.7.2/./plug-ins/pygimp/gimpenums.py /build/buildd/gimp-2.7.2/./plug-ins/pygimp/gimpfu.py /build/buildd/gimp-2.7.2/./plug-ins/pygimp/gimpplugin.py /build/buildd/gimp-2.7.2/./plug-ins/pygimp/gimpshelf.py /build/buildd/gimp-2.7.2/./plug-ins/pygimp/gimpui.py '/build/buildd/gimp-2.7.2/debian/tmp//usr/lib/gimp/2.0/python'
/bin/bash: line 18: /build/buildd/gimp-2.7.2/./py-compile: Permission denied
make[5]: *** [install-pygimpPYTHON] Error 126
make[5]: Leaving directory `/build/buildd/gimp-2.7.2/build/plug-ins/pygimp'
make[4]: *** [install-am] Error 2

```

The Debian/rules file for this build
```
#!/usr/bin/make -f
# PLEASE NOTE: when building a development version or a version where the minor
# library version changes or has changed but the major so version stays the 
# same, make sure to Build-Conflict on libgimpX.X, Where libgimpX.X contains
# a previous version of the same major version of the library. Otherwise,
# libtool will stupidly relink against the system version of the library
# when installing, and create a dependency on the old version of libgimp.
# TODO: maybe set LD_LIBRARY_PATH instead?

## WARNING: compiling without -O2 (DEB_BUILD_OPTIONS=noopt) may produce
## undesired effects, especially when scaling JPEG images

include /usr/share/cdbs/1/rules/debhelper.mk
include /usr/share/cdbs/1/class/autotools.mk
include /usr/share/cdbs/1/rules/simple-patchsys.mk


LDFLAGS = -Wl,--as-needed
DEB_CONFIGURE_EXTRA_FLAGS := --enable-python --enable-default-binary
DEB_BUILDDIR := $(DEB_SRCDIR)/build

DEB_DH_SHLIBDEPS_ARGS_ALL := -Llibgimp2.0 -l$(CURDIR)/debian/libgimp2.0/usr/lib
DEB_DH_SHLIBDEPS_ARGS_gimp := -Xlibcontroller-midi.so

clean::
	rm -rf build

common-install-impl::
	# Add translation domain to .desktop and .server files
	DOMAIN=$$(grep --max-count 1 '^GETTEXT_PACKAGE[[:space:]]*=' $(DEB_BUILDDIR)/po/Makefile | sed 's/^.*=[[:space:]]\([^[:space:]]\)/\1/'); \
	for d in $$(find debian/tmp -type f -name "*.desktop" ); do \
 		echo "Adding translation domain $$DOMAIN to $$d..."; \
 		echo "X-Ubuntu-Gettext-Domain=$$DOMAIN" >> $$d; \
	done;

	cd po; intltool-update -p
	cd po-libgimp; intltool-update -p
	cd po-plug-ins; intltool-update -p
	cd po-script-fu; intltool-update -p

	# Remove compiled python files from the distribution, they're compiled in
	# postrm by dh_python
	find $(CURDIR)/debian/tmp -name "*.py[co]" -exec rm '{}' ';'

	rm debian/tmp/usr/lib/*.la

	dh_movefiles
	dh_icons

binary-install/gimp::
	dh_pysupport -pgimp /usr/lib/gimp/2.0/python
```

---

