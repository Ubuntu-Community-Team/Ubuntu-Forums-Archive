---
title: "Package software"
date: 2018-02-04
forum: Packaging and Compiling Programs
---

### Post by jtodd.fr on 2018-02-04
I want to package this software volnoti ([https://github.com/davidbrazdil/volnoti](https://github.com/davidbrazdil/volnoti)). By following post at stackoverflow ([https://unix.stackexchange.com/questions/175292/convert-pacman-package-to-deb-or-rpm](https://unix.stackexchange.com/questions/175292/convert-pacman-package-to-deb-or-rpm)) executing command `debuild -us -uc[COLOR=#242729][FONT=Arial] [/FONT][/COLOR]` throws 

```

 dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: source package volnoti
dpkg-buildpackage: source version 0.2-1
dpkg-buildpackage: source distribution unstable
dpkg-buildpackage: source changed by user <user@unknown>
 dpkg-source --before-build volnoti
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
dh clean  --with autotools_dev
   dh_testdir
   dh_auto_clean
   dh_autotools-dev_restoreconfig
   dh_clean
 dpkg-source -b volnoti
dpkg-source: info: using source format '3.0 (quilt)'
dpkg-source: info: building volnoti using existing ./volnoti_0.2.orig.tar.gz
dpkg-source: error: cannot represent change to README:
dpkg-source: error:   new version is symlink to README.md
dpkg-source: error:   old version is plain file
dpkg-source: warning: executable mode 0775 of 'package.sh' will not be represented in diff
dpkg-source: error: cannot represent change to pkg/arch/volnoti-0.1-3.src.tar.gz: binary file contents changed
dpkg-source: error: add pkg/arch/volnoti-0.1-3.src.tar.gz in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: warning: executable mode 0775 of 'prepare.sh' will not be represented in diff
dpkg-source: error: cannot represent change to res/progressbar_empty.xcf: binary file contents changed
dpkg-source: error: add res/progressbar_empty.xcf in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to res/progressbar_full.xcf: binary file contents changed
dpkg-source: error: add res/progressbar_full.xcf in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to res/volume_high.png: binary file contents changed
dpkg-source: error: add res/volume_high.png in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to res/volume_low.png: binary file contents changed
dpkg-source: error: add res/volume_low.png in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to res/volume_medium.png: binary file contents changed
dpkg-source: error: add res/volume_medium.png in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to res/volume_muted.png: binary file contents changed
dpkg-source: error: add res/volume_muted.png in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to res/volume_off.png: binary file contents changed
dpkg-source: error: add res/volume_off.png in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to volnoti-0.2.tar.gz: binary file contents changed
dpkg-source: error: add volnoti-0.2.tar.gz in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: unrepresentable changes to source
dpkg-buildpackage: error: dpkg-source -b volnoti gave error exit status 2
debuild: fatal error at line 1376:
dpkg-buildpackage -rfakeroot -D -us -uc failed

```

My control file looks like 
```

Source: volnoti
Section: x11
Priority: optional
Maintainer: user <user@unknown>
Build-Depends: debhelper (>=9),autotools-dev, libdbus-1-dev (>=1.10.6), libdbus-glib-1-dev (>=0.106-1), libgtk2.0-dev (>=2.24.30)
Standards-Version: 3.9.6
Homepage: 
Vcs-Git: https://github.com/davidbrazdil/volnoti.git
Vcs-Browser: https://github.com/davidbrazdil/volnoti


Package: volnoti
Architecture: all
Depends: ${misc:Depends}  
Description: Lightweight volume notification for Linux
  Volnoti is a lightweight volume notification daemon for GNU/Linux and other POSIX operating systems. It is based on GTK+ and D-Bus and should work with any sensible window manager. The original aim was to create a volume notification daemon for lightweight window managers like LXDE or XMonad. It is known to work with a wide range of WMs, including GNOME, KDE, Xfce, LXDE, XMonad, i3 and many others. The source code is heavily based on the GNOME notification-daemon.

```

At first git clone the source to dir volnoti. After successfully building dist tar file by `make && make dist`, then create related Debian pkg files by `[COLOR=#242729][FONT=Consolas]dh_make -f volnoti-0.2.tar.gz[/FONT][/COLOR]` under cloned dir volnoti. 

How can I successfully build deb package file?

Thanks

---

### Post by wildmanne39 on 2018-02-04
*Thread moved to **Packaging and Compiling Programs, a more appropriate forum**.*

---

