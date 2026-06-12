---
title: "dpkg-buildpackage error !"
date: 2012-05-03
forum: Packaging and Compiling Programs
---

### Post by etdsbastar on 2012-05-03
Hello friends,

I am using Ubuntu 10.10. Today, I had successfully compiled the latest version of Gambas 3.3.1 and installed with the command:

```
make install
```Now, I want to make a debian file and upload it in my PPA here:

```
ppa:khmedia/gambas-3
```But, the dpkg-buildpackage is showing me the error:

```
dpkg-buildpackage: error: fakeroot debian/rules binary-arch gave error exit status 2
```I had used the command:

```
dpkg-buildpackage -rfakeroot -D -B -us -uc
```to build the debian file.

Please help friends, I am really new in creating DEB files and uploading to PPAs...

---

### Post by r-senior on 2012-05-03
Have you tried using debuild or bzr builddeb?:

[http://developer.ubuntu.com/packaging/html/packaging-new-software.html#building-the-package](http://developer.ubuntu.com/packaging/html/packaging-new-software.html#building-the-package)

---

### Post by etdsbastar on 2012-05-03
Dear,

debuild is giving me the following error:

```
dpkg-source: error: can't build with source format '3.0 (quilt)': no orig.tar file found
dpkg-buildpackage: error: dpkg-source -b gambas-3.3.1~3.3.1 gave error exit status 255
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -D -us -uc failed
```If i am using debuild as

```
 debuild -uc -us -B
```

then the following error is coming:

```
dh_auto_build: make -j1 returned exit code 2
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -D -us -uc -B failed
```

---

### Post by r-senior on 2012-05-03
You need the 'upstream' tarball for debuild to make diffs against. This has to be in the directory above your project directory and named according to the Debian upstream version standard, e.g. gambas_3.3.1.orig.tar.gz. This is the raw archive that doesn't include your packaging information or packaging modifications.

Also, if you want to upload this to a PPA, you need to sign the package with your GPG key. So don't use the -us and -uc options -- they mean 'unsigned'.

The command to use is 'debuild -S' from your project directory. If it is successful, it will create a *source.changes file alongside the upstream tarball, i.e. a level above your project directory, and it's that file that you submit with dput.

---

### Post by etdsbastar on 2012-05-03
Dear friend,

.orig.tar error has been rectified as per your solution. Thanks for that. But now the terminal is filled up with these:

```
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/opengl/.libs/gb.qt4.opengl.so.0.0.0: binary file contents changed
dpkg-source: error: add gb.qt4/src/opengl/.libs/gb.qt4.opengl.so.0.0.0 in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/opengl/.libs/gb.qt4.opengl.la:
dpkg-source: error:   new version is symlink to ../gb.qt4.opengl.la
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/opengl/.libs/CGLarea_moc.o: binary file contents changed
dpkg-source: error: add gb.qt4/src/opengl/.libs/CGLarea_moc.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/gb.qt4/gb.qt4.gambas: binary file contents changed
dpkg-source: error: add gb.qt4/src/gb.qt4/gb.qt4.gambas in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/cwebframe_moc.o: binary file contents changed
dpkg-source: error: add gb.qt4/src/webkit/.libs/cwebframe_moc.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/gb.qt4.webkit.so.0.0.0: binary file contents changed
dpkg-source: error: add gb.qt4/src/webkit/.libs/gb.qt4.webkit.so.0.0.0 in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/cwebdownload_moc.o: binary file contents changed
dpkg-source: error: add gb.qt4/src/webkit/.libs/cwebdownload_moc.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/cwebview.o: binary file contents changed
dpkg-source: error: add gb.qt4/src/webkit/.libs/cwebview.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/cwebview_moc.o: binary file contents changed
dpkg-source: error: add gb.qt4/src/webkit/.libs/cwebview_moc.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/cwebhittest.o: binary file contents changed
dpkg-source: error: add gb.qt4/src/webkit/.libs/cwebhittest.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/ccookiejar.o: binary file contents changed
dpkg-source: error: add gb.qt4/src/webkit/.libs/ccookiejar.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/gb.qt4.webkit.so.0:
dpkg-source: error:   new version is symlink to gb.qt4.webkit.so.0.0.0
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/cwebdownload.o: binary file contents changed
dpkg-source: error: add gb.qt4/src/webkit/.libs/cwebdownload.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/gb.qt4.webkit.la:
dpkg-source: error:   new version is symlink to ../gb.qt4.webkit.la
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/main.o: binary file contents changed
dpkg-source: error: add gb.qt4/src/webkit/.libs/main.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/ccookiejar_moc.o: binary file contents changed
dpkg-source: error: add gb.qt4/src/webkit/.libs/ccookiejar_moc.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/cwebframe.o: binary file contents changed
dpkg-source: error: add gb.qt4/src/webkit/.libs/cwebframe.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/gb.qt4.webkit.so:
dpkg-source: error:   new version is symlink to gb.qt4.webkit.so.0.0.0
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.qt4/src/webkit/.libs/cwebsettings.o: binary file contents changed
dpkg-source: error: add gb.qt4/src/webkit/.libs/cwebsettings.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/gb.image.h:
dpkg-source: error:   new version is symlink to ../main/lib/image/gb.image.h
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'gb.desktop/warnings.log' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'gb.desktop/ltmain.sh' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'gb.desktop/install-sh' will not be represented in diff
dpkg-source: warning: newly created empty file 'gb.desktop/README' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/COPYING:
dpkg-source: error:   new version is symlink to ../COPYING
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/gb_list.h:
dpkg-source: error:   new version is symlink to ../main/share/gb_list.h
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: executable mode 0755 of 'gb.desktop/config.sub' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/reconf:
dpkg-source: error:   new version is symlink to ../reconf
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'gb.desktop/AUTHORS' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/missing:
dpkg-source: error:   new version is symlink to ../missing
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/INSTALL:
dpkg-source: error:   new version is symlink to ../INSTALL
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/component.am:
dpkg-source: error:   new version is symlink to ../component.am
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'gb.desktop/NEWS' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'gb.desktop/config.guess' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'gb.desktop/configure' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/gb_list_temp.h:
dpkg-source: error:   new version is symlink to ../main/share/gb_list_temp.h
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/acinclude.m4:
dpkg-source: error:   new version is symlink to ../acinclude.m4
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/gb_common.h:
dpkg-source: error:   new version is symlink to ../main/share/gb_common.h
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/gambas.h:
dpkg-source: error:   new version is symlink to ../main/share/gambas.h
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: executable mode 0755 of 'gb.desktop/depcomp' will not be represented in diff
dpkg-source: warning: newly created empty file 'gb.desktop/ChangeLog' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/gb.desktop.component:
dpkg-source: error:   new version is symlink to gb.desktop/.component
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/.libs/desktop.o: binary file contents changed
dpkg-source: error: add gb.desktop/src/.libs/desktop.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/.libs/gb_list.o: binary file contents changed
dpkg-source: error: add gb.desktop/src/.libs/gb_list.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/.libs/gb.desktop.so.0.0.0: binary file contents changed
dpkg-source: error: add gb.desktop/src/.libs/gb.desktop.so.0.0.0 in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/.libs/x11.o: binary file contents changed
dpkg-source: error: add gb.desktop/src/.libs/x11.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/.libs/gb.desktop.so.0:
dpkg-source: error:   new version is symlink to gb.desktop.so.0.0.0
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/.libs/main.o: binary file contents changed
dpkg-source: error: add gb.desktop/src/.libs/main.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/.libs/gb.desktop.so:
dpkg-source: error:   new version is symlink to gb.desktop.so.0.0.0
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/.libs/gb.desktop.la:
dpkg-source: error:   new version is symlink to ../gb.desktop.la
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/gb.desktop/.icon.png: binary file contents changed
dpkg-source: error: add gb.desktop/src/gb.desktop/.icon.png in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/gb.desktop/gb.desktop.gambas: binary file contents changed
dpkg-source: error: add gb.desktop/src/gb.desktop/gb.desktop.gambas in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: warning: executable mode 0775 of 'gb.desktop/src/gb.desktop/.hidden/xdg-utils-1.0.2/scripts/xdg-email' will not be represented in diff
dpkg-source: warning: executable mode 0775 of 'gb.desktop/src/gb.desktop/.hidden/xdg-utils-1.0.2/scripts/xdg-mime' will not be represented in diff
dpkg-source: warning: executable mode 0775 of 'gb.desktop/src/gb.desktop/.hidden/xdg-utils-1.0.2/scripts/xdg-desktop-icon' will not be represented in diff
dpkg-source: warning: executable mode 0775 of 'gb.desktop/src/gb.desktop/.hidden/xdg-utils-1.0.2/scripts/xdg-open' will not be represented in diff
dpkg-source: warning: executable mode 0775 of 'gb.desktop/src/gb.desktop/.hidden/xdg-utils-1.0.2/scripts/xdg-icon-resource' will not be represented in diff
dpkg-source: warning: executable mode 0775 of 'gb.desktop/src/gb.desktop/.hidden/xdg-utils-1.0.2/scripts/xdg-desktop-menu' will not be represented in diff
dpkg-source: warning: executable mode 0775 of 'gb.desktop/src/gb.desktop/.hidden/xdg-utils-1.0.2/scripts/xdg-screensaver' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/gb.desktop/.hidden/control/desktopwatcher.png: binary file contents changed
dpkg-source: error: add gb.desktop/src/gb.desktop/.hidden/control/desktopwatcher.png in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/gnome/.libs/gb.desktop.gnome.so.0.0.0: binary file contents changed
dpkg-source: error: add gb.desktop/src/gnome/.libs/gb.desktop.gnome.so.0.0.0 in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/gnome/.libs/gb.desktop.gnome.la:
dpkg-source: error:   new version is symlink to ../gb.desktop.gnome.la
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/gnome/.libs/keyring.o: binary file contents changed
dpkg-source: error: add gb.desktop/src/gnome/.libs/keyring.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/gnome/.libs/main.o: binary file contents changed
dpkg-source: error: add gb.desktop/src/gnome/.libs/main.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/gnome/.libs/gb.desktop.gnome.so:
dpkg-source: error:   new version is symlink to gb.desktop.gnome.so.0.0.0
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.desktop/src/gnome/.libs/gb.desktop.gnome.so.0:
dpkg-source: error:   new version is symlink to gb.desktop.gnome.so.0.0.0
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'gb.compress.zlib/warnings.log' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/gb.compress.h:
dpkg-source: error:   new version is symlink to ../main/lib/compress/gb.compress.h
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: executable mode 0755 of 'gb.compress.zlib/ltmain.sh' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'gb.compress.zlib/install-sh' will not be represented in diff
dpkg-source: warning: newly created empty file 'gb.compress.zlib/README' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/COPYING:
dpkg-source: error:   new version is symlink to ../COPYING
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: executable mode 0755 of 'gb.compress.zlib/config.sub' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/reconf:
dpkg-source: error:   new version is symlink to ../reconf
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'gb.compress.zlib/AUTHORS' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/missing:
dpkg-source: error:   new version is symlink to ../missing
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/INSTALL:
dpkg-source: error:   new version is symlink to ../INSTALL
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'gb.compress.zlib/NEWS' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'gb.compress.zlib/config.guess' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'gb.compress.zlib/configure' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/acinclude.m4:
dpkg-source: error:   new version is symlink to ../acinclude.m4
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/gb_common.h:
dpkg-source: error:   new version is symlink to ../main/share/gb_common.h
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/gambas.h:
dpkg-source: error:   new version is symlink to ../main/share/gambas.h
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/depcomp:
dpkg-source: error:   new version is symlink to ../depcomp
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'gb.compress.zlib/ChangeLog' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/src/.libs/gb.compress.zlib.so:
dpkg-source: error:   new version is symlink to gb.compress.zlib.so.0.0.0
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/src/.libs/gb.compress.zlib.la:
dpkg-source: error:   new version is symlink to ../gb.compress.zlib.la
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/src/.libs/main.o: binary file contents changed
dpkg-source: error: add gb.compress.zlib/src/.libs/main.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/src/.libs/gb.compress.zlib.so.0.0.0: binary file contents changed
dpkg-source: error: add gb.compress.zlib/src/.libs/gb.compress.zlib.so.0.0.0 in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.compress.zlib/src/.libs/gb.compress.zlib.so.0:
dpkg-source: error:   new version is symlink to gb.compress.zlib.so.0.0.0
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/gb.image.h:
dpkg-source: error:   new version is symlink to ../main/lib/image/gb.image.h
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'gb.pdf/warnings.log' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/gb.gtk.h:
dpkg-source: error:   new version is symlink to ../gb.gtk/src/gb.gtk.h
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: executable mode 0755 of 'gb.pdf/ltmain.sh' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'gb.pdf/install-sh' will not be represented in diff
dpkg-source: warning: newly created empty file 'gb.pdf/README' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/COPYING:
dpkg-source: error:   new version is symlink to ../COPYING
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: executable mode 0755 of 'gb.pdf/config.sub' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/reconf:
dpkg-source: error:   new version is symlink to ../reconf
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'gb.pdf/AUTHORS' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/missing:
dpkg-source: error:   new version is symlink to ../missing
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/INSTALL:
dpkg-source: error:   new version is symlink to ../INSTALL
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/component.am:
dpkg-source: error:   new version is symlink to ../component.am
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'gb.pdf/NEWS' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'gb.pdf/config.guess' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'gb.pdf/configure' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/acinclude.m4:
dpkg-source: error:   new version is symlink to ../acinclude.m4
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/gb_common.h:
dpkg-source: error:   new version is symlink to ../main/share/gb_common.h
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/gambas.h:
dpkg-source: error:   new version is symlink to ../main/share/gambas.h
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/depcomp:
dpkg-source: error:   new version is symlink to ../depcomp
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: file gambas_3.3.1~maverick/gb.pdf/ChangeLog has no final newline (either original or modified version)
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/src/.libs/gb.pdf.la:
dpkg-source: error:   new version is symlink to ../gb.pdf.la
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/src/.libs/gb.pdf.so:
dpkg-source: error:   new version is symlink to gb.pdf.so.0.0.0
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/src/.libs/gb.pdf.so.0:
dpkg-source: error:   new version is symlink to gb.pdf.so.0.0.0
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/src/.libs/CPdfDocument.o: binary file contents changed
dpkg-source: error: add gb.pdf/src/.libs/CPdfDocument.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/src/.libs/main.o: binary file contents changed
dpkg-source: error: add gb.pdf/src/.libs/main.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.pdf/src/.libs/gb.pdf.so.0.0.0: binary file contents changed
dpkg-source: error: add gb.pdf/src/.libs/gb.pdf.so.0.0.0 in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/gb.db.proto.h:
dpkg-source: error:   new version is symlink to ../main/lib/db/gb.db.proto.h
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'gb.db.sqlite2/warnings.log' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'gb.db.sqlite2/ltmain.sh' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'gb.db.sqlite2/install-sh' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/COPYING:
dpkg-source: error:   new version is symlink to ../COPYING
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: executable mode 0755 of 'gb.db.sqlite2/config.sub' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/reconf:
dpkg-source: error:   new version is symlink to ../reconf
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'gb.db.sqlite2/AUTHORS' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/missing:
dpkg-source: error:   new version is symlink to ../missing
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/INSTALL:
dpkg-source: error:   new version is symlink to ../INSTALL
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/component.am:
dpkg-source: error:   new version is symlink to ../component.am
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'gb.db.sqlite2/NEWS' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/gb.db.h:
dpkg-source: error:   new version is symlink to ../main/lib/db/gb.db.h
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: executable mode 0755 of 'gb.db.sqlite2/config.guess' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'gb.db.sqlite2/configure' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/acinclude.m4:
dpkg-source: error:   new version is symlink to ../acinclude.m4
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/gb_common.h:
dpkg-source: error:   new version is symlink to ../main/share/gb_common.h
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/gambas.h:
dpkg-source: error:   new version is symlink to ../main/share/gambas.h
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/depcomp:
dpkg-source: error:   new version is symlink to ../depcomp
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: executable mode 0775 of 'gb.db.sqlite2/src/Makefile.am' will not be represented in diff
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/src/.libs/gb_db_sqlite2_la-main.o: binary file contents changed
dpkg-source: error: add gb.db.sqlite2/src/.libs/gb_db_sqlite2_la-main.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/src/.libs/gb.db.sqlite2.so.0:
dpkg-source: error:   new version is symlink to gb.db.sqlite2.so.0.0.0
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/src/.libs/gb_db_sqlite2_la-sqlitedataset.o: binary file contents changed
dpkg-source: error: add gb.db.sqlite2/src/.libs/gb_db_sqlite2_la-sqlitedataset.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/src/.libs/gb_db_sqlite2_la-stringhelper.o: binary file contents changed
dpkg-source: error: add gb.db.sqlite2/src/.libs/gb_db_sqlite2_la-stringhelper.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/src/.libs/gb.db.sqlite2.so:
dpkg-source: error:   new version is symlink to gb.db.sqlite2.so.0.0.0
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/src/.libs/gb.db.sqlite2.la:
dpkg-source: error:   new version is symlink to ../gb.db.sqlite2.la
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/src/.libs/gb_db_sqlite2_la-qry_dat.o: binary file contents changed
dpkg-source: error: add gb.db.sqlite2/src/.libs/gb_db_sqlite2_la-qry_dat.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/src/.libs/gb_db_sqlite2_la-dataset.o: binary file contents changed
dpkg-source: error: add gb.db.sqlite2/src/.libs/gb_db_sqlite2_la-dataset.o in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to gambas_3.3.1~maverick/gb.db.sqlite2/src/.libs/gb.db.sqlite2.so.0.0.0: binary file contents changed
dpkg-source: error: add gb.db.sqlite2/src/.libs/gb.db.sqlite2.so.0.0.0 in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: unrepresentable changes to source
dpkg-buildpackage: error: dpkg-source -b gambas_3.3.1~maverick gave error exit status 2
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -d -us -uc -S failed
```

Please help...

---

### Post by r-senior on 2012-05-03
Looks like you didn't clean the project before you made the source tarball. It's full of .o files. The source tarball must be a clean archive of sources only -- what you would expect to find in version control.

---

### Post by etdsbastar on 2012-05-03
Now this error with debuild -B:

```
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary-arch gave error exit status 2
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -D -us -uc -B failed
```and this with debuild -S:

```
dpkg-source: error: unrepresentable changes to source
dpkg-buildpackage: error: dpkg-source -b gambas-3.3.1 gave error exit status 2
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -d -us -uc -S failed
```Please help senior ! I don't know actually where i am wrong.

---

### Post by r-senior on 2012-05-03
Let me try it. Could you post the contents of the files from the debian directory you created for packaging? I've downloaded the source and I'm just compiling it.

---

### Post by etdsbastar on 2012-05-03
Here are the contents in zip format.

Anyhow managed with following errors:

```
gpg: /tmp/debsign.HPcsz8w5/gambas_3.3.1-1.dsc: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1258:
running debsign failed
```

---

### Post by r-senior on 2012-05-03
After a few attempts I got to that same point. 

You probably found that the trick was not to compile it. Just unpack the pure source tarball, add the debian directory and run debuild -S.

To solve the signing issue, which you need to do to upload, you need to set up your GPG key as set out in [http://developer.ubuntu.com/packaging/html/getting-set-up.html](http://developer.ubuntu.com/packaging/html/getting-set-up.html). This needs to match what you have in debian/changelog, i.e. same name and email address.

---

### Post by etdsbastar on 2012-05-03
Thanks a lot Senior.

Its great to solve a problem by a beginner in just few hours.

Thanks a lot again. I hope you will be always there for us again in need of some help.

Take care....

---

### Post by etdsbastar on 2012-05-03
Hey senior,

I got a mail from launchpad saying:

REJECTED:
Unable to find distroseries: stable
Further error processing not possible because of a critical previous error.

---

### Post by r-senior on 2012-05-03
I think you solved a lot of it yourself. Now you've seen the process it will be easier next time.

Don't forget to mark the thread solved (under Thread Tools at the top of the page).

---

### Post by etdsbastar on 2012-05-03
> **r-senior said:**
> I think you solved a lot of it yourself. Now you've seen the process it will be easier next time.

Don't forget to mark the thread solved (under Thread Tools at the top of the page).

Hey senior,

I got a mail from launchpad saying:

REJECTED:
Unable to find distroseries: stable
Further error processing not possible because of a critical previous error.

---

### Post by r-senior on 2012-05-03
You need to change the first line of your debian/changelog file so that it specifies the series you are targetting, e.g.

```
gambas (3.3.1) [COLOR="Red"]precise[/COLOR]; urgency=low
```

Debian uses 'stable', Ubuntu uses 'precise', 'oneiric', etc.

Once you have the PPA working for a series, you can easily copy it in Launchpad for other series, as long as the dependencies are compatible. There's no need to do separate packaging.

---

### Post by etdsbastar on 2012-05-03
How to get the section list, since gambas comes under Development (universe), what I have to implement on the sections. Since I got this mail:

Unknown section 'universe'

---

### Post by r-senior on 2012-05-03
I don't know how you get a list but I think you need 'devel'.

EDIT: Here's the list: [http://packages.debian.org/stable/](http://packages.debian.org/stable/). Click on the section to see the tag to use.

---

### Post by etdsbastar on 2012-05-03
Thanks a lot for all your help....

Please have a look in my First and Flawless PPA:

ppa:khmedia/gambas-3

I will definitely add more packages for which the PPAs are not available....

Thanks.

---

### Post by etdsbastar on 2012-05-04
> **r-senior said:**
> After a few attempts I got to that same point. 

You probably found that the trick was not to compile it. Just unpack the pure source tarball, add the debian directory and run debuild -S.

To solve the signing issue, which you need to do to upload, you need to set up your GPG key as set out in [http://developer.ubuntu.com/packaging/html/getting-set-up.html](http://developer.ubuntu.com/packaging/html/getting-set-up.html). This needs to match what you have in debian/changelog, i.e. same name and email address.

Just now uploaded again. Lets see what happens this time.

---

### Post by etdsbastar on 2012-05-04
What does this email means:

Rejected:
File gambas3_3.1.1-1.debian.tar.gz already exists in Gambas-3, but uploaded version has different contents. See more information about this error in [https://help.launchpad.net/Packaging/UploadErrors](https://help.launchpad.net/Packaging/UploadErrors).
Files specified in DSC are broken or missing, skipping package unpack verification.

I retried the build from Launchpad...

---

### Post by etdsbastar on 2012-05-04
Weird problem senior,

Morning I stuck into these errors:

```
cp: will not overwrite just-created `debian/gambas3/usr/share/info/.info' with `comp/src/gb.mysql/.info'
cp: will not overwrite just-created `debian/gambas3/usr/share/info/.info' with `comp/src/gb.settings/.info'
cp: will not overwrite just-created `debian/gambas3/usr/share/info/.info' with `comp/src/gb.form/.info'
cp: will not overwrite just-created `debian/gambas3/usr/share/info/.info' with `comp/src/gb.web/.info'
cp: will not overwrite just-created `debian/gambas3/usr/share/info/.info' with `comp/src/gb.eval.highlight/.info'
cp: will not overwrite just-created `debian/gambas3/usr/share/info/.info' with `comp/src/gb.db.form/.info'
cp: will not overwrite just-created `debian/gambas3/usr/share/info/.info' with `comp/src/gb.report/.info'
cp: will not overwrite just-created `debian/gambas3/usr/share/info/.info' with `comp/src/gb.form.mdi/.info'
cp: will not overwrite just-created `debian/gambas3/usr/share/info/.info' with `comp/src/gb.form.dialog/.info'
cp: will not overwrite just-created `debian/gambas3/usr/share/info/.info' with `comp/src/gb.chart/.info'
cp: will not overwrite just-created `debian/gambas3/usr/share/info/.info' with `gb.gtk/src/gb.gtk/.info'
cp: will not overwrite just-created `debian/gambas3/usr/share/info/.info' with `gb.qt4/src/gb.qt4/.info'
cp: will not overwrite just-created `debian/gambas3/usr/share/info/.info' with `gb.desktop/src/gb.desktop/.info'
dh_installinfo: cp gb.xml/src/rpc/gb.xml.rpc/.info comp/src/gb.mysql/.info comp/src/gb.settings/.info comp/src/gb.form/.info comp/src/gb.web/.info comp/src/gb.eval.highlight/.info comp/src/gb.db.form/.info comp/src/gb.report/.info comp/src/gb.form.mdi/.info comp/src/gb.form.dialog/.info comp/src/gb.chart/.info gb.gtk/src/gb.gtk/.info gb.qt4/src/gb.qt4/.info gb.desktop/src/gb.desktop/.info debian/gambas3/usr/share/info returned exit code 1
make: *** [binary] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -D -us -uc failed 
```

---

### Post by r-senior on 2012-05-04
I thought you had it working? Why are you uploading it again?

This error is saying you already uploaded 3.1.1-1 but now you are trying to upload it again with different content. You can't change the content of a previously uploaded version, you have to increase the version number, e.g. 3.3.1-2.

```
File gambas3_3.1.1-1.debian.tar.gz already exists in Gambas-3, but uploaded version has different contents. See more information about this error in https://help.launchpad.net/Packaging/UploadErrors.
```

---

### Post by etdsbastar on 2012-05-04
Hey senior,

I just frustrated using launchpad and compilations from the past 2 days. Sitting almost 12 hours a day...

Will you please help me in one thing.

Please create a PPA for GAMBAS 3.1.1 for MAVERICK 10.10 release of Ubuntu and tell me the PPA name.

Because, I am in need to install Gambas in 4 of my systems and each time I have to compile for every machine. Better to use a PPA in each machine.

Thanks.

---

### Post by r-senior on 2012-05-05
> **etdsbastar said:**
> Please create a PPA for GAMBAS 3.1.1 for MAVERICK 10.10 release of Ubuntu and tell me the PPA name.
You can't really expect me to create your PPA for you. If you can't use the gambas2 from the repositories and need to package gambas3, you need to figure it out.

Sorry.

---

### Post by etdsbastar on 2012-05-05
Its ok r-senior,

And thanks for your reply. I had upgraded to Precise Pangolin and Gambas 3.3.1 PPA from Kendek is working fine.

Thanks a lot for your help.

---

