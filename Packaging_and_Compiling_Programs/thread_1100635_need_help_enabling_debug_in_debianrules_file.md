---
title: "need help enabling debug in debian/rules file"
date: 2009-03-19
forum: Packaging and Compiling Programs
---

### Post by Pollywoggy on 2009-03-19
I downloaded deb-src for kdepim-3.5.10 and I want to enable debugging in the kdepim-3.5.10/debian/rules file for kmail so that I can send debug output for kmail, but I am unable to find the place to put --enable-debug=yes  in this file.  There is usually an obvious configure section in the rules files but I do not see it here:

#! /usr/bin/make -f

# DEB_TAR_SRCDIR := $(shell basename $(wildcard *.tar.bz2) .tar.bz2)

# include /usr/share/cdbs/1/rules/tarball.mk
include /usr/share/cdbs/1/rules/debhelper.mk
include debian/cdbs/debian-qt-kde.mk
include /usr/share/cdbs/1/rules/simple-patchsys.mk
include /usr/share/cdbs/1/rules/utils.mk

DEB_KDE_APIDOX := yes

DEB_CONFIGURE_SCRIPT_ENV += KMIX=/usr/bin/kmix KTTSD=/usr/bin/kttsd

DEB_DH_INSTALL_SOURCEDIR := $(DEB_DESTDIR)

#override cdbs files, no --enable-final in kdepim
DEB_KDE_ENABLE_FINAL :=

DEB_INSTALL_DOCS_ALL :=

DEB_INSTALL_CHANGELOGS_ALL = $(shell for f in ChangeLog CHANGELOG CHANGES; do if test -s $(DEB_SRCDIR)/$(cdbs_curpkg)/$$f; then echo $(DEB_SRCDIR)/$(cdbs_curpkg)/$$f; break; fi; done)

shlibs_ver=4:3.5.7
DEB_DH_MAKESHLIBS_ARGS_libindex0 := -V'libindex0 (>= $(shlibs_ver))'
DEB_DH_MAKESHLIBS_ARGS_libkcal2b := -V'libkcal2b (>= $(shlibs_ver))'
DEB_DH_MAKESHLIBS_ARGS_libkdenetwork2 := -V'libkdenetwork2 (>= $(shlibs_ver))'
DEB_DH_MAKESHLIBS_ARGS_libkdepim1a := -V'libkdepim1a (>= $(shlibs_ver))'
DEB_DH_MAKESHLIBS_ARGS_libkgantt0 := -V'libkgantt0 (>= $(shlibs_ver))'
DEB_DH_MAKESHLIBS_ARGS_libkleopatra1 := -V'libkleopatra1 (>= $(shlibs_ver))'
DEB_DH_MAKESHLIBS_ARGS_libkmime2 := -V'libkmime2 (>= $(shlibs_ver))'
DEB_DH_MAKESHLIBS_ARGS_libkpimexchange1 := -V'libkpimexchange1 (>= $(shlibs_ver))'
DEB_DH_MAKESHLIBS_ARGS_libkpimidentities1 := -V'libkpimidentities1 (>= $(shlibs_ver))'
DEB_DH_MAKESHLIBS_ARGS_libksieve0 := -V'libksieve0 (>= $(shlibs_ver))'
DEB_DH_MAKESHLIBS_ARGS_libktnef1 := -V'libktnef1 (>= $(shlibs_ver))'
DEB_DH_MAKESHLIBS_ARGS_libmimelib1c2a := -V'libmimelib1c2a (>= $(shlibs_ver))'

PACKAGES_WITH_LIBS := akregator kaddressbook kalarm kdepim-kresources \
        kdepim-wizards kitchensync kleopatra kmail knode knotes kode kontact \
        korganizer kpilot ksync ktnef libindex0 libkcal2b libkdenetwork2 \
        libkdepim1a libkgantt0 libkleopatra1 libkmime2 libkpimexchange1 \
        libkpimidentities1 libksieve0 libktnef1 libmimelib1c2a

