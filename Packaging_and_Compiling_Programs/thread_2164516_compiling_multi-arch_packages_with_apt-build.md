---
title: "compiling multi-arch packages with apt-build"
date: 2013-07-31
forum: Packaging and Compiling Programs
---

### Post by mendieta on 2013-07-31
Hi

I've been toying with apt-build, not in small part because I got a Haswell processor, and some of the software can run much faster if compiled with the right flags
[http://www.phoronix.com/scan.php?page=article&item=intel_core_avx2&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_core_avx2&num=1)

Anyways, I am stumped because I have packages like this:

```
ii  libgstreamer0.10-0:amd64               0.10.36-1ubuntu2                                                       amd64        Core GStreamer libraries and elements
ii  libgstreamer0.10-0:i386                0.10.36-1ubuntu2                                                       i386         Core GStreamer libraries and elements
```

How do I get to produce those multi-arch packages? Any ideas? My build only produces amd64 packages, so I can't really upgrade to the packages I build (and there is always the odd piece of software relying on the 386 packages)

Many thanks for any pointers! I googled, I man'ed, and no charm

Cheers!

---

