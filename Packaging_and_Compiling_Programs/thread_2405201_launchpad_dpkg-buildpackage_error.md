---
title: "launchpad: dpkg-buildpackage: error"
date: 2018-11-02
forum: Packaging and Compiling Programs
---

### Post by cyring on 2018-11-02
Hello,

I'm creating an Ubuntu package for my project [CoreFreq]("https://github.com/cyring/CoreFreq") which makes two binaries and one kernel module

The main sequence is running fine locally:
```

debuild -us -uc -S
debsign
dput

```

The package is accepted by the Launchpad PPA but it fails to build on server with the following log:
```

dpkg-buildpackage
-----------------

dpkg-buildpackage: info: source package corefreq
dpkg-buildpackage: info: source version 1.37.0.4-0ubuntu1
dpkg-buildpackage: info: source distribution bionic
 dpkg-source --before-build corefreq-1.37.0.4
dpkg-buildpackage: info: host architecture amd64
 fakeroot debian/rules clean
dh clean
   dh_auto_clean
    make -j4 -O clean
make -j1 -C /lib/modules/4.4.0-138-generic/build M=/<<PKGBUILDDIR>> clean
make[2]: Entering directory '/<<PKGBUILDDIR>>'
make[2]: warning: -jN forced in submake: disabling jobserver mode.
make[2]: *** /lib/modules/4.4.0-138-generic/build: No such file or directory.  Stop.
make[2]: Leaving directory '/<<PKGBUILDDIR>>'
Makefile:74: recipe for target 'clean' failed
make[1]: *** [clean] Error 2
dh_auto_clean: make -j4 -O clean returned exit code 2
debian/rules:5: recipe for target 'clean' failed
make: *** [clean] Error 25
dpkg-buildpackage: error: fakeroot debian/rules clean subprocess returned exit status 2
--------------------------------------------------------------------------------

```


The build package files are the following:

**debian/rules**
```
#!/usr/bin/make -f
export DH_VERBOSE = 1


%:
    dh $@



```

**debian/changelog**
```
corefreq (1.37.0.4-0ubuntu1) bionic; urgency=medium


  * Initial release


 -- CyrIng <etc@etc.etc>  Thu, 02 Nov 2018 20:05:00 +0100



```

**debian/control**
```
Source: corefreq
Section: utils
Priority: optional
Maintainer: CyrIng <etc@etc.etc>
Build-Depends: debhelper (>= 10)
Standards-Version: 4.1.2
Homepage: https://github.com/cyring/CoreFreq
#Vcs-Git: https://anonscm.debian.org/git/collab-maint/corefreq.git
#Vcs-Browser: https://anonscm.debian.org/cgit/collab-maint/corefreq.git


Package: corefreq
Architecture: amd64
Depends: ${shlibs:Depends}, ${misc:Depends}
Description: CPU monitoring
 CoreFreq is a CPU monitoring software designed for the 64-bits Processors,
 including architectures Intel Atom, Core2, Xeon, Phi, Nehalem, Westmere,
 SandyBridge, IvyBridge, Haswell, Broadwell, Skylake, Kaby Lake, Coffee Lake,
 AMD K8, Zen



```

**debian/copyright**
```
Format: https://www.debian.org/doc/packaging-manuals/copyright-format/1.0/
Upstream-Name: corefreq
Source: <https://github.com/cyring/CoreFreq>


Files: *
Copyright: 2015-2018 CYRIL INGENIERIE <etc@etc.etc>
License: GPL-2+


Files: debian/*
Copyright: 2018 CYRIL INGENIERIE <etc@etc.etc>
License: GPL-2+
 This package is free software;
 etc ...



```

**debian/compat**
```
10



```

**debian/files**
```
corefreq_1.37.0.4-0ubuntu1_source.buildinfo utils optional



```

[Makefile]("https://github.com/cyring/CoreFreq/blob/master/Makefile")

Thanks for any help ):P

---

### Post by cyring on 2018-11-03
No kernel headers can be installed on the build server.
The dkms way might be the only solution.

---

