---
title: "Found a bug in mozilla-dev"
date: 2006-09-23
forum: Programming Talk
---

### Post by almahtar on 2006-09-23
Hey.  I'm working on a project that embeds Gecko, and in the process came accross a bug in the mozilla-dev package:  the file /usr/include/mozilla/nscore.h includes "prtypes.h" and should include "nspr/prtypes.h".

I've fixed it for my machine and I'm happily developing, but I'd like to know the process by which I should report this fix.  Should it be the package maintainer?  The Mozilla devs?  I've never actually submitted a fix before, so I'm in the dark.  If I wasn't up to my neck in programming homework I'd find out for myself, but I figured maybe one of you more experienced devs might be able to point me in the right direction.

---

