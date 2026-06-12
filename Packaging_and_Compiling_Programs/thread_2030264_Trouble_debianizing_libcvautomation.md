---
title: "Trouble debianizing libcvautomation"
date: 2012-07-20
forum: Packaging and Compiling Programs
---

### Post by djbushido on 2012-07-20
Hello all! I've recently been creating a software product called libcvautomation. I've gotten the autotools up and running, and created an RPM for it.
I've had significant troubles trying to create the Debian package though.
I'm creating a multiple binary package, but there is only one ./configure, etc.
I've created .install files for all the packages that should result, but I'm doing something wrong, because all generated packages are empty, and it's not building a package for the actual project - i.e. no libcvautomation.deb.
By any means, I've put what I believe is the relevant content below, please let me know if anything else is needed.
You can download the source from git at [https://github.com/DjBushido/libcvautomation](https://github.com/DjBushido/libcvautomation), which will build. To get a dist tarball run "./autogen.sh; ./configure; make; make dist".

And the code I have for debianizing the package:

debian/control:
```
Source: libcvautomation
Section: Development
Priority: extra
Maintainer: Bradlee Speice <bspeice@uncc.edu>
Build-Depends: debhelper (>= 8.0.0), autotools-dev, pkg-config, libpcre3, libx11-dev, libopencv-core-dev, libopencv-highgui-dev, libopencv-imgproc-dev
Standards-Version: 3.9.2
Homepage: http://djbushido.github.com/libcvautomation/
#Vcs-Git: git://git.debian.org/collab-maint/libcvautomation.git
#Vcs-Browser: http://git.debian.org/?p=collab-maint/libcvautomation.git;a=summary

Package: libcvautomation
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}, libxtst6, libx11, libopencv-core2.3, libopencv-highgui2.3, libopencv-imgproc2.3
Description: Libcvautomation - GUI Automation and Testing Library
 Libcvautomation is a GUI automation and testing tool based on image recognition and response. This program was designed as a direct replacement for Sikuli and Xpresser. Each solution had large problems with crashing, and both refused to function on Red Hat Linux and Ubuntu 12.04. The author really liked the way each of these programs approached GUI automation, but they simply didn't work. As such, a simple library was designed to integrate OpenCV and XTest, which can be used by BASH to drive GUI testing and automation, and works on both new and old Linux distributions.

Package: libcvautomation-doc
Architecture: all
Description: documentation for libcvautomation
 Contains the HTML documentation for libcvautomation.

Package: libcvautomation-dev
Depends: libcvautomation (= 1.3)
Architecture: any
Description: development files for libcvautomation
 Contains all files needed to build programs on top of libcvautomation

Package: libcvautomation-examples
Depends: ${shlibs:Depends}, ${misc:Depends}, libxtst6, libx11, libopencv-core2.3, libopencv-highgui2.3, libopencv-imgproc2.3
Architecture: any
Description: Example programs to demonstrate libcvautomation functionality
 Contains programs designed to showcase the functionality of libcvautomation, as well as a BASH wrapper to write application tests from BASH.
```

And an example .install file:
debian/libcvautomation-examples.install:
```
etc/libcvautomation_funcs etc/libcvautomation_funcs
usr/bin/* usr/bin/
usr/share/man/man1/* usr/share/man/man1/
```

One final note: I have a working .spec file at [https://github.com/DjBushido/libcvautomation/blob/master/rpm/libcvautomation.spec.in](https://github.com/DjBushido/libcvautomation/blob/master/rpm/libcvautomation.spec.in) if it's helpful.

---

### Post by MadCow108 on 2012-07-20
please show the debian folder or at least a build log and debian/rules

the only thing I can say from your info is that the library package should be versioned e.g. libcvautomation*soversion* and the -dev package should have such a depend to avoid forgetting to update it:
Depends: libcvautomation (= ${binary:Version})

also the descriptions should be wrapped to 80 characters lines

---

### Post by djbushido on 2012-07-20
Thank you for the tips, I'll definitely get those in.

Do you want just a listing of the debian/ folder?
If so:
```
$ ls
changelog
compat
control
copyright
docs
emacsen-install.ex
emacsen-remove.ex
emacsen-startup.ex
files
init.d.ex
libcvautomation
libcvautomation.cron.d.ex
libcvautomation.debhelper.log
libcvautomation.default.ex
libcvautomation-dev
libcvautomation-dev.debhelper.log
libcvautomation-dev.install
libcvautomation-dev.substvars
libcvautomation-doc
libcvautomation.doc-base.EX
libcvautomation-doc.debhelper.log
libcvautomation-doc.docs
libcvautomation-doc.install
libcvautomation-doc.substvars
libcvautomation-examples
libcvautomation-examples.debhelper.log
libcvautomation-examples.install
libcvautomation-examples.substvars
libcvautomation.install
manpage.1.ex
manpage.sgml.ex
manpage.xml.ex
menu.ex
postinst.ex
postrm.ex
preinst.ex
prerm.ex
README.Debian
README.source
rules
source
watch.ex

```

An example build log (I removed all the text up through make install, let me know if you want this as well):
```
 fakeroot debian/rules binary
dh_testdir
dh_testroot
dh_installdirs
dh_installman
dh_link -plibcvautomation-doc
dh_strip -plibcvautomation-doc
dh_compress -plibcvautomation-doc
dh_fixperms -plibcvautomation-doc
dh_makeshlibs -plibcvautomation-doc
dh_installdeb -plibcvautomation-doc
dh_gencontrol -plibcvautomation-doc
dh_md5sums -plibcvautomation-doc
dh_builddeb -plibcvautomation-doc
dpkg-deb: building package `libcvautomation-doc' in `../libcvautomation-doc_1.3-1_all.deb'.
dh_testdir
dh_testroot
dh_installdirs
dh_installman
dh_link -plibcvautomation-dev
dh_strip -plibcvautomation-dev
dh_compress -plibcvautomation-dev
dh_fixperms -plibcvautomation-dev
dh_makeshlibs -plibcvautomation-dev
dh_installdeb -plibcvautomation-dev
dh_gencontrol -plibcvautomation-dev
dh_md5sums -plibcvautomation-dev
dh_builddeb -plibcvautomation-dev
dpkg-deb: building package `libcvautomation-dev' in `../libcvautomation-dev_1.3-1_amd64.deb'.
dh_testdir
dh_testroot
dh_installdirs
dh_installman
dh_link -plibcvautomation-examples
dh_strip -plibcvautomation-examples
dh_compress -plibcvautomation-examples
dh_fixperms -plibcvautomation-examples
dh_makeshlibs -plibcvautomation-examples
dh_installdeb -plibcvautomation-examples
dh_gencontrol -plibcvautomation-examples
dpkg-gencontrol: warning: Depends field of package libcvautomation-examples: unknown substitution variable ${shlibs:Depends}
dh_md5sums -plibcvautomation-examples
dh_builddeb -plibcvautomation-examples
dpkg-deb: building package `libcvautomation-examples' in `../libcvautomation-examples_1.3-1_amd64.deb'.
 dpkg-genchanges  >../libcvautomation_1.3-1_amd64.changes
dpkg-genchanges: warning: package libcvautomation in control file but not in files list
dpkg-genchanges: including full source code in upload
 dpkg-source --after-build libcvautomation-1.3
dpkg-buildpackage: full upload (original source is included)
Now running lintian...
W: libcvautomation source: debhelper-but-no-misc-depends libcvautomation-doc
W: libcvautomation source: debhelper-but-no-misc-depends libcvautomation-dev
W: libcvautomation source: dh-make-template-in-source debian/emacsen-install.ex
W: libcvautomation source: dh-make-template-in-source debian/emacsen-remove.ex
W: libcvautomation source: dh-make-template-in-source debian/emacsen-startup.ex
W: libcvautomation source: dh-make-template-in-source debian/init.d.ex
W: libcvautomation source: dh-make-template-in-source debian/libcvautomation.cron.d.ex
W: libcvautomation source: dh-make-template-in-source debian/libcvautomation.default.ex
W: libcvautomation source: dh-make-template-in-source debian/libcvautomation.doc-base.EX
W: libcvautomation source: dh-make-template-in-source debian/manpage.1.ex
W: libcvautomation source: dh-make-template-in-source debian/manpage.sgml.ex
W: libcvautomation source: dh-make-template-in-source debian/manpage.xml.ex
W: libcvautomation source: dh-make-template-in-source debian/menu.ex
W: libcvautomation source: dh-make-template-in-source debian/postinst.ex
W: libcvautomation source: dh-make-template-in-source debian/postrm.ex
W: libcvautomation source: dh-make-template-in-source debian/preinst.ex
W: libcvautomation source: dh-make-template-in-source debian/prerm.ex
W: libcvautomation source: dh-make-template-in-source debian/watch.ex
E: libcvautomation source: debian-rules-missing-required-target binary-arch
E: libcvautomation source: debian-rules-missing-required-target binary-indep
W: libcvautomation source: debian-rules-missing-recommended-target build-arch
W: libcvautomation source: debian-rules-missing-recommended-target build-indep
W: libcvautomation source: package-would-benefit-from-build-arch-targets
W: libcvautomation source: missing-field-in-dep5-copyright license (paragraph at line 5)
W: libcvautomation source: out-of-date-standards-version 3.9.2 (current is 3.9.3)
E: libcvautomation-examples: no-copyright-file
W: libcvautomation-examples: extended-description-line-too-long
W: libcvautomation-examples: unknown-section Development
W: libcvautomation-examples: empty-binary-package
E: libcvautomation-doc: no-copyright-file
W: libcvautomation-doc: unknown-section Development
W: libcvautomation-doc: wrong-section-according-to-package-name libcvautomation-doc => doc
W: libcvautomation-doc: empty-binary-package
E: libcvautomation-dev: no-copyright-file
W: libcvautomation-dev: unknown-section Development
W: libcvautomation-dev: wrong-section-according-to-package-name libcvautomation-dev => libdevel
W: libcvautomation-dev: empty-binary-package
Finished running lintian.
```

And the rules file:
```
#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
#
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.
#
# Modified to make a template file for a multi-binary package with separated
# build-arch and build-indep targets  by Bill Allombert 2001

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

# This has to be exported to make some magic below work.
export DH_OPTIONS

clean:
	dh_testdir
	dh_auto_clean
	dh_clean

build:
	dh_testdir
	dh_auto_configure
	dh_auto_build

install:
	dh_testdir
	dh_testroot
	dh_prep
	dh_auto_install DESTDIR=${DESTDIR}

binary: libcvautomation libcvautomation-doc libcvautomation-dev libcvautomation-examples

libcvautomation:
	dh_testdir
	dh_testroot
	dh_installdirs
	dh_installman
	dh_link -p$@
	dh_strip -p$@
	dh_compress -p$@
	dh_fixperms -p$@
	dh_makeshlibs -p$@
	dh_installdeb -p$@
	dh_gencontrol -p$@
	dh_md5sums -p$@
	dh_builddeb -p$@

libcvautomation-doc:
	dh_testdir
	dh_testroot
	dh_installdirs
	dh_installman
	dh_link -p$@
	dh_strip -p$@
	dh_compress -p$@
	dh_fixperms -p$@
	dh_makeshlibs -p$@
	dh_installdeb -p$@
	dh_gencontrol -p$@
	dh_md5sums -p$@
	dh_builddeb -p$@

libcvautomation-dev:
	dh_testdir
	dh_testroot
	dh_installdirs
	dh_installman
	dh_link -p$@
	dh_strip -p$@
	dh_compress -p$@
	dh_fixperms -p$@
	dh_makeshlibs -p$@
	dh_installdeb -p$@
	dh_gencontrol -p$@
	dh_md5sums -p$@
	dh_builddeb -p$@

libcvautomation-examples:
	dh_testdir
	dh_testroot
	dh_installdirs
	dh_installman
	dh_link -p$@
	dh_strip -p$@
	dh_compress -p$@
	dh_fixperms -p$@
	dh_makeshlibs -p$@
	dh_installdeb -p$@
	dh_gencontrol -p$@
	dh_md5sums -p$@
	dh_builddeb -p$@


```

Thank you much for the help!

---

### Post by MadCow108 on 2012-07-21
you rules file is unnecessarily long, it can be much shorter nowadays.
see man dh

replace it with this here:
```
#!/usr/bin/make -f
%:
     dh $@
```

as your source looks autotools based it you may want to use:
dh $@ --with autoreconf
or less favorable:
dh $@ --with autotools_dev

with appropriate build depends on dh-autoreconf or autotools-dev


the build log did not actually build anything. without the source I can't say why.

---

### Post by djbushido on 2012-07-21
The source is available on github - I posted a link previously, but if you need the most recent dist tarball, I've attached it to this post. Let me know if there are any other questions.
The build process itself uses autotools exclusively, and I can confirm that the build is working. I apologize that I can't be of more help, but let me know if there's anything that I can do.

EDIT: Apparently the tarball got lost... Re-attached.

---

### Post by MadCow108 on 2012-07-21
there is no debian folder on the github page

---

### Post by djbushido on 2012-07-21
Alright, I had a local commit that I was doing this work with, and didn't have access to it (different computers).
In trying to recreate everything, it's now working. I have absolutely no idea what I did differently, but apparently it was something. My best guess is that something was up with the .install file.
At this point I have a bunch of lintian errors to clean up, but the basic build is working.
I apologize that I have no idea how to fix this for anyone that might read this in the future, but everything appears to be working fine for now.
Thank you for bearing with me!

Edit: That being said, if someone wants to get an idea of what the initial debian tree looks like, check out commit 04131913b2c89eb07e6b94db387c39208f5ac753 for libcvautomation - [https://github.com/DjBushido/libcvautomation/tree/04131913b2c89eb07e6b94db387c39208f5ac753](https://github.com/DjBushido/libcvautomation/tree/04131913b2c89eb07e6b94db387c39208f5ac753)

---

