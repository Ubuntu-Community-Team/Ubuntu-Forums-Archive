---
title: "[Solved] Problem with dh_python2 --compile-all"
date: 2013-04-24
forum: Packaging and Compiling Programs
---

### Post by VinsS on 2013-04-24
Hi,

I'm creating a .deb package for my application Qarte.

Following the last recommandations, I use dh_python2 in the rules file

rules
--------------------------------
```

#!/usr/bin/make -f
# -*- makefile -*-

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

CFLAGS = -Wall -g

ifneq (,$(findstring noopt,$(DEB_BUILD_OPTIONS)))
    CFLAGS += -O0
else
    CFLAGS += -O2
endif

%:
    dh $@ --with python2

(snip)

    dh_python2 --compile-all

(snip)

```
-----------------------------

The package is builded with  'debuild -i -us -uc'
and is finnished with theses Lintian warnings:
--------------------------------------------------------
Now running lintian...
W: qarte source: non-native-package-with-native-version
W: qarte source: binary-arch-rules-but-pkg-is-arch-indep
W: qarte: duplicate-changelog-files usr/share/doc/qarte/changelog.Debian.gz usr/share/doc/qarte/changelog.gz
Finished running lintian.
-------------------------------------------------------
wich are nothing to do with my problem.

Now, when I try to install the package, I've this return:
-------------------------------------------------------
```

vincent@tiemoko:~/Releases/Qarte/1.7$ sudo dpkg -i qarte_1.7_all.deb 
[sudo] password for vincent: 
Sélection du paquet qarte précédemment désélectionné.
(Lecture de la base de données... 209078 fichiers et répertoires déjà installés.)
Dépaquetage de qarte (à partir de qarte_1.7_all.deb) ...
Paramétrage de qarte (1.7) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 290, in <module>
    main()
  File "/usr/bin/pycompile", line 263, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 155, in compile
    for fn, versions_to_compile in filter_files(files, e_patterns, versions):
  File "/usr/bin/pycompile", line 110, in filter_files
    for fn in files:
  File "/usr/share/python/debpython/files.py", line 77, in filter_out_ext
    for fn in files:
  File "/usr/share/python/debpython/namespace.py", line 74, in add_namespace_files
    namespaces = load(package)
  File "/usr/share/python/debpython/tools.py", line 152, in __call__
    self.cache[key] = self.func(*args, **kwargs)
  File "/usr/share/python/debpython/namespace.py", line 65, in load
    result = set(i.replace('.', '/') for i in parse(fpaths))
  File "/usr/share/python/debpython/namespace.py", line 38, in parse
    with open(fpath, 'r') as fp:
IOError: [Errno 21] Is a directory: '/usr/share/qarte'
dpkg : erreur de traitement de qarte (--install) :
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 1
Traitement des actions différées (« triggers ») pour « man-db »...
Traitement des actions différées (« triggers ») pour « bamfdaemon »...
Rebuilding /usr/share/applications/bamf.index...
Traitement des actions différées (« triggers ») pour « desktop-file-utils »...
Traitement des actions différées (« triggers ») pour « gnome-menus »...
Des erreurs ont été rencontrées pendant l'exécution :
 qarte

```
-----------------------------------------------------


Ubuntu 12.04 precise
Python 2.7.3
dpkg 1.16.1.2ubuntu7.1

Other infos:

file control
------------------------------------------------------
```

Source: qarte
Section: video
Priority: optional
Maintainer: Vincent Vande Vyvre <vincent.vandevyvre@swing.be>
Build-Depends: debhelper (>= 7), python-all (>= 2.6.6)
Standards-Version: 3.9.3
Homepage: https://launchpad.net/qarte

Package: qarte
Version: 1.7
Architecture: all
Section: video
Priority: optional
Depends: ${misc:Depends}, python , python-qt4 , rtmpdump 
Description: Arte TV Browser
 Qarte allows you to browse into the archives of arte+7 and arteLiveWeb sites
 and to record your preferred videos.

```
-----------------------------------------------------

