---
title: "apache2 2.2.19 build problems with lucid ppa"
date: 2011-08-30
forum: Packaging and Compiling Programs
---

### Post by ptn107 on 2011-08-30
So I backported apache 2.2.19 for lucid, maverick, and natty.  After uploading the source files to launchpad I see that maverick and natty built fine but lucid did not because of a dependency problem.  Apache2 requires libssl-dev (>= 0.9.8m) which is not in lucid.  I did a local test build on my lucid x64 machine earlier which worked because I snatched the libssl-dev 1.0.0d-2ubuntu2 from oneiric.

My question is can I fake the launchpad build machine into using libssl-dev (>= 0.9.8m) for building or maybe modify the dependencies in the control file to bypass this problem on lucid?

---

### Post by ptn107 on 2011-08-30
This problem was *temporarily* circumvented by changing the control file to exclude a specific version number for libssl-dev on lucid.  I would still like for someone to explain how to build with a newer dependency on an older version of Ubuntu.

---

