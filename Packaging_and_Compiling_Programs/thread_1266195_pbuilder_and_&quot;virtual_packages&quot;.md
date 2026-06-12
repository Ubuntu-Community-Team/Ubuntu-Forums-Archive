---
title: "pbuilder and &quot;virtual packages&quot;"
date: 2009-09-14
forum: Packaging and Compiling Programs
---

### Post by Bachstelze on 2009-09-14
```
  pbuilder-satisfydepends-dummy: Depends: libdirac-dev which is a virtual package.
                                 Depends: libfaad-dev which is a virtual package. or
                                          libfaad2-dev which is a virtual package.
                                 Depends: libopenjpeg-dev which is a virtual package.
                                 Depends: yasm which is a virtual package.

```

So for some reason, pbuilder thinks those packages are virtual packages, which they are definitely not. The pbuilder tarball is freshly created. Any ideas about what may be causing this? This is on a Jaunty system, by the way.

---

### Post by Bachstelze on 2009-09-14
Problem solved, my tarball was missing universe/multiverse.

[https://wiki.ubuntu.com/PbuilderHowto#Universe%20support](https://wiki.ubuntu.com/PbuilderHowto#Universe%20support)

---