file postinst
-----------------------------------------------------
```

#!/bin/sh
set -e

# Automatically added by dh_python2:
if which pycompile >/dev/null 2>&1; then
    pycompile -p  /usr/share/qarte -V 2.4-
fi

# End automatically added section

```
-----------------------------------------------------

Thank's for all advices.

Vincent

---

### Post by schragge on 2013-04-24
What's the purpose of both specifying the addon *--with python2* _and_ calling *dh_python2* in one of the targets? Just
```

%:
        dh $@ --with python2

```
should be enough unless your package has some special requirements. In the latter case, please post your *debian/rules* in the full length.

---

### Post by VinsS on 2013-04-24
Because --with python2 is not enough to create the postinst, sure, I've tested, I must add dh_python2 --compile-all for that.

The rules files:
```

#!/usr/bin/make -f
# -*- makefile -*-

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

CFLAGS = -Wall -g

ifneq (,$(findstring noopt,$(DEB_BUILD_OPTIONS)))
    CFLAGS += -O0
else
    CFLAGS += -O2
endif

%:
    dh $@ --with python2

configure: configure-stamp
configure-stamp:
    dh_testdir
    # Add here commands to configure the package.

    touch configure-stamp

build: build-stamp

build-stamp: configure-stamp
    dh_testdir
    touch build-stamp

clean:
    dh_testdir
    dh_testroot
    rm -f build-stamp configure-stamp
    dh_clean

install: build
    dh_testdir
    dh_testroot
    #dh_clean -k
    dh_installdirs

    #==========================================

    #$(MAKE) DESTDIR="$(CURDIR)/debian/qarte" install
    mkdir -p "$(CURDIR)/debian/qarte"
    mkdir -p "$(CURDIR)/debian/qarte/usr"
    mkdir -p "$(CURDIR)/debian/qarte/usr/bin"
    cp -a "$(CURDIR)/qarte" "$(CURDIR)/debian/qarte/usr/bin/qarte"
    cp -a "$(CURDIR)/qarte" "$(CURDIR)/debian/qarte/usr/bin/qarte"
    mkdir -p "$(CURDIR)/debian/qarte/usr/share/applications"
    cp -a "$(CURDIR)/q_arte.desktop" "$(CURDIR)/debian/qarte/usr/share/applications/q_arte.desktop"
    cp -a "$(CURDIR)/q_arte.desktop" "$(CURDIR)/debian/qarte/usr/share/applications/q_arte.desktop"
    mkdir -p "$(CURDIR)/debian/qarte/usr/share/doc/qarte"
    cp -a "$(CURDIR)/README" "$(CURDIR)/debian/qarte/usr/share/doc/qarte/README"
    mkdir -p "$(CURDIR)/debian/qarte/usr/share/locale/de/LC_MESSAGES"
    cp -a "$(CURDIR)/locale/de/LC_MESSAGES/qarte.mo" "$(CURDIR)/debian/qarte/usr/share/locale/de/LC_MESSAGES/qarte.mo"
    cp -a "$(CURDIR)/locale/de/LC_MESSAGES/qarte.mo" "$(CURDIR)/debian/qarte/usr/share/locale/de/LC_MESSAGES/qarte.mo"
    mkdir -p "$(CURDIR)/debian/qarte/usr/share/locale/fr/LC_MESSAGES"
    cp -a "$(CURDIR)/locale/fr/LC_MESSAGES/qarte.mo" "$(CURDIR)/debian/qarte/usr/share/locale/fr/LC_MESSAGES/qarte.mo"
    cp -a "$(CURDIR)/locale/fr/LC_MESSAGES/qarte.mo" "$(CURDIR)/debian/qarte/usr/share/locale/fr/LC_MESSAGES/qarte.mo"
    mkdir -p "$(CURDIR)/debian/qarte/usr/share/pixmaps"
    cp -a "$(CURDIR)/qarte.png" "$(CURDIR)/debian/qarte/usr/share/pixmaps/qarte.png"
    cp -a "$(CURDIR)/qarte.png" "$(CURDIR)/debian/qarte/usr/share/pixmaps/qarte.png"
    mkdir -p "$(CURDIR)/debian/qarte/usr/share/qarte"
    mkdir -p "$(CURDIR)/debian/qarte/usr/share/qarte/VWidgets"
    cp -a "$(CURDIR)/VWidgets/vlineedit.py" "$(CURDIR)/debian/qarte/usr/share/qarte/VWidgets/vlineedit.py"
    cp -a "$(CURDIR)/VWidgets/__init__.py" "$(CURDIR)/debian/qarte/usr/share/qarte/VWidgets/__init__.py"
    mkdir -p "$(CURDIR)/debian/qarte/usr/share/qarte/commonwidgets"
    cp -a "$(CURDIR)/commonwidgets/horizontalslider.py" "$(CURDIR)/debian/qarte/usr/share/qarte/commonwidgets/horizontalslider.py"
    cp -a "$(CURDIR)/commonwidgets/__init__.py" "$(CURDIR)/debian/qarte/usr/share/qarte/commonwidgets/__init__.py"
    mkdir -p "$(CURDIR)/debian/qarte/usr/share/qarte/crontab"
    cp -a "$(CURDIR)/crontab/crontab.py" "$(CURDIR)/debian/qarte/usr/share/qarte/crontab/crontab.py"
    cp -a "$(CURDIR)/crontab/ChangeLog" "$(CURDIR)/debian/qarte/usr/share/qarte/crontab/ChangeLog"
    cp -a "$(CURDIR)/crontab/AUTHORS" "$(CURDIR)/debian/qarte/usr/share/qarte/crontab/AUTHORS"
    cp -a "$(CURDIR)/crontab/__init__.py" "$(CURDIR)/debian/qarte/usr/share/qarte/crontab/__init__.py"
    mkdir -p "$(CURDIR)/debian/qarte/usr/share/qarte/medias"
    cp -a "$(CURDIR)/medias/box_unchecked.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/box_unchecked.png"
    cp -a "$(CURDIR)/medias/download_sett_26x28.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/download_sett_26x28.png"
    cp -a "$(CURDIR)/medias/blogo_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/blogo_off.png"
    cp -a "$(CURDIR)/medias/select-all.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/select-all.png"
    cp -a "$(CURDIR)/medias/edit.svg" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/edit.svg"
    cp -a "$(CURDIR)/medias/jazz_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/jazz_on.png"
    cp -a "$(CURDIR)/medias/blogo_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/blogo_on.png"
    cp -a "$(CURDIR)/medias/next_44x30.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/next_44x30.png"
    cp -a "$(CURDIR)/medias/process-stop.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/process-stop.png"
    cp -a "$(CURDIR)/medias/cdm_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/cdm_off.png"
    cp -a "$(CURDIR)/medias/alw_logo.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/alw_logo.png"
    cp -a "$(CURDIR)/medias/previous_44x30.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/previous_44x30.png"
    cp -a "$(CURDIR)/medias/picker.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/picker.png"
    cp -a "$(CURDIR)/medias/scroll_spindown.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/scroll_spindown.png"
    cp -a "$(CURDIR)/medias/download_44x30.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/download_44x30.png"
    cp -a "$(CURDIR)/medias/arrow.svg" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/arrow.svg"
    cp -a "$(CURDIR)/medias/save.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/save.png"
    cp -a "$(CURDIR)/medias/theater_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/theater_off.png"
    cp -a "$(CURDIR)/medias/news_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/news_on.png"
    cp -a "$(CURDIR)/medias/theater_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/theater_on.png"
    cp -a "$(CURDIR)/medias/cdm_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/cdm_on.png"
    cp -a "$(CURDIR)/medias/oprf_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/oprf_off.png"
    cp -a "$(CURDIR)/medias/noPreview.svg" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/noPreview.svg"
    cp -a "$(CURDIR)/medias/introd_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/introd_off.png"
    cp -a "$(CURDIR)/medias/magnifier_20x20.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/magnifier_20x20.png"
    cp -a "$(CURDIR)/medias/world.svg" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/world.svg"
    cp -a "$(CURDIR)/medias/odp_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/odp_off.png"
    cp -a "$(CURDIR)/medias/arte.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/arte.png"
    cp -a "$(CURDIR)/medias/scroll_spinup.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/scroll_spinup.png"
    cp -a "$(CURDIR)/medias/news_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/news_off.png"
    cp -a "$(CURDIR)/medias/magnifier.svg" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/magnifier.svg"
    cp -a "$(CURDIR)/medias/spinup.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/spinup.png"
    cp -a "$(CURDIR)/medias/stop_44x30.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/stop_44x30.png"
    cp -a "$(CURDIR)/medias/noPreview.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/noPreview.png"
    cp -a "$(CURDIR)/medias/combo_spin.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/combo_spin.png"
    cp -a "$(CURDIR)/medias/introd_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/introd_on.png"
    cp -a "$(CURDIR)/medias/oprf_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/oprf_on.png"
    cp -a "$(CURDIR)/medias/down_26x28.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/down_26x28.png"
    cp -a "$(CURDIR)/medias/rdr_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/rdr_on.png"
    cp -a "$(CURDIR)/medias/minus_white_20x5.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/minus_white_20x5.png"
    cp -a "$(CURDIR)/medias/mondomix_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/mondomix_on.png"
    cp -a "$(CURDIR)/medias/refresh.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/refresh.png"
    cp -a "$(CURDIR)/medias/plus_white_20x20.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/plus_white_20x20.png"
    cp -a "$(CURDIR)/medias/clipboard.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/clipboard.png"
    cp -a "$(CURDIR)/medias/lounge_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/lounge_on.png"
    cp -a "$(CURDIR)/medias/world_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/world_off.png"
    cp -a "$(CURDIR)/medias/refresh.svg" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/refresh.svg"
    cp -a "$(CURDIR)/medias/world_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/world_on.png"
    cp -a "$(CURDIR)/medias/eraser.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/eraser.png"
    cp -a "$(CURDIR)/medias/close.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/close.png"
    cp -a "$(CURDIR)/medias/box_checked.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/box_checked.png"
    cp -a "$(CURDIR)/medias/lounge_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/lounge_off.png"
    cp -a "$(CURDIR)/medias/clean.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/clean.png"
    cp -a "$(CURDIR)/medias/spindown.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/spindown.png"
    cp -a "$(CURDIR)/medias/box_unchecked_hover.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/box_unchecked_hover.png"
    cp -a "$(CURDIR)/medias/add_44x30.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/add_44x30.png"
    cp -a "$(CURDIR)/medias/noPreview_2.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/noPreview_2.png"
    cp -a "$(CURDIR)/medias/classic_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/classic_on.png"
    cp -a "$(CURDIR)/medias/apply.svg" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/apply.svg"
    cp -a "$(CURDIR)/medias/tracks_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/tracks_on.png"
    cp -a "$(CURDIR)/medias/rdr_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/rdr_off.png"
    cp -a "$(CURDIR)/medias/mondomix_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/mondomix_off.png"
    cp -a "$(CURDIR)/medias/rock_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/rock_on.png"
    cp -a "$(CURDIR)/medias/logoLW_213x36.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/logoLW_213x36.png"
    cp -a "$(CURDIR)/medias/classic_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/classic_off.png"
    cp -a "$(CURDIR)/medias/news_on_70x29_extract.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/news_on_70x29_extract.png"
    cp -a "$(CURDIR)/medias/logo+7_112x48.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/logo+7_112x48.png"
    cp -a "$(CURDIR)/medias/odp_on.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/odp_on.png"
    cp -a "$(CURDIR)/medias/remove_26x28.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/remove_26x28.png"
    cp -a "$(CURDIR)/medias/box_checked_hover.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/box_checked_hover.png"
    cp -a "$(CURDIR)/medias/up_26x28.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/up_26x28.png"
    cp -a "$(CURDIR)/medias/tracks_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/tracks_off.png"
    cp -a "$(CURDIR)/medias/jazz_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/jazz_off.png"
    cp -a "$(CURDIR)/medias/rock_off.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/rock_off.png"
    cp -a "$(CURDIR)/medias/shadow.png" "$(CURDIR)/debian/qarte/usr/share/qarte/medias/shadow.png"

    #==========================================

# Build architecture-independent files here.
binary-indep: build install
# We have nothing to do by default.

# Build architecture-dependent files here.
binary-arch: build install
    dh_testdir
    dh_testroot
    dh_installchangelogs debian/changelog
    dh_installdocs
    dh_installexamples
#    dh_install
#    dh_installmenu
#    dh_installdebconf
#    dh_installlogrotate
#    dh_installemacsen
#    dh_installpam
#    dh_installmime
    dh_python2 --compile-all
#    dh_installinit
#    dh_installcron
#    dh_installinfo
    dh_installman $(CURDIR)/debian/manpages/*.*
    dh_link
    dh_strip
    dh_compress
    dh_fixperms
#    dh_perl
#    dh_makeshlibs
    dh_installdeb
    dh_shlibdeps
    dh_gencontrol
    dh_md5sums
    dh_builddeb

binary: binary-indep binary-arch
.PHONY: build clean binary-indep binary-arch binary install configure

```

