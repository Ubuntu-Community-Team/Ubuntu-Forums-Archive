---
title: "How to make launchpad builder to use g++-4.9 in trusty"
date: 2016-02-12
forum: Packaging and Compiling Programs
---

### Post by Jahidul_Hamid on 2016-02-12
I am building a package in trusty. In local machine I have added the toolchain-r repository and installed g++-4.9. But how do I tell the launchpad builder to do the same.

I have added the following without any sccess:
```
Build-Depends: debhelper (>= 8.0.0), g++ (>=4.9.2), gcc (>=4.9.2), autotools-dev
Depends: libstdc++6 (>=4.9.2)
```

[This is the build log.]("https://launchpadlibrarian.net/238295587/buildlog_ubuntu-trusty-amd64.rnm_3.3.2-2_BUILDING.txt.gz")

---

