---
title: "Build package with my own library as dependency"
date: 2011-03-30
forum: Packaging and Compiling Programs
---

### Post by msdark on 2011-03-30
Hi (sorry for my english)..
I'm trying to build a package of an app that depends on Qt4 and OpenCV , but the version of OpenCV i use is a patched version not the version of the oficial repositories (i compiled this manually) ...

But when i try to create the package with pbuilder i need to put the OpenCV packages like dependencies in the debian/control file, but i need to create with my libs.. how can i do that????

Any idea??

Thanks in advance.

---

### Post by Ibidem on 2011-03-30
1. Package the patched OpenCV, make sure it builds using dpkg-buildpackage.
2. Modify the version of the patched OpenCV (eg, use dch to set version to <baseversion>-msdark1) 
If your version breaks stuff built against the stock version, modify the package name (libcv2.1p) so it won't be installed instead of a regular version. You may want to change libcv-dev to (for example) libcvp-dev, since it sounds like building against your own version is not the same as building with stock libcv-dev
3. Upload it to a repository that pbuilder will use (eg, use your own ppa)

4. Set the other package to build-depend on ```
libcvp-dev (>= <baseversion>-msdark1)
```
(assuming you changed package name and version), and update the package information.
5. Build the other version with pbuilder (a ppa does this automatically)

---