---

### Post by schragge on 2013-04-24
Ouch. It's the other way round. You probably don't need *dh $@ --with python2* as you're running all debhelper scripts per hand anyway. I was under impression your package uses setuptools/distribute/distutils. Obviously not.

Perhaps you should run *dh_python2* twice in debian/rules:
```

dh_python2
dh_python2 /path/to/private/modules/dir

```
and maybe change *Depends: python* in *debian/control* to ```
Depends: ${python:Depends}
``` but obviously you know your application better. Sorry, I can't help you here.

---

### Post by schragge on 2013-04-24
Well, I cleaned up the debian directory, take a look at it: [ATTACH]241733[/ATTACH] It's only a starting point.

For how to properly package python apps, see [http://wiki.debian.org/Python/AppStyleGuide](http://wiki.debian.org/Python/AppStyleGuide)

---

### Post by VinsS on 2013-04-25
Ok, that's more clear like that. I was not sure for the syntax for the file install.

I've tested and, now, the file are properly compiled at the install.

Many thanks.

A question: in the changelog "qarte (1.7-0+local1) UNRELEASED" what means "+local1) UNRELEASED" ? I don't see anything about that in the Debian policy.

---

### Post by schragge on 2013-04-25
*+local1* means it's my local build. I added this to not clash with possible future official package updates. Consider following:

Suppose I build and install 1.7-1 locally, then you release the same version, and I cannot install it from repository because I already have 1.7-1 installed, although it's not the same version as yours. To prevent this, [dch]("http://manpages.ubuntu.com/manpages/raring/man1/debchange.1.html") has an option *--local* that appends this suffix to release number when adding a new changelog entry.

This practice gets briefly mentioned in [chapter 9]("http://www.debian.org/doc/manuals/maint-guide/update.en.html") of *Debian New Maintainers' Guide* and in [chapter 15]("http://debian-handbook.info/browse/stable/debian-packaging.html#idp9516880") of the *Debian Administrator's Handbook*. Also see [this blog entry]("http://raphaelhertzog.com/2010/12/15/howto-to-rebuild-debian-packages/") by one of the authors of the latter book.

Similarly, UNRELEASED is just a placeholder. Its purpose is described in [chapter 4]("http://www.debian.org/doc/manuals/maint-guide/dreq.en.html#changelog") of DNMG. Change it to actual release codename you're building for: precise, quantal, raring, whatever. See also description of package version in [chapter 2]("http://www.debian.org/doc/manuals/maint-guide/first.en.html#namever") of DNMG. The information is also scattered across Debian Wiki, e.g. [HowToRebuildAnOfficialDebianKernelPackage]("http://wiki.debian.org/HowToRebuildAnOfficialDebianKernelPackage#line-58") mentions it as well.

Obviously, my *debian/changelog* is fake: it's neither initial release nor am I the package maintainer. Replace it with yours. The *debian/copyright* is also most probably wrong/incomplete and should be replaced.

Instead of *debian/pyversions*, dh_python2 now uses X-Python-Version: field in *debian/control*. Put in the source package stanza there something like ```
X-Python-Version: >= 2.4
``` if that's the minimum required Python version for the package.

Also, I didn't install gettext files in i18n/.

---

### Post by VinsS on 2013-04-25
Yes, I've replaced the changelog by the min.

Again thanks

---

