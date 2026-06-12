---
title: "Unity 4.0.1"
date: 2011-06-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Starks on 2011-06-22
[https://launchpad.net/ubuntu/+source/unity/4.0.1-0ubuntu1](https://launchpad.net/ubuntu/+source/unity/4.0.1-0ubuntu1)

> unity (4.0.1-0ubuntu1) oneiric; urgency=low

  * New upstream release.
    - Launcher - move Launcher icon count indicator so that it appears on the
      right side of the Launcher icons (LP: #767046)
  * Cherry pick some patches to not build on GTest, soname fixes as well as
    invalid value for automaximize
  * Some lintian cleanage:
    debian/control:
    - bump Standards-Version
    - don't build-dep on quilt
    debian/rules, debian/patches:
    - dont use --with-quilt
  * debian/control:
    - add build-dep on libgtk-3-dev, libcairo2-dev, libindicator3-dev,
      libsigc++-2.0-dev
    - bump deps on libunity-misc-dev, libnux-1.0-dev, libbamf3-dev
    - remove vala
  * debian/unity-common.install, debian/control:
    - now ship the ccsm unityshell image, gconf schemas, all images and
      apport hook
  * debian/unity-services.install, debian/control
    - new unity-services package containing current and futur unity services,
      moving files to it from unity
  * debian/libunity-core-4.0-1.install, debian/libunity-core-4.0-dev.install,
    debian/control:
    - new libunity-core packages for shared library between unity and unity-2d
  * debian/rules:
    - remove unitydialog and networkarearegion from ccsm to avoid enabling them,
      they are making compiz hanging and segfault on switch
    - generate some shlibs for libunity-core-4.0-1 taking into accout ABI
      unstability
 -- Didier Roche <didrocks@ubuntu.com>   Wed, 22 Jun 2011 18:01:16 +0200

---

