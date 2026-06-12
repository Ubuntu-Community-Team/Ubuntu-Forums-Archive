---
title: "rstudio can't find libuuid.so.1"
date: 2015-10-29
forum: Programming Talk
---

### Post by mark allyn on 2015-10-29
Hello everyone,

I managed to ruin an installation of rstudio by installing rdevel (which was built from source, not from ubuntu rbase-dev).  At this point I have re-installed rstudio and r-base.  However, when I issue rstudio from the command line my 14.04 shell comes back with this:
```

rstudio: error while loading shared libraries: libuuid.so.1: cannot open shared object file: No such file or directory

```

As a matter of fact, libuuid.so.1 is instaled at /lib/x86_64-linux-gnu.  Can someone explain what is happening.  It's clear that rstudio is not finding the path, but I don't know how to fix the problem.  

Thank you,
Mark Allyn

---

