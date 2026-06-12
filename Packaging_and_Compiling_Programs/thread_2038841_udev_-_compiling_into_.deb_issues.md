---
title: "udev - compiling into .deb issues"
date: 2012-08-07
forum: Packaging and Compiling Programs
---

### Post by Doug S on 2012-08-07
I am trying to make the udev .deb from a local bzr branch.
As a starting point, I have not made any changes, but rather am just trying to get it to build.
The reference I am using is: [http://developer.ubuntu.com/packaging/html/](http://developer.ubuntu.com/packaging/html/)
and it took awhile but I finally figured out that```
bzr branch ubuntu:p/udev precise
```doesn't work and it needs to be```
bzr branch ubuntu:precise/udev precise
```When I get to the build step```
bzr builddeb -- -S -us -uc
```It does stuff for a short time and then gives up, after some lintian warnings```
...
dpkg-source: info: building udev in udev_175-0ubuntu9.dsc
 dpkg-genchanges -S >../udev_175-0ubuntu9_source.changes
dpkg-genchanges: not including original source code in upload
 dpkg-source --after-build udev-175
dpkg-source: info: using options from udev-175/debian/source/options: --tar-ignore=.bzr --tar-ignore=.git --tar-ignore=test --diff-ignore=(^|/)(.bzr|.gitignore|test)($$|/)|docs/.*\.types
dpkg-buildpackage: binary and diff upload (original source NOT included)
Now running lintian...
W: udev source: debian-rules-missing-recommended-target build-arch
W: udev source: debian-rules-missing-recommended-target build-indep
W: udev source: out-of-date-standards-version 3.9.2 (current is 3.9.3)
Finished running lintian.
Cleaning build dir: /home/doug/udev-bzr-pp-2/build-area/udev-175
(precise_i386)doug@s15:~/udev-bzr-pp-2/bug-986654$

```I have been unable to get any further.
 
Other notes:
I am working on [bug 986654]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/986654")
Compiling on a different computer, with a chroot environment, because the destination computer (the one that demonstrates the issue) is very pathetic.
while the udev 175-0ubuntu9.1 update was released a day or two ago, the bzr branch doesn't seem to include it yet. It doesn't matter because the problem remains and I will want to go backwards from 175-0ubuntu9 anyhow.
I have tried to increase verbose information in debian/rules with "export DH_VERBOSE=1".
 
Any help or suggestions would be greatly appreciated.

---

### Post by SevenMachines on 2012-08-07
This isnt giving up, it looks fine (apart from inevitable warnings) and I imagine its built the source package ok. if you look in directory above do you not find tarball and .dsc files?
-S will build a source package, have you tried building the binaries with -b? Maybe thats the .deb files you were expecting

---

### Post by Doug S on 2012-08-07
Thanks for the reply.
Yes the tarball and .dsc files were there. And yes, using the -b option makes the .deb files I was expecting.

---

