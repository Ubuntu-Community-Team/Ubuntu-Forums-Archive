---
title: "Build-depends on old version of package in ppa opposed to ubuntu repository"
date: 2012-09-18
forum: Packaging and Compiling Programs
---

### Post by krosswindz on 2012-09-18
I am trying to build XBMC v11.0 with libnfs support. Unfortunately for XBMC v11.0 to work with libnfs it requires a very specific version of libnfs which is outdated. I am trying to setup a ppa for myself in which I have the correct version of libnfs built. The question now is how do I setup the dependencies correctly for XBMC such that it picks up libnfs-dev from my ppa as opposed to what is in Ubuntu's repositories. I tried setting the build depends with libnfs(= 1.0.0~git20110902.0804e67) but then it fails with the following error
```

After installing, the following source dependencies are still unsatisfied:
libnfs-dev(inst 1.2.0-3 ! = wanted 1.0.0~git20110902.0804e67)
```

Any help on how to resolve this issue would be greatly appreciated.

---

