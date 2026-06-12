---
title: "Can't figure out how to set up up a ppa, going mad slowly"
date: 2012-02-24
forum: Packaging and Compiling Programs
---

### Post by Dr.Bimle on 2012-02-24
Hope some of you guys can help me - I must be incredibly daft because I can't figure it out myself having spent two days browsing launchpad manuals and user guides.

Step one: dh_make

My directory: /home/ppa/ubuntu-1.0/Ubuntu

From /ubuntu-1.0 I run
```
 dh_make -e my@email.com --createorig
```

That gives the orig tar ball in the parent directory and the debian subdirectory. I edit all debian files as instructed on several webmanuals, add an install file (it's an Ubuntu theme for Cinnamon I want to package) and:
```
debuild -S
```

I then get:
```
 dpkg-buildpackage -rfakeroot -d -us -uc -S
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package ubuntu
dpkg-buildpackage: source version 1.0-1
dpkg-buildpackage: source changed by brian <my@email.com>
 dpkg-source --before-build ubuntu-1.0
 fakeroot debian/rules clean
dh clean 
   dh_testdir
   dh_auto_clean
   dh_clean
 dpkg-source -b ubuntu-1.0
dpkg-source: info: using source format `3.0 (quilt)'
dpkg-source: info: building ubuntu using existing ./ubuntu_1.0.orig.tar.gz
dpkg-source: warning: ignoring deletion of directory cinnamon
dpkg-source: warning: ignoring deletion of file cinnamon/filter-selected.svg
dpkg-source: warning: ignoring deletion of file cinnamon/toggle-on-us.svg
dpkg-source: warning: ignoring deletion of file cinnamon/toggle-off-intl.svg
dpkg-source: warning: ignoring deletion of file cinnamon/menu-symbolic.svg
dpkg-source: warning: ignoring deletion of file cinnamon/theme.json
dpkg-source: warning: ignoring deletion of file cinnamon/scroll-vhandle.svg
dpkg-source: warning: ignoring deletion of file cinnamon/corner-ripple.png
dpkg-source: warning: ignoring deletion of file cinnamon/close.png
dpkg-source: warning: ignoring deletion of file cinnamon/process-working.svg
dpkg-source: warning: ignoring deletion of file cinnamon/thumbnail.png
dpkg-source: warning: ignoring deletion of file cinnamon/calendar-arrow-left.svg
dpkg-source: warning: ignoring deletion of file cinnamon/scroll-hhandle.svg
dpkg-source: warning: ignoring deletion of file cinnamon/ws-switch-arrow-up.svg
dpkg-source: warning: ignoring deletion of file cinnamon/toggle-on-intl.svg
dpkg-source: warning: ignoring deletion of file cinnamon/dash-placeholder.svg
dpkg-source: warning: ignoring deletion of file cinnamon/cinnamon.css
dpkg-source: warning: ignoring deletion of file cinnamon/close-hover.png
dpkg-source: warning: ignoring deletion of file cinnamon/toggle-off-us.svg
dpkg-source: warning: ignoring deletion of file cinnamon/close-pressed.png
dpkg-source: warning: ignoring deletion of file cinnamon/calendar-arrow-right.svg
dpkg-source: warning: ignoring deletion of file cinnamon/ws-switch-arrow-down.svg
dpkg-source: error: cannot represent change to ubuntu-1.0/Ubuntu/cinnamon/corner-ripple.png: binary file contents changed
dpkg-source: error: add Ubuntu/cinnamon/corner-ripple.png in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to ubuntu-1.0/Ubuntu/cinnamon/close.png: binary file contents changed
dpkg-source: error: add Ubuntu/cinnamon/close.png in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to ubuntu-1.0/Ubuntu/cinnamon/thumbnail.png: binary file contents changed
dpkg-source: error: add Ubuntu/cinnamon/thumbnail.png in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to ubuntu-1.0/Ubuntu/cinnamon/close-hover.png: binary file contents changed
dpkg-source: error: add Ubuntu/cinnamon/close-hover.png in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to ubuntu-1.0/Ubuntu/cinnamon/close-pressed.png: binary file contents changed
dpkg-source: error: add Ubuntu/cinnamon/close-pressed.png in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: unrepresentable changes to source
dpkg-buildpackage: error: dpkg-source -b ubuntu-1.0 gave error exit status 2
debuild: fatal error at line 1348:
dpkg-buildpackage -rfakeroot -d -us -uc -S failed

```

Sometimes, other times I try this the source.changes file is built (along with the .dcs file) but it won't upload to launchpad, I don't get prompted for gpg keys.




Can someone help out a ppa noob? :(

---

### Post by oldos2er on 2012-02-25
Moved to Packaging and Compiling Programs.

---

### Post by Yellow Pasque on 2012-02-26
It looks like you're changing files other than those in the debian/ subdir. You should not modify the source directly.

---

