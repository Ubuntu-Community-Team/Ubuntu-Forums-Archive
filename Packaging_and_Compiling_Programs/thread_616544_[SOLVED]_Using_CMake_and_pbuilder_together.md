---
title: "[SOLVED] Using CMake and pbuilder together"
date: 2007-11-18
forum: Packaging and Compiling Programs
---

### Post by SeanHodges on 2007-11-18
I'm having a problem packaging my program using the guide at:

[https://help.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html](https://help.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html)

I think my problem stems from the fact I'm using CMake instead of autotools, but I might just be doing something wrong. I'm completely new to packaging, so I'll step through what I've done, followed by the error I'm getting:

1. Perform an in-source configure using CMake (otherwise the packaging tools do not get their top-level Makefile)

```
cd ~/medes-1.0.0
ccmake .
```

(Within ccmake, I alter the CMAKE_INSTALL_PREFIX to be "/usr")

2. Build the debian package template and orig tarball

```
dh_make -e seanhodges@bluebottle.com --createorig
```

3. Edit debian/control to include the required dependancies (including cmake and pkg-config):

```
Source: medes
Section: web
Priority: extra
Maintainer: Sean Hodges <seanhodges@bluebottle.com>
Build-Depends: debhelper (>= 5), cmake (>= 2), pkg-config (>= 0.22), firefox-dev (>= 2)), libgtk2.0-dev (>= 2), libxml2-dev (>= 2)
Standards-Version: 3.7.2

Package: medes
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}, firefox (>= 2), libxml2 (>= 2)
Description: This is a test
 This is a test
```

4. For now, I'm ignoring GPG signing (it refuses to find my key atm) so I call dpkg-buildpackage as follows:

```
dpkg-buildpackage -us -uc -S -rfakeroot
```

5. No errors so far. Finally, I attempt to run pbuilder against the package contents:

```
sudo pbuilder build ../*.dsc
```

And I get a big stdout dump (I can attach it if wanted) followed by:

```
# Add here commands to configure the package.
touch configure-stamp
dh_testdir
# Add here commands to compile the package.
/usr/bin/make
make[1]: Entering directory `/tmp/buildd/medes-1.0.0'
CMake Error: The source directory "/home/sean/medes-1.0.0" does not exist.
Specify --help for usage, or press the help button on the CMake GUI.
make[1]: *** [cmake_check_build_system] Error 254
make[1]: Leaving directory `/tmp/buildd/medes-1.0.0'
make: *** [build-stamp] Error 2
pbuilder: Failed autobuilding of package
 -> Aborting with an error
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/pbuilder/build//2689 and its subdirectories
```

I can see that cmake is trying to build against my home dir inside the pbuilder environment, which obviously won't work. Does anyone have an idea where I'm going wrong?

---

### Post by dholbach on 2007-11-20
Try without running the 'ccmake' command locally. If necessary run it in debian/rules, maybe in the configure target.

---

### Post by SeanHodges on 2007-11-21
> **dholbach said:**
> Try without running the 'ccmake' command locally. If necessary run it in debian/rules, maybe in the configure target.

Hey, thanks for your reply.

Adding the non-interactive "cmake" command to the debian/rules, and not calling it locally, worked perfectly.

Thanks for pointing me in the right direction!

---

