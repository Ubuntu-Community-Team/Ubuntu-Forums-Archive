---
title: "Mysterious signing error in Debuild"
date: 2013-10-28
forum: Packaging and Compiling Programs
---

### Post by IndigoJo on 2013-10-28
I recently installed Saucy and have been packaging my own application and publishing it through Launchpad for years. This morning, when I tried to package my app for Saucy, I could not get it to sign. My name, nickname and email address are all correct; I've generated a new key with the same particulars and it still won't sign.

The error does not occur when I get the passphrase wrong; it occurs when I get it right. When I get the passphrase wrong, it asks me for it again.

Here's the output when I try to build:

```
indigojo@indigojo-Macmini:~/debian/qtm-1.3.14$ debuild -S -rfakeroot -sa -k8F5B5734
 dpkg-buildpackage -rfakeroot -d -us -uc -S -sa
dpkg-buildpackage: source package qtm
dpkg-buildpackage: source version 1.3.14-0ubuntu2~ppa4
dpkg-buildpackage: source changed by Matthew Smith (Yusuf) <indigojo@blogistan.co.uk>
 dpkg-source --before-build qtm-1.3.14
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Entering directory `/home/indigojo/debian/qtm-1.3.14'
make[1]: *** No rule to make target `clean'. Stop.
make[1]: Leaving directory `/home/indigojo/debian/qtm-1.3.14'
make: [clean] Error 2 (ignored)
rm -rf CMakeFiles cmake_install.cmake CMakeCache.txt Makefile *.make
dh_clean 
 dpkg-source -b qtm-1.3.14
dpkg-source: warning: no source format specified in debian/source/format, see dpkg-source(1)
dpkg-source: warning: Version number suggests Ubuntu changes, but Maintainer: does not have Ubuntu address
dpkg-source: warning: Version number suggests Ubuntu changes, but there is no XSBC-Original-Maintainer field
dpkg-source: info: using source format `1.0'
dpkg-source: info: building qtm using existing qtm_1.3.14.orig.tar.gz
dpkg-source: info: building qtm in qtm_1.3.14-0ubuntu2~ppa4.diff.gz
dpkg-source: warning: the diff modifies the following upstream files: 
 gpg-message
 install_manifest.txt
 install_manifest.txt.debdiff
 ubuntu-message
dpkg-source: info: use the '3.0 (quilt)' format to have separate and documented changes to upstream files, see dpkg-source(1)
dpkg-source: info: building qtm in qtm_1.3.14-0ubuntu2~ppa4.dsc
 dpkg-genchanges -S -sa >../qtm_1.3.14-0ubuntu2~ppa4_source.changes
dpkg-genchanges: including full source code in upload
 dpkg-source --after-build qtm-1.3.14
dpkg-buildpackage: source only upload (original source is included)
Now running lintian...
W: qtm source: debian-rules-ignores-make-clean-error line 48
W: qtm source: debian-rules-missing-recommended-target build-arch
W: qtm source: debian-rules-missing-recommended-target build-indep
Finished running lintian.
Now signing changes and any dsc files...
 signfile qtm_1.3.14-0ubuntu2~ppa4.dsc 8F5B5734


You need a passphrase to unlock the secret key for
user: "Matthew Smith (Yusuf) <indigojo@blogistan.co.uk>"
2048-bit RSA key, ID 93547622, created 2013-10-28


gpg: problem with the agent - disabling agent use
                  
You need a passphrase to unlock the secret key for
user: "Matthew Smith (Yusuf) <indigojo@blogistan.co.uk>"
2048-bit RSA key, ID 93547622, created 2013-10-28
gpg: Invalid passphrase; please try again ...


                  
gpg: Invalid passphrase; please try again ...
You need a passphrase to unlock the secret key for
user: "Matthew Smith (Yusuf) <indigojo@blogistan.co.uk>"
2048-bit RSA key, ID 93547622, created 2013-10-28


debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1280:
running debsign failed

```
I've tried using both the pub and sub IDs for the GPG key; I've checked that the Changelog has the same particulars as the GPG key. I wonder if the "problem with the agent" is the issue, but then I prefer a console passphrase prompt as I use a long passphrase which it's difficult to remember, so copy and paste is a must and none of the passphrase dialogs have that.

---

