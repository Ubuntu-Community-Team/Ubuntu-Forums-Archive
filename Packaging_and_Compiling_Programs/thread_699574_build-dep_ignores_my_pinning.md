---
title: "build-dep ignores my pinning"
date: 2008-02-17
forum: Packaging and Compiling Programs
---

### Post by tekknokrat on 2008-02-17
I have hardy repos in my sources list because i upgraded to its kernel.
I am on gutsy amd64.

> deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy main universe multiverse restricted


After upgrading kernel, I pinned all other hardy packages in preferences:

> Package: *
Pin: release a=etch-backports
Pin-Priority: -1

Package: *
Pin: release a=hardy
Pin-Priority: -1


> apt-cache policy:
...
 500 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/restricted Translation-de
  -1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/restricted Packages
     release v=8.04,o=Ubuntu,a=hardy,l=Ubuntu,c=restricted
     origin de.archive.ubuntu.com
 500 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/multiverse Translation-de
  -1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/multiverse Packages
     release v=8.04,o=Ubuntu,a=hardy,l=Ubuntu,c=multiverse
     origin de.archive.ubuntu.com
 500 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/universe Translation-de
  -1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/universe Packages
     release v=8.04,o=Ubuntu,a=hardy,l=Ubuntu,c=universe
     origin de.archive.ubuntu.com
 500 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Translation-de
  -1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Packages
     release v=8.04,o=Ubuntu,a=hardy,l=Ubuntu,c=main
     origin de.archive.ubuntu.com
...


When I try an upgrade everything is ok:
>  LC_ALL=C sudo apt-get upgrade -s
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


but when I try to get the build-deps for bacula it ignores the pinning completely:
> 
LC_ALL=C sudo apt-get build-dep bacula -s | grep hardy
Inst libsm-dev (2:1.0.3-1 Ubuntu:7.10/gutsy, Ubuntu:8.04/hardy)
Inst libxau-dev (1:1.0.3-2 Ubuntu:7.10/gutsy, Ubuntu:8.04/hardy)
Inst libxdmcp-dev (1:1.0.2-2 Ubuntu:7.10/gutsy, Ubuntu:8.04/hardy)
Inst x11proto-input-dev (1.4.2-1 Ubuntu:7.10/gutsy, Ubuntu:8.04/hardy)
Inst x11proto-kb-dev (1.0.3-2ubuntu1 Ubuntu:7.10/gutsy, Ubuntu:8.04/hardy)
Inst x11proto-xext-dev (7.0.2-5ubuntu1 Ubuntu:7.10/gutsy, Ubuntu:8.04/hardy)
Inst x11proto-fixes-dev (1:4.0-2ubuntu1 Ubuntu:7.10/gutsy, Ubuntu:8.04/hardy)
Inst libxfixes-dev (1:4.0.3-2 Ubuntu:7.10/gutsy, Ubuntu:8.04/hardy)
Inst libxdamage1 (1:1.1.1-3 Ubuntu:7.10/gutsy, Ubuntu:8.04/hardy)
Inst x11proto-damage-dev (1:1.1.0-2build1 Ubuntu:7.10/gutsy, Ubuntu:8.04/hardy)
Inst libxdamage-dev (1:1.1.1-3 Ubuntu:7.10/gutsy, Ubuntu:8.04/hardy)
Inst libxext-dev (2:1.0.3-2build1 Ubuntu:7.10/gutsy, Ubuntu:8.04/hardy)
Inst libfreetype6-dev (2.3.5-1ubuntu4 Ubuntu:7.10/gutsy, Ubuntu:8.04/hardy)


I know an easy workaround would be to remove the entry from sources.list but thats not a solution i like.
Some suggestions?

---