# kontact starts fine without korganizer or kpilot dependencies
# specialdates is only in recommends to get the kaddressbook dependency there
kontact_recommends_plugins := korganizer specialdates
kontact_suggests_plugins := journal kpilot todo

DEB_DH_SHLIBDEPS_ARGS_kontact := \
        $(foreach p,$(kontact_recommends_plugins) $(kontact_suggests_plugins),-Xusr/lib/kde3/libkontact_$(p)plugin.so) \
        -- -dRecommends \
        $(foreach p,$(kontact_recommends_plugins),debian/kontact/usr/lib/kde3/libkontact_$(p)plugin.so) \
        -dSuggests \
        $(foreach p,$(kontact_suggests_plugins),debian/kontact/usr/lib/kde3/libkontact_$(p)plugin.so) \
        -dDepends       # Since -u args go first in dpkg-shlibdeps call

# Move kaddressbook dependency (from libkabc_xmlrpc.so) to Recommends
DEB_DH_SHLIBDE       -Xusr/lib/kde3/kcal_kabc.so \
        -- -dRecommends \
        debian/libkcal2b/usr/lib/kde3/kcal_kabc.so \
        -dDepends

test-shlibdeps:
        @echo $(DEB_DH_SHLIBDEPS_ARGS_kontact)

KDE_UPSTREAM_VERSION := $(shell echo $(DEB_UPSTREAM_VERSION) | sed -e 's/\.dfsg.*//')
KDE_TARBALL := ../$(DEB_SOURCE_PACKAGE)-$(KDE_UPSTREAM_VERSION).tar.bz2
KDE_SOURCEDIR := dfsg-tmp/$(DEB_SOURCE_PACKAGE)-$(KDE_UPSTREAM_VERSION)
NEWDEB_SOURCEDIR := $(DEB_SOURCE_PACKAGE)-$(DEB_UPSTREAM_VERSION)
PS_ARGS_kdepim-kresources := \
        -Xusr/lib/libkabc_xmlrpc.so.1 \
        -- -dRecommends \
        debian/kdepim-kresources/usr/lib/libkabc_xmlrpc.so.1.* \
        -dDepends

# Move kaddressbook dependency of libkcal2b to Recommends
DEB_DH_SHLIBDEPS_ARGS_libkcal2b := \





thanks

---

### Post by andrewsomething on 2009-03-20
Might there alread be a precompiled package in the debug symbol archive:

[http://ddebs.ubuntu.com/pool/main/k/kdepim/](http://ddebs.ubuntu.com/pool/main/k/kdepim/)

Repo:
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) intrepid main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) intrepid-updates main restricted universe multiverse 
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) intrepid-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) intrepid-proposed main restricted universe multiverse

If that's not what you want try adding this:

DEB_CONFIGURE_EXTRA_FLAGS := --enable-debug=yes

---

### Post by Pollywoggy on 2009-03-22
> **andrewsomething said:**
> Might there alread be a precompiled package in the debug symbol archive:

[http://ddebs.ubuntu.com/pool/main/k/kdepim/](http://ddebs.ubuntu.com/pool/main/k/kdepim/)

Repo:
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) intrepid main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) intrepid-updates main restricted universe multiverse 
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) intrepid-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) intrepid-proposed main restricted universe multiverse

If that's not what you want try adding this:

DEB_CONFIGURE_EXTRA_FLAGS := --enable-debug=yes

I will try the extra flags line first.  I did not know about ddebs.  I will look into that too.

thanks

---

### Post by Pollywoggy on 2009-03-22
> **Pollywoggy said:**
> I will try the extra flags line first.  I did not know about ddebs.  I will look into that too.

thanks

This morning I found that the debs were sucessfully compiled but without debugging symbols.  If I cannot determine what went wrong (I will Google for a solution), I will need to go the ddeb route and I already have information on how to do that.

---

